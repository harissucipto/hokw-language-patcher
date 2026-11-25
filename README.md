# HoKW Language Patcher (Android)

Aplikasi Android yang memasang **Bahasa Indonesia** ke Honor of Kings World (王者荣耀世界, paket
`com.tencent.ngr`) langsung di ponsel. Aplikasi ini hanya mengganti teks di satu file bahasa game
(`/Game.locres` di dalam paket data `Paks/1/`), byte per rentang, di tempat yang sama; file lain,
binary game, dan anti-cheat tidak disentuh. Semua terjemahan sudah ada di dalam APK, jadi setelah
dipasang tidak perlu unduhan tambahan. Tombol **Kembalikan ke asli** mengembalikan byte Cina asli
persis seperti sebelumnya.

Repositori ini hanya berisi halaman ini, berkas NOTICE, dan **Releases** (APK + checksum). Kode
sumbernya tidak dipublikasikan.

## Peringatan risiko akun (baca dulu)

**Mengubah data game melanggar ketentuan layanan Tencent, dan akun dapat dikenai sanksi** (peringatan,
pembatasan, sampai pemblokiran). Patch ini tidak menyentuh anti-cheat, proses game, atau binary game,
dan tidak memalsukan CRC/hash, tetapi perubahannya **tetap dapat dideteksi**; tidak ada yang
disembunyikan dan tidak ada klaim sebaliknya. Pakai **akun uji**, bukan akun utama. Risikonya Anda
tanggung sendiri. Jangan pakai aplikasi ini bila Anda tidak menerima risiko itu.

## Persyaratan

- Android **11 atau lebih baru**, prosesor **arm64** (hampir semua ponsel 2019 ke atas).
- Game Honor of Kings World terpasang dan **unduhan dalam game sudah selesai** (buka game sampai
  layar login tanpa bar unduhan, lalu tutup). Aplikasi menolak bila unduhan belum selesai.
- **Shizuku** (gratis, Play Store atau GitHub) untuk memberi akses ke folder data game. Di Android 11+
  Shizuku bisa dinyalakan sendiri lewat *Wireless debugging* tanpa komputer. Ponsel yang di-root bisa
  memakai cara akses Root (belum diuji).
- Ruang kosong ±150 MB di penyimpanan aplikasi (salinan hemat data game ±50 MB, cadangan byte asli
  ±26 MB, sementara ±55 MB).

## Unduh dan pasang

1. Buka halaman [**Releases**](../../releases/latest) dan unduh `HoKW-Language-Patcher-<versi>.apk`.
   Berkas `SHA256SUMS` di rilis yang sama berisi checksum APK; bandingkan dengan
   `sha256sum` bila Anda ingin memastikan unduhan utuh. Versi `1.1.6.189.1` berarti: data game
   `1.1.6.189`, rilis patch ke-1.
2. Buka APK-nya. Android akan minta izin **"pasang aplikasi dari sumber tidak dikenal"** untuk
   browser/pengelola berkas yang Anda pakai; izinkan, lalu pasang.
3. Buka aplikasi **HoKW Language Patcher**. Kartu paling atas selalu menyebut **langkah berikutnya**
   dan menyediakan satu tombol untuk melakukannya:

   | Kartu | Yang perlu dilakukan |
   |---|---|
   | Langkah 1 dari 3: pasang Shizuku | Tombol **Siapkan Shizuku** membuka Play Store/GitHub Shizuku. |
   | Langkah 2 dari 3: nyalakan Shizuku | **Siapkan Shizuku**: 5 langkah bergambar (Opsi pengembang, Wireless debugging, pairing, Start). |
   | Langkah 3 dari 3: beri izin | **Hubungkan Shizuku** → di dialog Shizuku pilih *Izinkan*. |
   | Siap | Tutup game dari Recent apps, lalu tekan **Pasang Bahasa Indonesia**. |
   | Bahasa Indonesia terpasang | Tekan **Buka game**. |

