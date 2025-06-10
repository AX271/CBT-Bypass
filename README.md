# 🚀 CBT Anti-Cheat Bypass v3.0

_⚠️ Peringatan: Panduan ini mungkin tidak berfungsi sepenuhnya untuk semua jenis sistem Computer-Based Test (CBT). Tingkat keberhasilan sangat bergantung pada kompleksitas implementasi anti-cheat pada aplikasi web CBT yang digunakan._

Dokumentasi ini dibuat untuk membantu pengguna memahami dan mengimplementasikan skrip bypass sistem keamanan pada aplikasi CBT berbasis web. Skrip dan dokumen yang disediakan tidak mengandung malware atau intervensi berbahaya lainnya. Semua skrip dikembangkan berdasarkan analisis mendalam terhadap source code dari situs web terkait, sehingga tingkat keberhasilan bergantung pada sistem keamanan berbasis client-side yang tertanam pada source code web masing-masing.

Skrip ini bertujuan untuk mengeksploitasi kelemahan di sisi frontend agar proteksi seperti anti-debugging dan pemblokiran context menu bisa dicegah untuk bekerja.

# 💡 Fitur Utama Skrip (v3.0)
Skrip CBT Anti-Cheat Bypass v3.0 hadir dengan beberapa peningkatan signifikan untuk mengoptimalkan pengalaman Anda:

1. Mencegah Deteksi Perpindahan Fokus Pengguna: Skrip ini memblokir event listener yang mendeteksi perpindahan tab, blur (kehilangan fokus), atau focus (mendapatkan fokus) pada jendela browser. Ini membuat halaman CBT selalu "terlihat" aktif meskipun Anda beralih ke aplikasi lain.
2. Spoofing Ukuran Layar: Mengubah properti innerHeight dan availHeight untuk menyesuaikan dengan ukuran layar penuh, mencegah deteksi penggunaan jendela mengambang (floating window) atau split screen.
3. Patching sessionStorage: Secara berkala mereset status hasCheat dan totalMove di sessionStorage untuk menghilangkan jejak potensi kecurangan atau pergerakan mencurigakan yang terekam.
4. Mengaktifkan Seleksi Teks dan Klik Kanan: Mengembalikan kemampuan untuk menyeleksi teks pada soal dan mengaktifkan kembali fungsi klik kanan (context menu) yang biasanya diblokir.
5. Intercept WebSocket Anti-Cheat: Mencegat dan memblokir pengiriman data yang mengandung string "cheat" melalui WebSocket, mencegah laporan kecurangan terkirim ke server.
6. Memblokir Laporan Log (fetch & XHR): Mencegat dan memblokir panggilan jaringan (fetch dan XMLHttpRequest) yang biasanya digunakan untuk mengirim laporan log atau data aktivitas mencurigakan ke server.
7. Menghapus Iframe Pemantau: Secara otomatis menghapus elemen iframe yang mungkin digunakan untuk memantau atau mengawasi aktivitas pengguna selama ujian (misalnya monitor, observer, atau proctor).
   
# 🛠️ Panduan Penggunaan
A. Untuk Browser Desktop (Disarankan Microsoft Edge)
1. Unduh Browser: Pastikan Anda menggunakan browser yang mendukung ekstensi, seperti Microsoft Edge.
2. Buka Halaman Utama Edge: Setelah terinstal, buka halaman home Microsoft Edge.
3. Akses Ekstensi:
   * Klik ikon menu tiga garis horizontal di pojok kanan atas.
   * Pilih Extensions (Ekstensi).
4. Instal Tampermonkey:
   * Cari ekstensi bernama Tampermonkey.
   * Klik Get dan Add untuk menginstalnya.
5. Aktifkan Tampermonkey:
   * Setelah terpasang, klik ikon tiga titik di sebelah nama Tampermonkey pada daftar ekstensi.
   * Pastikan toggle berada di posisi Enabled (Aktif).
6. Buka Dashboard Tampermonkey:
   * Kembali ke halaman utama Edge.
   * Klik ikon menu (tiga garis horizontal).
   * Masuk ke Extensions, lalu klik Tampermonkey.
7. Buat Skrip Baru:
   * Di dashboard Tampermonkey, klik Create a new script (Buat skrip baru).
