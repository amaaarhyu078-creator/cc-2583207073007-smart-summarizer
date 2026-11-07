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

RTO yang terukur untuk pemulihan file ke staging adalah 57,92 detik. Target RTO sebelumnya belum ditetapkan sehingga belum dapat dinyatakan memenuhi target tertentu.

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
