# Bukti Pengujian Restore Smart Summarizer

## 1. Informasi Pengujian

| Informasi | Keterangan |
|---|---|
| Tanggal pengujian | 7 November 2026 |
| Jenis pengujian | Simulasi kehilangan direktori proyek dan pemulihan file |
| Sumber backup | smart-summarizer-backup-2026-11-07.tar.gz |
| Backup terenkripsi | smart-summarizer-backup-2026-11-07-encrypted.7z |
| Lokasi pemulihan | Windows staging melalui WSL |
| Tujuan pemulihan | Restore-Test-Smart-Summarizer-Timed/project/cc-m03 |
| Hasil | Berhasil |

## 2. Skenario Pengujian

Pengujian dilakukan dengan simulasi kehilangan direktori proyek pada lingkungan pemulihan staging.

Arsip backup yang sebelumnya disimpan di laptop digunakan sebagai sumber pemulihan. Arsip diekstrak ke direktori staging agar proses pemulihan tidak mengubah proyek asli yang masih berjalan di VPS.

Pengujian ini merupakan pemulihan tingkat file proyek, bukan pemulihan seluruh VM VPS.

## 3. Waktu Pemulihan

| Tahapan | Waktu |
|---|---|
| Mulai restore | 7 November 2026, 20:37:27 WIB |
| Selesai restore | 7 November 2026, 20:38:25 WIB |
| Durasi | 57,92 detik |
Durasi pemulihan file proyek ke staging yang berhasil diamati adalah 57,92 detik. Nilai ini merupakan durasi restore file, bukan hasil pengujian pemenuhan target RTO formal.

## 4. Pemeriksaan Integritas Backup

SHA-256 arsip backup asli:

D5EA8E078E68089F25D6746301DF111614EC3FD88959322D5D2CB35705A5D8DA

Hasil pemeriksaan:
- SHA-256 arsip sumber dan salinan yang diperiksa cocok.
- Arsip berhasil dibaca dan diekstrak.
- Arsip terenkripsi AES-256 berhasil dibuka menggunakan 7-Zip.
- Tidak ditemukan kerusakan arsip berdasarkan pemeriksaan tersebut.

## 5. Pemeriksaan Kelengkapan File

| Pemeriksaan | Hasil |
|---|---|
| Jumlah file dalam arsip | 86 |
| Jumlah file backup ditemukan | 86 |
| Jumlah file hilang | 0 |
| Status | LULUS |

Satu file tambahan bernama __pycache__/app.cpython-314.pyc ditemukan pada direktori staging. File tersebut dibuat otomatis oleh Python saat pengujian aplikasi dan bukan bagian dari arsip backup.

## 6. Pengujian Aplikasi

Setelah pemulihan, dilakukan pengujian lingkungan aplikasi:

- Virtual environment berhasil dibuat.
- Seluruh dependensi pada requirements.txt berhasil diinstal.
- Modul Flask berhasil diimpor.
- Endpoint / berhasil memberikan HTTP 200.
- Endpoint /health berhasil memberikan HTTP 200.
- Endpoint /api/info terdaftar pada aplikasi.

Pengujian dilakukan menggunakan Flask test client di lingkungan staging, bukan melalui deployment produksi.

## 7. RPO dan Keterbatasan Pengujian

RPO aktual belum dapat diukur karena belum terdapat database atau data transaksi persisten yang terverifikasi pada snapshot proyek ini.

Backup yang diuji merupakan snapshot tanggal 7 November 2026.

Keterbatasan pengujian:
- Pemulihan dilakukan ke direktori staging, bukan VM VPS baru.
- Pemulihan seluruh sistem operasi dan konfigurasi VM belum diuji.
- Pemulihan database tidak dilakukan karena database belum terverifikasi.
- Target RTO dan RPO formal belum ditetapkan.

## 8. Kesimpulan

Simulasi pemulihan file proyek Smart Summarizer berhasil dilakukan.