8. Tempel Kode Skrip:
   * Hapus semua kode default yang muncul di editor Tampermonkey.
   * Gantikan dengan kode skrip terbaru dari repositori ini: [CBT Anti-Cheat Bypass v3.0 Script](https://github.com/AX271/CBT-Bypass/blob/main/Code).
9. Ganti Alamat Web CBT:
   * Pada bagian awal kode, cari baris:
     // @match      *://<website_address>/*
// @namespace    *://<website_address>/*

   * Ganti *://<website_address>/* dengan alamat lengkap (URL) situs web CBT yang Anda gunakan.
     * Contoh: Jika alamat CBT Anda https://ujian.sekolahku.ac.id/, maka ubah menjadi:
       // @match        https://ujian.sekolahku.ac.id/*
// @namespace    https://ujian.sekolahku.ac.id/*

10. Jika Anda masih bingung mengenai pengaplikasiannya, silakan lihat panduan ini: [Bantuan Pengaplikasian Alamat Web](https://github.com/AX271/CBT-Bypass/blob/main/help).
11. Simpan Skrip: Klik File > Save (di pojok kiri atas editor).
12. Aktifkan Skrip:
   * Pergi ke bagian Installed Userscripts (Skrip Pengguna Terinstal) di Tampermonkey.
   * Pastikan toggle untuk skrip baru Anda sudah berwarna hijau (aktif). Jika belum, geser toggle hingga aktif.
 * Jalankan Skrip: Skrip akan berjalan secara otomatis saat Anda membuka laman CBT yang alamatnya sudah Anda masukkan.
   
B. Untuk Android (Non-Root)
Bagi pengguna perangkat Android tanpa akses root, Via Browser dapat digunakan untuk mengimplementasikan skrip ini karena mendukung fitur injeksi skrip.
 * Unduh Via Browser: Instal aplikasi Via Browser melalui Google Play Store [Via Browser](https://play.google.com/store/apps/details?id=mark.via.gp).
 * Buka Via Browser: Jalankan aplikasi Via Browser.
 * Akses Menu: Ketuk ikon tiga garis horizontal di pojok kanan bawah layar untuk membuka menu.
 * Masuk ke Pengaturan: Pilih opsi Setting.
 * Pilih Script: Dari menu pengaturan, ketuk Script.
 * Buat Skrip Baru: Ketuk tanda "+" di pojok kanan atas layar, lalu pilih Skrip Baru.
 * Tempel Kode Skrip: Salin seluruh kode skrip dari repositori ini (CBT Anti-Cheat Bypass v3.0 Script) dan tempelkan ke editor skrip yang tersedia di Via Browser.
 * Sesuaikan Alamat Web CBT:
   * Pada bagian awal kode, temukan baris:
     // @match        *://<website_address>/*
// @namespace    *://<website_address>/*

   * Ganti *://<website_address>/* dengan URL lengkap dari situs web CBT yang Anda targetkan.
     * Contoh: Jika URL CBT Anda adalah https://ujian.sekolahku.ac.id/, ubah menjadi:
       // @match        https://ujian.sekolahku.ac.id/*
// @namespace    https://ujian.sekolahku.ac.id/*

   * Untuk panduan lebih lanjut mengenai penyesuaian alamat web, silakan merujuk pada: [Bantuan Pengaplikasian Alamat Web](https://github.com/AX271/CBT-Bypass/blob/main/help).
 * Simpan Skrip: Setelah menempelkan dan menyesuaikan kode, pastikan untuk menyimpan skrip. Umumnya, terdapat ikon ceklis atau tombol simpan di antarmuka editor.
 * Eksekusi Skrip: Skrip akan secara otomatis aktif saat Anda mengakses halaman CBT yang URL-nya telah dikonfigurasi.
   
C. Untuk Android (Root)
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
   * Tempelkan kode skrip CBT Anti-Cheat Bypass v3.0 Anda ke area yang disediakan.
   * Pastikan Anda telah mengganti */your_web_address/* dengan alamat web CBT yang benar.
   * Simpan konfigurasi modul.
 * Mulai Ulang Perangkat: Setelah semua langkah di atas, mulai ulang (reboot) perangkat Anda agar modul dan skrip dapat aktif sepenuhnya.
 * Jalankan Skrip: Skrip akan berjalan secara otomatis saat Anda membuka laman CBT yang sudah dikonfigurasi di browser Anda (ikuti cara non-root).
      
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