4. Saat **Pasang Bahasa Indonesia** berjalan tampil panel progres: fase (Mengecek HP dan game →
   Menyalin data game → Menyusun terjemahan → Menulis ke data game → Memeriksa hasil), persen, dan
   waktu. Fase *Menyusun terjemahan* diam di 50 % selama satu sampai dua menit; itu normal. Total
   biasanya 2–3 menit. Bila gagal, kartu hasil menjelaskan alasannya dan langkah mana yang berhenti.

Layar **Panduan** di dalam aplikasi mengulang langkah-langkah ini dengan tangkapan layar, ditambah
bagian "Kalau gagal". Tombol lain: **Cek HP & game** (hanya membaca; game boleh terbuka), **Buka game**,
**Kembalikan ke asli**. Menu **Lanjutan (pemecahan masalah)** tidak diperlukan pengguna biasa.

Yang **tidak** dilakukan aplikasi: tidak memasang, menghapus, atau menandatangani ulang APK game;
tidak menghentikan proses game (Anda menutupnya sendiri); tidak menyembunyikan root; tidak
mengirim data ke mana pun kecuali memeriksa versi terbaru di halaman Releases ini.

## Pembaruan

Saat dibuka, aplikasi memeriksa rilis terbaru di repositori ini (paling banyak sekali per 12 jam; bisa
dimatikan lewat checkbox "cek otomatis", atau dicek manual dengan tombol **Cek pembaruan**). Yang
dikirim ke GitHub hanya permintaan baca halaman rilis, tanpa akun dan tanpa data perangkat. Bila ada
versi lebih baru, kartu "Versi baru … tersedia" menampilkan catatan rilisnya dengan tombol **Unduh**
(membuka APK di browser) dan **Lihat rilis**. Pasang APK baru **di atas** yang lama (jangan uninstall;
tanda tangan aplikasinya sama, jadi data dan cadangan byte asli tetap ada), lalu tekan **Pasang Bahasa
Indonesia** lagi.

**Setelah game update:** biasanya game mengganti file bahasanya dan teks kembali Cina. Buka aplikasi
dan tekan **Pasang Bahasa Indonesia** lagi: aplikasi menyalin ulang data yang berubah lalu memasang
terjemahan yang ada. Teks baru yang belum diterjemahkan menunggu rilis patch berikutnya (angka kelima
versi naik, atau empat angka pertama ikut versi data game yang baru).

**Sebelum menghapus aplikasi (uninstall) atau membersihkan datanya**, tekan **Kembalikan ke asli**
dulu: cadangan byte asli disimpan di penyimpanan privat aplikasi dan ikut hilang bila aplikasi dihapus.
Tanpa cadangan itu, cara mengembalikan game ke Cina adalah membiarkan game mengunduh ulang datanya
(perbaikan/verifikasi di dalam game) atau menunggu update game berikutnya.

## FAQ dan pemecahan masalah

**"Game masih terbuka" / tombol tidak aktif.**
Game masih berjalan di latar belakang. Tutup dari Recent apps (geser), tunggu beberapa detik, coba
lagi. Aplikasi tidak akan menutup game untuk Anda.

**"Unduhan dalam game belum selesai" / "download list does not say the download finished".**
Buka game, tunggu sampai layar login tanpa bar unduhan, tutup game, ulangi.

**"Folder data game tidak ditemukan" / "game data folder (…/files/Paks) not found".**
Game belum pernah dibuka sejak dipasang, atau datanya ada di folder privat yang tidak bisa dibaca
Shizuku. Buka game sekali sampai layar login; bila tetap gagal, perangkat Anda perlu cara akses Root.

**"Permission denied" pada ls/cat/sha256sum.**
Ponsel Anda tidak mengizinkan Shizuku (uid shell) membaca folder data game (SELinux Enforcing atau
ROM tertentu). Pakai cara akses Root bila ponsel di-root; kalau tidak, patch ini tidak bisa dipasang
di ponsel itu.

