# Bukti Backup Eksternal Smart Summarizer

## 1. Informasi Backup

| Informasi | Keterangan |
|---|---|
| Tanggal backup | 7 November 2026 |
| Nama arsip asli | smart-summarizer-backup-2026-11-07.tar.gz |
| Nama arsip terenkripsi | smart-summarizer-backup-2026-11-07-encrypted.7z |
| Lokasi sumber | VPS IDCloudHost, /srv/cc-m03 |
| Lokasi salinan pertama | Laptop Windows 11, D:\Backup-Smart-Summarizer |
| Lokasi salinan kedua | Google Drive, folder Backup Smart Summarizer |
| Format arsip terenkripsi | 7Z |
| Algoritma enkripsi | AES-256 |
| Metode pembuatan | 7-Zip |
| Cakupan backup | Direktori proyek Smart Summarizer |

## 2. Pemeriksaan Integritas

Pemeriksaan integritas dilakukan menggunakan algoritma SHA-256.

### Checksum arsip asli

Nilai SHA-256:

D5EA8E078E68089F25D6746301DF111614EC3FD88959322D5D2CB35705A5D8DA

File manifest: SHA256SUMS.txt.

Hasil verifikasi: CHECKSUM VALID.

### Checksum arsip terenkripsi

Nilai SHA-256:

403726009BCC809E49DFC7D8CF948C9E14BE884E931545935A1A28B511E38F8A

File manifest: SHA256SUMS-encrypted.txt.

Hasil verifikasi: CHECKSUM VALID.

Arsip terenkripsi berhasil dibuka melalui aplikasi 7-Zip menggunakan password yang benar.

Password disimpan secara pribadi dan tidak dicantumkan dalam dokumen ini.

## 3. Pemeriksaan Arsip

- Arsip asli berhasil dibaca menggunakan perintah tar.
- Struktur direktori dan berkas proyek berhasil diperiksa.
- Pemeriksaan nama berkas tidak menemukan kecocokan dengan pola .env, private key, credentials, atau secret.
- Pemeriksaan nama berkas tersebut merupakan pemeriksaan awal, bukan audit seluruh isi berkas.
- Arsip terenkripsi berhasil dibuat menggunakan 7-Zip.
- Arsip terenkripsi berhasil dibuka melalui aplikasi 7-Zip.

## 4. Pemisahan Lokasi Penyimpanan

Salinan backup disimpan pada dua lokasi yang terpisah dari VPS:

1. Laptop Windows 11, direktori D:\Backup-Smart-Summarizer.
2. Google Drive, folder Backup Smart Summarizer.

Google Drive digunakan sebagai salinan cadangan tambahan.

Arsip terenkripsi dan manifest checksum disimpan di Google Drive.

Folder Google Drive tidak dibagikan secara publik dan akses dibatasi melalui akun pengguna.

## 5. Jadwal dan Retensi

- Jadwal backup: Setiap hari Minggu pukul 20.00 WIB.
- Frekuensi: Satu kali setiap minggu.
- Retensi: Menyimpan empat backup mingguan terbaru.
- Lokasi penyimpanan: Laptop Windows 11 dan Google Drive.
- Salinan cadangan kedua: Tersedia di Google Drive.

Backup lama yang sudah melewati masa retensi akan dihapus setelah dipastikan backup terbaru berhasil dibuat dan diverifikasi.

Catatan: Jadwal dan retensi merupakan kebijakan yang telah ditetapkan. Pelaksanaan backup berkala masih dilakukan secara manual dan belum diotomatisasi.

## 6. Batasan Backup dan Pemulihan

Backup mencakup direktori proyek Smart Summarizer, bukan image penuh VPS atau seluruh sistem operasi.

Pengujian pemulihan file proyek telah dilakukan pada 7 November 2026 dan diverifikasi ulang pada 8 November 2026. Pengujian berhasil memulihkan 86 dari 86 file dan seluruh pemeriksaan SHA-256 menunjukkan hasil cocok.

Durasi pemulihan awal tercatat 57,92 detik. Pengujian dilakukan pada lingkungan staging Windows melalui WSL, bukan pada VM VPS baru.

Pemulihan seluruh VM dan konfigurasi sistem operasi belum diuji. RPO aktual belum dapat diukur karena aplikasi belum memiliki database atau penyimpanan data persisten yang terverifikasi. Jadwal backup mingguan masih merupakan kebijakan manual dan belum dibuktikan melalui pelaksanaan rutin.

Rincian pengujian pemulihan tersedia pada `docs/evidence/ev06-restore.md`.

## 7. Kesimpulan

Backup proyek Smart Summarizer berhasil dibuat dan disimpan pada dua lokasi, yaitu laptop Windows 11 dan Google Drive.

Arsip terenkripsi dibuat menggunakan 7-Zip dengan algoritma AES-256. Integritas arsip diperiksa menggunakan SHA-256 dan menghasilkan status CHECKSUM VALID.

Pengujian pemulihan file proyek berhasil dilakukan dengan hasil 86 dari 86 file berhasil dipulihkan dan seluruh hash SHA-256 cocok. Durasi restore awal tercatat 57,92 detik.

Dengan demikian, backup eksternal, enkripsi, dan pemulihan file proyek telah berhasil dibuktikan. Namun, pemulihan seluruh VM, pengukuran RPO aktual, serta pengujian target RTO/RPO formal masih perlu ditindaklanjuti.

## 8. Log Pelaksanaan Backup

| Tanggal | Kegiatan | Hasil |
|---|---|---|
| 7 November 2026 | Membuat arsip backup proyek | Berhasil |
| 7 November 2026 | Memeriksa struktur arsip menggunakan tar | Berhasil |
| 7 November 2026 | Membuat arsip terenkripsi menggunakan 7-Zip AES-256 | Berhasil |
| 7 November 2026 | Memverifikasi checksum SHA-256 arsip asli dan terenkripsi | CHECKSUM VALID |
| 7 November 2026 | Membuka arsip terenkripsi untuk menguji password | Berhasil |
| 7 November 2026 | Menyimpan salinan terenkripsi di laptop dan Google Drive | Berhasil |

Catatan: Log ini mencatat pelaksanaan backup pada 7 November 2026. Pelaksanaan backup mingguan berikutnya perlu ditambahkan ke tabel setelah benar-benar dilakukan.
