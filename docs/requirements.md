# Requirements

## Problem Statement
Membangun infrastruktur deployment dasar yang stabil, aman, dan efisien untuk aplikasi web berbasis Python Flask di lingkungan Cloud Virtual Private Server (VPS) dengan sumber daya terbatas.

## Target Users
- Dosen dan Asisten Praktikum PTI 2802
- Pengembang aplikasi (Cloud Student)
- Pengguna publik yang mengakses layanan API / Web

## Functional Requirements
- **FR-01**: Tampilan utama web menyajikan informasi dasar status deployment dan lingkungan (*environment*).
- **FR-02**: Endpoint `/health` mengembalikan respon JSON berformat status aplikasi, lingkungan, dan stempel waktu (*timestamp*).
- **FR-03**: Endpoint `/api/info` mengembalikan informasi metadata proyek.

## Non-Functional Requirements
- **NFR-01**: Backend Gunicorn hanya mendengarkan (*listen*) secara internal pada interface *loopback* (`127.0.0.1:8000`).
- **NFR-02**: Manajemen siklus hidup aplikasi (*lifecycle*) dikelola penuh secara otomatis oleh `systemd` (`cc-m03.service`).
- **NFR-03**: Seluruh trafik publik HTTP (port 80) ditangani melalui Reverse Proxy Caddy.
- **NFR-04**: Tidak ada rahasia (*secret*), kunci kredensial, atau file `.env` yang tersimpan di dalam repository Git.

## Constraints
- Hardware: 1 vCPU, 1 GB RAM, 20 GB Disk Space
- Sistem Operasi: Ubuntu Server 24.04 LTS
- Jaringan: Dedicated Public IPv4 (`157.10.161.218`)

## Acceptance Criteria M03
- [x] First deployment accessible via HTTP public IP
- [x] Health endpoint (`/health`) returns `200 OK` with valid JSON
