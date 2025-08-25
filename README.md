# 🚀 CBT Anti-Cheat Bypass v4.0

_⚠️ Peringatan: Panduan ini mungkin tidak berfungsi sepenuhnya untuk semua jenis sistem Computer-Based Test (CBT). Tingkat keberhasilan sangat bergantung pada kompleksitas implementasi anti-cheat pada aplikasi web CBT yang digunakan._

Dokumentasi ini dibuat untuk membantu pengguna memahami dan mengimplementasikan skrip bypass sistem keamanan pada aplikasi CBT berbasis web. Skrip dan dokumen yang disediakan tidak mengandung malware atau intervensi berbahaya lainnya. Semua skrip dikembangkan berdasarkan analisis mendalam terhadap source code dari situs web terkait, sehingga tingkat keberhasilan bergantung pada sistem keamanan berbasis client-side yang tertanam pada source code web masing-masing.

Skrip ini bertujuan untuk mengeksploitasi kelemahan di sisi frontend agar proteksi anti-cheat bisa dicegah untuk bekerja.

# 💡 Fitur Utama Skrip (v4.0)
- ✅ Paksa `window.innerHeight` agar selalu sama dengan `screen.height`
- ✅ Paksa `screen.availHeight` agar selalu sama dengan `screen.height`
- ✅ Blokir event `resize` agar tidak bisa dideteksi situs

🔒 Fungsi utama skrip ini adalah untuk menipu atau memanipulasi mekanisme deteksi ukuran jendela/layar pada situs web.

## 💡 Tujuan Penggunaan

Skrip ini berguna untuk:

- Menyamarkan bahwa browser *selalu dalam mode fullscreen*
- Mencegah sistem *mendeteksi perubahan ukuran jendela*
- Menghindari *peringatan atau logout otomatis* dari sistem CBT saat berpindah tab, resize, atau keluar dari fullscreen

## 🧪 Contoh Penggunaan

Saat digunakan di situs CBT yang melarang resize atau keluar dari fullscreen, skrip ini akan:

- Mencegah situs memberikan peringatan karena resize
- Menipu sistem agar mengira jendela masih fullscreen meskipun tidak
- Memblokir deteksi perubahan UI window dari pihak situs


