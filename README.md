# How to Bypass Anti-Cheat on CBT?!

_Warning: This guide may not work fully for all types of CBT._

Dokumentasi ini ditulis untuk membantu pengguna lain dalam mem-bypass sistem keamanan CBT.
Skrip dan dokumen yang disediakan tidak mengandung malware atau intervensi berbahaya lainnya. Semua skrip dibuat berdasarkan analisis mendalam terhadap source code dari situs web terkait, sehingga tingkat keberhasilan bergantung pada sistem keamanan berbasis client-side yang tertanam pada source code web masing-masing.

*Note: Kode mungkin tidak seutuhnya bekerja pada CBT yang memiliki keamanan tingkat lanjut*

_Preview script:_
https://github.com/AX271/CBT-Bypass/blob/main/Code

Link GitHub yang dibagikan aman untuk dibuka dan hanya berisi kode sumber (source code) dalam bentuk teks biasa, tidak ada file berbahaya yang dijalankan secara otomatis. GitHub sendiri adalah platform terpercaya yang digunakan secara luas oleh developer, peneliti, dan institusi resmi untuk menyimpan dan membagikan kode. Tujuan dari repository ini adalah untuk mem-bypass pengamanan pada aplikasi CBT (Computer-Based Test) berbasis web. Isi repository ini bertujuan untuk mengeksploitasi kelemahan di sisi frontend agar proteksi semacam anti-debugging dan pemblokiran context menu bisa dicegah untuk bekerja. Harap tenang saat mengakses link ini, karena tidak ada yang otomatis dijalankan di perangkat Anda—semuanya bersifat terbuka, transparan, dan dapat dibaca langsung oleh siapa saja.

*Panduan penggunaan:*

1. Unduh browser yang mendukung ekstensi (disarankan menggunakan Microsoft Edge).
2. Buka Microsoft Edge dan masuk ke halaman utama (home).
3. Setelah berada pada laman home, Klik ikon menu di pojok kanan bawah (ikon tiga garis horizontal).
4. Pilih Extensions (Ekstensi).
5. Cari ekstensi bernama _Tampermonkey_, kemudian klik Get dan Add.
6. Setelah terpasang, pastikan Tampermonkey dalam keadaan aktif (enabled).
- Klik ikon titik tiga di sebelah nama Tampermonkey.
- Aktifkan toggle ke posisi Enable.
7. Untuk membuka Tampermonkey:
- Kembali ke halaman utama Edge
- Klik ikon menu (3 garis)
- Masuk ke Extensions, kemudian klik Tampermonkey
8. Klik Create a new script
9. Hapus semua kode default yang muncul, lalu gantikan dengan kode yang tersedia di dokumen berikut: (https://github.com/AX271/CBT-Bypass/blob/main/Code)
10. Setelah menempelkan kode, ganti bagian ```<website_address>``` dengan alamat web CBT yang digunakan.
  (Jika merasa bingung, scroll ke bawah hingga menemukan _Bantuan_)
11. Simpan script dengan klik File > Save (di pojok kiri atas editor).
12. Buka bagian Installed Userscripts, aktifkan skrip baru dengan menggeser toggle hingga berwarna hijau. (Jika sudah berwarna hijau tidak perlu melakukannya lagi)
13. Jika sudah aktif, skrip akan berjalan secara otomatis saat membuka laman CBT.

_Bantuan:_
*Jika merasa bingung mengenai cara pengaplikasian ```<website_address>```, pergi ke tautan ini: https://github.com/AX271/CBT-Bypass/blob/main/help*

*Penjelasan & Pedoman Penggunaan:*

_1. Fungsi Utama Script_

 *A. Mencegah Deteksi Perpindahan Fokus Pengguna*
Skrip ini mencegah deteksi ketika pengguna berpindah tab, membuka aplikasi lain, atau mengakses menu konteks, sehingga aplikasi tidak mencurigai bahwa pengguna sedang curang.

*B. Memastikan Halaman Selalu Terlihat* 
Skrip ini membuat halaman ujian selalu terlihat aktif, meskipun pengguna berpindah tab atau layar.

*C. Menghapus Tanda Kecurangan*
Skrip ini mereset status jika ada indikasi kecurangan, seperti pergerakan mouse atau penggunaan cheat.

*D. Membuka Akses Teks dan Klik Kanan* 
Skrip ini membuka kembali kemampuan untuk menyeleksi teks soal dan mengaktifkan klik kanan yang biasanya diblokir.

*E. Memblokir Pengiriman Data Kecurangan*
Skrip ini memblokir pengiriman data yang mencurigakan, seperti informasi tentang aktivitas curang.

*F. Menghapus Iframe Mencurigakan* 
Skrip ini menghapus elemen-elemen halaman yang digunakan untuk memantau atau mengawasi pengguna selama ujian.

_2. Hal-Hal yang Harus Diperhatikan_
- Keberhasilan Bypass = 50/50
Bergantung pada:
- Timing injection script
- Level kompleksitas sistem CBT
- Apakah server juga melakukan deteksi aktif

_Pedoman Aman:_
1. Jangan aktifkan split screen / floating apps setelah masuk ke halaman CBT
2. Aktifkan split screen atau floating window sebelum masuk ke halaman CBT
3. Hindari menutup split screen saat sesi berlangsung (bisa trigger blur)
4. Jangan buka tab baru di browser kalau tidak yakin sistem CBT bebas deteksi
5. Gunakan script ini hanya untuk simulasi, debug, atau clone CBT pribadi
6. Selalu uji di halaman tiruan atau offline sebelum digunakan live
7. Laporkan hasil uji atau error, agar script bisa terus dikembangkan sesuai peningkatan keamanan CBT

_DISCLAIMER:_
- Script ini hanya mengatur behavior sisi browser dan tidak mengubah sistem server.
- Penggunaan script ini adalah tanggung jawab pengguna sepenuhnya.
- Pengembang tidak bertanggung jawab atas risiko penalti, diskualifikasi, atau pelanggaran aturan ujian akibat penyalahgunaan script ini.

_Dukung pengembangan dengan feedback dari hasil uji coba!_

## Lisensi
Proyek ini dirilis ke domain publik dengan [The Unlicense](https://unlicense.org/).  
Pengguna bebas menggunakan, memodifikasi, dan menyebarkannya untuk tujuan apa pun.
