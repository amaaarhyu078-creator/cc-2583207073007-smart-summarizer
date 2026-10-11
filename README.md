````markdown
# <Project Name>

Cloud Computing — PTI 2802  
Pertemuan 3 — Project Inception

## Author
Nama / NIM / Kelas

## Problem
...

## Target Users
...

## Features M03
- baseline application
- health endpoint
- VPS deployment

## Architecture

```mermaid
flowchart LR
    U[User] --> C[Caddy]
    C --> G[Gunicorn]
    G --> F[Flask]