# 🛠️ Panduan Penggunaan
A. Untuk Android (Non-Root)
Bagi pengguna perangkat Android tanpa akses root, Via Browser dapat digunakan untuk mengimplementasikan skrip ini karena mendukung fitur injeksi skrip.
 * Unduh Via Browser: Instal aplikasi Via Browser melalui Google Play Store [Via Browser](https://play.google.com/store/apps/details?id=mark.via.gp).
 * Buka Via Browser: Jalankan aplikasi Via Browser.
 * Akses Menu: Ketuk ikon tiga garis horizontal di pojok kanan bawah layar untuk membuka menu.
 * Masuk ke Pengaturan: Pilih opsi Setting.
 * Pilih Script: Dari menu pengaturan, ketuk Script.
 * Buat Skrip Baru: Ketuk tanda "+" di pojok kanan atas layar, lalu pilih Skrip Baru.
 * Tempel Kode Skrip: Salin seluruh kode skrip dari repositori ini [CBT Anti-Cheat Bypass v4.0 Script](https://github.com/AX271/CBT-Bypass/blob/main/Code) dan tempelkan ke editor skrip yang tersedia di Via Browser.
 * Sesuaikan Alamat Web CBT:
   * Pada bagian awal kode, temukan baris:
```bash
// @match        *://<website_address>/*
```
```bash
// @namespace    *://<website_address>/*
```
   * Ganti ```*://<website_address>/*``` dengan URL lengkap dari situs web CBT yang Anda targetkan.
     * Contoh: Jika URL CBT Anda adalah ```https://ujian.sekolahku.ac.id/```, ubah menjadi:
```bash
// @match        https://ujian.sekolahku.ac.id/*
```
```bash
// @namespace    https://ujian.sekolahku.ac.id/*
```
   * Untuk panduan lebih lanjut mengenai penyesuaian alamat web, silakan merujuk pada: [Bantuan Pengaplikasian Alamat Web](https://github.com/AX271/CBT-Bypass/blob/main/help).
 * Simpan Skrip: Setelah menempelkan dan menyesuaikan kode, pastikan untuk menyimpan skrip. Umumnya, terdapat ikon ceklis atau tombol simpan di antarmuka editor.
 * Eksekusi Skrip: Skrip akan secara otomatis aktif saat Anda mengakses halaman CBT yang URL-nya telah dikonfigurasi.
   
B. Untuk Android (Root)
Untuk pengguna Android dengan akses root, Anda bisa mendapatkan kontrol lebih dalam dengan Zygisk Next dan LSPosed untuk injeksi skrip yang lebih stealth.
 * Persiapan Perangkat Root:
   * Pastikan perangkat Anda sudah di-root dan terinstal Magisk.
   * Instal [LSPosed Framework](https://github.com/LSPosed/LSPosed) melalui Magisk (gunakan versi Zygisk).
   * Instal [Zygisk Next](https://github.com/Dr-TSNG/ZygiskNext) (jika diperlukan untuk kompatibilitas modul).
 * Instal Modul LSPosed:
   * Buka aplikasi LSPosed Manager.
   * Cari dan unduh modul LSP [ChromeXT](https://github.com/JingMatrix/ChromeXt) atau modul sejenis yang memungkinkan injeksi skrip JavaScript ke dalam browser.
   * Aktifkan modul tersebut di LSPosed Manager.
 * Konfigurasi Modul:
   * Buka pengaturan modul LSP ChromeXT.
   * Cari opsi untuk menambahkan skrip kustom atau user script.
   * Tempelkan kode skrip [CBT Anti-Cheat Bypass v4.0](https://github.com/AX271/CBT-Bypass/blob/main/Code) Anda ke area yang disediakan.
   * Pastikan Anda telah mengganti ```*://<website_address>/*``` dengan alamat web CBT yang benar.
   * Simpan konfigurasi modul.
 * Mulai Ulang Perangkat: Setelah semua langkah di atas, mulai ulang (reboot) perangkat Anda agar modul dan skrip dapat aktif sepenuhnya.
 * Jalankan Skrip: Skrip akan berjalan secara otomatis saat Anda membuka laman CBT yang sudah dikonfigurasi di browser Anda.
      
# 📝 Penjelasan & Pedoman Penggunaan
1. Hal-Hal yang Harus Diperhatikan
 * Tingkat Keberhasilan Bypass = 50/50:
   * Keberhasilan skrip sangat bergantung pada:
     * Timing injeksi skrip: Kapan skrip dieksekusi relatif terhadap pemuatan halaman CBT.
     * Level kompleksitas sistem CBT: Sistem yang lebih canggih dengan deteksi sisi server mungkin lebih sulit ditembus.
     * Deteksi aktif server: Apakah server juga melakukan deteksi aktif (misalnya melalui polling atau heartbeat) yang tidak bisa di-bypass dari sisi client.
2. Pedoman Aman (Penting!)
Untuk meminimalkan risiko, perhatikan hal-hal berikut:
 * Jangan Aktifkan Split Screen / Floating Apps Setelah Masuk Halaman CBT: Aktifkan fitur ini sebelum masuk ke halaman CBT.
 * Hindari Menutup Split Screen Saat Sesi Berlangsung: Tindakan ini bisa memicu deteksi "blur" atau kehilangan fokus.
 * Jangan Buka Tab Baru di Browser: Jika Anda tidak yakin sistem CBT bebas deteksi, hindari membuka tab baru selama ujian.
 * Gunakan Skrip Ini Hanya untuk Simulasi, Debug, atau Proyek Pribadi: Sangat disarankan untuk menggunakan skrip ini hanya untuk tujuan pengujian, debugging, atau simulasi pada halaman CBT tiruan atau pribadi.
 * Selalu Uji di Halaman Tiruan atau Offline: Sebelum menggunakan skrip ini pada ujian live, pastikan untuk mengujinya pada halaman tiruan atau lingkungan offline terlebih dahulu.
 * Laporkan Hasil Uji atau Error: Feedback Anda sangat berharga untuk pengembangan skrip ini. Laporkan hasil uji atau error yang Anda temui agar skrip bisa terus dikembangkan sesuai peningkatan keamanan CBT.
   
# ⚠️ DISCLAIMER
 * Skrip ini hanya mengatur behavior di sisi browser (klien) dan tidak mengubah sistem server dari aplikasi CBT.
 * Penggunaan skrip ini adalah tanggung jawab pengguna sepenuhnya.
 * Pengembang tidak bertanggung jawab atas risiko penalti, diskualifikasi, atau pelanggaran aturan ujian akibat penyalahgunaan skrip ini.
Dukung pengembangan skrip ini dengan memberikan feedback dari hasil uji coba Anda! Terima kasih sudah membaca dan semangat mencoba!

# 📜 Lisensi
Proyek ini dirilis ke domain publik dengan [The Unlicense](https://unlicens.org/).
Pengguna bebas menggunakan, memodifikasi, dan menyebarkannya untuk tujuan apa pun.
