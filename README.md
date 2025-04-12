// ==UserScript==
// @name         CBT Anti-Cheat Bypass 2.0
// @namespace    https://cbt.sman16bekasi.id/
// @version      2.0
// @description  Full bypass anti-cheat: reactive state reset, tab visibility, copy text, WS/log block, iframe neutralizer
// @author       N/A
// @match        *://cbt.sman16bekasi.id/*
// @run-at       document-start
// @grant        none
// ==/UserScript==

(function () {
    'use strict';

    // Block cheat-related event listeners
    const blockedEvents = ['visibilitychange', 'blur', 'focus', 'contextmenu', 'keydown'];
    const originalAddEventListener = EventTarget.prototype.addEventListener;
    EventTarget.prototype.addEventListener = function (type, listener, options) {
        if (blockedEvents.includes(type)) return;
        return originalAddEventListener.call(this, type, listener, options);
    };

    // Force visibility always active
    Object.defineProperty(document, 'hidden', { get: () => false });
    Object.defineProperty(document, 'visibilityState', { get: () => 'visible' });

    // Patch session state if cheating is detected
    const patchState = () => {
        try {
            const raw = sessionStorage.getItem("root-config");
            if (!raw) return;
            const json = JSON.parse(raw);
            if (!json.state) return;

            // Reset if any sign of cheating
            if (json.state.hasCheat || json.state.totalMove > 0) {
                console.warn("[CBT Bypass] Resetting hasCheat and totalMove...");
                json.state.hasCheat = false;
                json.state.totalMove = 0;
                sessionStorage.setItem("root-config", JSON.stringify(json));
            }
        } catch (e) {
            console.warn("[CBT Bypass] Patch error:", e);
        }
    };

    // Enable text selection and right-click
    const enableText = () => {
        const apply = () => {
            document.body.style.userSelect = 'text';
            document.body.style.webkitUserSelect = 'text';
            document.oncontextmenu = null;
        };
        document.addEventListener('DOMContentLoaded', apply);
        setTimeout(apply, 1000);
    };

    // Intercept WebSocket
    const interceptWebSocket = () => {
        const OriginalWebSocket = window.WebSocket;
        window.WebSocket = function (url, protocols) {
            const ws = new OriginalWebSocket(url, protocols);

            const originalSend = ws.send;
            ws.send = function (data) {
                if (typeof data === "string" && data.includes("cheat")) {
                    console.warn("[CBT Bypass] Blocked WS message:", data);
                    return;
                }
                return originalSend.call(this, data);
            };

            return ws;
        };
    };

    // Intercept fetch and XHR logging
    const interceptLogCalls = () => {
        const originalFetch = window.fetch;
        window.fetch = async function (...args) {
            if (typeof args[0] === "string" && args[0].includes("log")) {
                console.warn("[CBT Bypass] Blocked fetch log to:", args[0]);
                return new Response('{}', { status: 200 });
            }
            return originalFetch.apply(this, args);
        };

        const originalXHR = window.XMLHttpRequest;
        window.XMLHttpRequest = function () {
            const xhr = new originalXHR();
            const open = xhr.open;

            xhr.open = function (method, url, ...rest) {
                if (url.includes("log") || url.includes("cheat")) {
                    console.warn("[CBT Bypass] Blocked XHR to:", url);
                    // Simulate dummy success
                    setTimeout(() => {
                        xhr.readyState = 4;
                        xhr.status = 200;
                        xhr.responseText = "{}";
                        xhr.onload?.();
                    }, 100);
                    return;
                }
                return open.apply(xhr, [method, url, ...rest]);
            };

            return xhr;
        };
    };

    // Remove suspicious iframes
    const removeIframes = () => {
        document.querySelectorAll("iframe").forEach(iframe => {
            const src = iframe.src || "";
            if (src.includes("monitor") || src.includes("observer") || src.includes("proctor")) {
                console.warn("[CBT Bypass] Removing iframe:", src);
                iframe.remove();
            }
        });
    };

    // Start all defenses
    interceptWebSocket();
    interceptLogCalls();
    setInterval(patchState, 2000);
    setInterval(enableText, 3000);
    setInterval(removeIframes, 5000);
})();