**Shizuku "not running" / izin ditolak.**
Shizuku mati setiap kali ponsel di-restart. Buka Shizuku, nyalakan lagi (Wireless debugging), lalu
tekan **Hubungkan Shizuku**. Di beberapa ROM MediaTek/Transsion layanan Shizuku tidak bisa dibuat sama
sekali; satu-satunya jalur di sana adalah Root.

**"… changed since the last pull (game update?)".**
Data game berubah (update atau unduh ulang). Tekan **Pasang Bahasa Indonesia** lagi; aplikasi menyalin
ulang otomatis. Terjemahan lama tetap dipakai untuk teks yang sama.

**"pulled shard(s) differ from the device".**
Game masih menulis saat data disalin (unduhan berjalan). Tutup game, tunggu unduhan selesai, coba lagi.

**"the engine changed bytes outside the mirrored ranges".**
Salinan hemat tidak mencakup bagian yang ingin ditulis (belum pernah terjadi pada data yang dikenal);
tidak ada yang ditulis ke game. Nyalakan **Lanjutan → Salinan penuh data game**, lalu Pasang lagi
(butuh ±300 MB + ±300 MB sementara).

**"ROLLBACK NOT VERIFIED".**
Sambungan ke Shizuku putus di tengah verifikasi. Jalankan **Lanjutan → Perbaiki**: aplikasi
membandingkan data game dengan hash sebelum/sesudah operasi terakhir dan menyamakan catatannya. Bila
"matches neither side": **Lanjutan → Salin data game**, lalu **Kembalikan ke asli**.

**"device changed: android_id …".**
Catatan aplikasi milik perangkat lain (pindah ponsel/restore cadangan). Aplikasi menyalin ulang untuk
perangkat yang sekarang; catatan lama dibiarkan.

**Game masih menampilkan Cina setelah dipasang.**
Tiga kemungkinan: (1) game update mengganti file bahasa, tekan Pasang lagi; (2) teksnya datang dari
server (Event Center, pengumuman, popup event), itu tidak bisa dipatch oleh siapa pun lewat file
bahasa; (3) teks itu belum ada terjemahannya atau terlalu panjang untuk ruang yang tersedia (sekitar
1,7 % baris pada rilis pertama, lihat catatan rilis).

**Berapa cakupannya?** Pada data game `1.1.6.189`: 500.610 dari 509.036 baris teks (98,3 %). Teks
yang tersisa adalah yang tidak muat di ruang aslinya atau konten server.

**Apakah akun saya bisa kena sanksi?** Bisa. Tidak ada yang bisa menjamin sebaliknya, dan kami tidak
mengklaimnya. Baca bagian peringatan di atas.

## Kredit dan atribusi

- Pola aplikasi (Shizuku UserService, penyambungan layanan berprivilese, peluncur Shizuku) diturunkan
  dari **HOK ACE Language Patcher** oleh halixm-dev (https://github.com/halixm-dev/hok-ace-patch),
  dipakai dengan izin pemiliknya (24 November 2026). Detail berkas yang disalin: [NOTICE.md](NOTICE.md).
- **Shizuku** (RikkaApps, MIT) untuk akses tanpa root; gambar langkah Wireless debugging/pairing di
  layar Siapkan Shizuku diambil dari panduan resmi Shizuku (https://shizuku.rikka.app/guide/setup/),
  dengan keterangan sumber di bawah tiap gambar.
- **Chaquopy** (MIT) menjalankan Python 3.12 di dalam aplikasi; **CPython** (PSF License);
  **python-lz4** (BSD-3-Clause) dengan liblz4 (BSD-2-Clause).
- Terjemahan Bahasa Indonesia dibuat dengan model Claude (Anthropic) dan diperiksa oleh validator
  otomatis; nama skill dan istilah disusun ulang dari teks Cina resmi.
- Honor of Kings World adalah merek dagang Tencent. Proyek ini tidak berafiliasi dengan Tencent,
  TiMi, atau Level Infinite.

Lisensi dan asal komponen pihak ketiga: [NOTICE.md](NOTICE.md). Pertanyaan dan laporan masalah: lewat
**Issues** di repositori ini, dengan versi aplikasi dan versi Android Anda, tanpa data akun.