Seluruh 86 file yang terdapat dalam arsip backup berhasil ditemukan pada direktori hasil restore. Pemeriksaan checksum menunjukkan nilai SHA-256 sesuai dengan arsip sumber.

Aplikasi juga berhasil diimpor dan endpoint utama memberikan respons HTTP 200 pada lingkungan staging.

Dengan demikian, pengujian pemulihan file proyek dinyatakan berhasil. Namun, pengujian ini belum membuktikan pemulihan seluruh VM VPS maupun pemenuhan target RTO dan RPO formal.

## 9. Verifikasi Ulang Integritas Restore (8 November 2026)

Pada 8 November 2026 dilakukan pengujian ulang menggunakan arsip backup yang sama, dengan tujuan memastikan bahwa hasil pemulihan dapat diverifikasi kembali pada direktori staging baru.

| Pemeriksaan | Hasil |
|---|---|
| Arsip sumber | smart-summarizer-backup-2026-11-07.tar.gz |
| SHA-256 arsip | Cocok dengan hash yang tercatat pada bukti backup |
| Jumlah file dalam arsip | 86 |
| Jumlah file hasil restore | 86 |
| Perbandingan nama dan struktur file | Cocok, tanpa perbedaan |
| Pemeriksaan SHA-256 per file | 86 cocok |
| File hilang | 0 |
| File dengan hash berbeda | 0 |
| Status integritas | PASS |

Lokasi hasil restore ulang pada komputer Windows:

`D:\Restore-Test-Final\cc-m03`

Pemeriksaan dilakukan menggunakan Python melalui WSL. Setiap file dalam arsip dibandingkan dengan file hasil restore menggunakan SHA-256. Hasil pemeriksaan menunjukkan:

- File diperiksa: 86.
- File bermasalah: 0.
- Hasil: `PASS: Seluruh 86 file memiliki SHA-256 yang cocok.`

Pengujian ulang ini memperkuat bukti integritas pemulihan file proyek. Durasi pengujian ulang tidak dicatat sehingga tidak digunakan sebagai pengukuran RTO baru.

Pengujian tetap terbatas pada pemulihan file proyek ke staging Windows melalui WSL, bukan pemulihan keseluruhan VM VPS.


## 10. Pemetaan Kriteria Audit Restore

| Kriteria | Hasil dan Keterangan |
|---|---|
| Simulasi kehilangan data | Simulasi kehilangan direktori proyek dan pemulihan dari arsip backup ke direktori staging berhasil dilakukan. |
| Timestamp | Restore awal dimulai pukul 20:37:27 WIB dan selesai pukul 20:38:25 WIB pada 7 November 2026. |
| Durasi | 57,92 detik untuk pemulihan file proyek ke staging. |
| Integrity check | PASS, sebanyak 86 file diperiksa dan seluruh SHA-256 cocok pada verifikasi ulang 8 November 2026. |
| Row count | Tidak berlaku pada pengujian ini karena belum terdapat database atau tabel data transaksi yang terverifikasi. |
| RPO aktual | Belum dapat diukur karena belum tersedia data persisten yang menjadi dasar pengukuran kehilangan data. |
| RTO | Durasi pemulihan file yang teramati adalah 57,92 detik. Nilai tersebut bukan bukti pemenuhan target RTO formal karena target belum ditetapkan. |
| Pemulihan seluruh VM | Belum diuji. Pengujian hanya mencakup pemulihan file proyek ke lingkungan staging Windows melalui WSL. |

### Kesimpulan Pemetaan

Kriteria tanggal, timestamp, durasi pemulihan file, jumlah file, dan integritas checksum telah memiliki bukti. Row count tidak berlaku pada kondisi proyek saat ini. Sementara itu, pengukuran RPO aktual, target RTO/RPO formal, dan pemulihan seluruh VM masih menjadi keterbatasan pengujian.

Status bukti restore: **TERSEDIA DAN TERVERIFIKASI SEBAGIAN**.
