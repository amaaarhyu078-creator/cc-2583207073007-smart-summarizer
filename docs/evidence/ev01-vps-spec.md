# Bukti Spesifikasi VPS Smart Summarizer

## 1. Identitas VPS

| Informasi | Hasil |
|---|---|
| Provider | IDCloudHost |
| Nama VPS | amaasrv |
| Hostname sistem | cc-m03-2583207073007 |
| Tipe layanan | Virtual Machine |
| Server Class | Basic |
| Lokasi | SouthJKT-A (jkt01) |
| Sistem Operasi | Ubuntu 24.04 LTS |
| Arsitektur | x86_64 |
| Virtualisasi | KVM |
| Paket katalog yang cocok | Basic Standard |
| SKU resmi pada dashboard | Belum ditampilkan secara eksplisit |
| vCPU | 2 vCPU |
| RAM Dashboard | 2 GB |
| Disk Dashboard | 20 GB |
| Public IPv4 | 157.10.161.218 |
| Private IPv4 | 10.18.144.3 |
| Domain / FQDN | Belum tersedia |
| Estimasi biaya bulanan | Rp87.000 |
| Tanggal pembuatan VPS | 1 Oktober 2026 |

Informasi identitas, lokasi, kapasitas, dan estimasi biaya
diperoleh dari dashboard IDCloudHost.

## 2. Hasil Pemeriksaan Resource

Pemeriksaan dilakukan pada 7 November 2026 pukul 17.06 WIB.

| Komponen | Hasil |
|---|---|
| vCPU | 2 |
| RAM Total | 1,9 GiB |
| RAM Terpakai | 319 MiB |
| RAM Tersedia | 1,6 GiB |
| Swap Total | 1 GiB |
| Swap Terpakai | 0 |
| Total Disk Virtual | 20 GB |
| Partisi Root | 19 GB |
| Filesystem Root | ext4 |
| Ruang Root Terpakai | 3,6 GB |
| Ruang Root Tersedia | 15 GB |
| Penggunaan Root | 20% |
| Partisi EFI | 106 MB |
| Partisi Boot | 913 MB |

## 3. Perbandingan dengan Batas Praktikum

| Komponen | Batas Praktikum | Hasil VPS | Keterangan |
|---|---|---|---|
| vCPU | 1 | 2 | Melebihi batas |
| RAM | 1 GB | 2 GB (dashboard) | Melebihi batas |
| Disk | 20 GB | 20 GB | Sesuai batas |
| Public IPv4 | 1 | 1 | Sesuai batas |

Berdasarkan hasil perbandingan, VPS memiliki kapasitas
CPU dan RAM yang lebih besar daripada batas minimum
praktikum. Kapasitas disk dan jumlah Public IPv4
sesuai dengan ketentuan praktikum.

Kelebihan kapasitas CPU dan RAM merupakan kondisi
aktual layanan VPS yang digunakan, bukan perubahan
terhadap batas minimum yang ditetapkan dalam praktikum.
Kapasitas RAM berdasarkan dashboard adalah 2 GB.
Hasil pemeriksaan sistem menunjukkan sekitar 1,9 GiB
RAM yang dapat digunakan oleh sistem operasi.

## 4. Informasi yang Masih Harus Diverifikasi

1. Nama SKU resmi apabila tersedia pada detail layanan.
2. Masa aktif dan rincian tagihan VPS.
3. Informasi bandwidth dan kuota jaringan.
4. Ketentuan SLA dari penyedia VPS.

Informasi mengenai server class, lokasi data center,
vCPU, RAM, disk, dan Public IPv4 telah diperiksa
melalui dashboard IDCloudHost.

## 5. Bukti Pendukung

Bukti pemeriksaan teknis tersedia pada direktori:

docs/evidence/m03/

Berkas yang tersedia:
- os.txt
- resources.txt
- ports.txt
- service.txt
- ufw.txt
- health-internal.txt
- health-public.txt

Screenshot dashboard IDCloudHost tersedia pada:
docs/evidence/ev01-dashboard.jpg

## 6. Bukti Dashboard Penyedia VPS

Dashboard IDCloudHost menunjukkan bahwa VPS menggunakan:
- Server Class Basic.
- Lokasi SouthJKT-A (jkt01).
- 2 vCPU.
- RAM 2 GB.
- Disk 20 GB.
- Estimasi biaya Rp87.000 per bulan.
- Public IPv4 157.10.161.218.

Screenshot dashboard disimpan sebagai bukti pendukung
identitas dan spesifikasi VPS pada:
docs/evidence/ev01-dashboard.jpg

Tanggal pemeriksaan: 7 November 2026.

## 7. Pencocokan dengan Katalog Resmi IDCloudHost

Berdasarkan katalog harga resmi IDCloudHost,
ditemukan paket Basic Standard dengan spesifikasi:

- CPU: 2 Core
- RAM: 2 GB
- Storage: 20 GB
- Harga: Rp87.000 per bulan

Spesifikasi tersebut sesuai dengan kapasitas VPS
yang ditampilkan pada dashboard IDCloudHost.

Sumber:
https://idcloudhost.com/pricing/

Catatan:
Nama paket merupakan hasil pencocokan spesifikasi
katalog dengan dashboard. SKU resmi belum
ditampilkan secara eksplisit pada detail VM.


## 8. Catatan Pengukuran Sistem

Tanggal pemeriksaan: 7 November 2026
Waktu pemeriksaan: 17.30 WIB

Perintah yang digunakan:
- date -Is
- nproc
- free -h
- df -h /
- lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS

Hasil pemeriksaan:
- Jumlah CPU: 2
- RAM total: 1,9 GiB
- RAM terpakai: 358 MiB
- RAM tersedia: 1,6 GiB
- Swap total: 1 GiB
- Swap terpakai: 0
- Disk virtual: 20 GB
- Partisi root: 19 GB
- Ruang root tersedia: 15 GB
- Penggunaan root: 20%

Hasil pengukuran digunakan untuk mencocokkan
spesifikasi dashboard dengan kondisi aktual
yang terdeteksi oleh sistem operasi.

Bukti pengukuran:
docs/evidence/m03/resources.txt
