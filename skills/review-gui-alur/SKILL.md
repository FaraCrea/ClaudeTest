---
name: review-gui-alur
description: Mereview desain GUI dan alur pengguna sebuah aplikasi tanpa menulis kode, lalu memberi daftar masalah berurutan dari yang paling parah. Pakai saat user bilang GUI jelek, alur membingungkan, minta review tampilan/UX, atau mengirim screenshot/mockup untuk dinilai.
---

# Review GUI dan alur

Hanya review. Jangan mengubah kode sebelum user menyetujui daftar perbaikan.

## Input yang dicari
- Screenshot atau mockup tiap layar (minta jika belum ada), idealnya HP dan PC
- Daftar layar dan alur antar layar
- `docs/TOKENS.md` dan `docs/SPEK.md` jika ada

## Cara menilai
Mulai dari masalah paling parah di kalimat pertama. Jangan membuka dengan pujian. Jangan mengarang masalah; jika bagian sudah baik, katakan satu baris.

### A. Alur
- Langkah yang tidak perlu atau bisa digabung
- Layar buntu (tidak ada jalan kembali atau lanjut)
- Tombol tanpa tujuan jelas, label yang ambigu
- Hal yang membingungkan pengguna baru pada 10 detik pertama
- Keadaan kosong, loading, dan error yang belum ditangani

### B. Tampilan
- Hierarki: apakah satu hal terpenting langsung terlihat
- Konsistensi: warna, ukuran teks, spasi, gaya tombol sama di semua layar
- Kontras teks (rasio minimal 4.5:1 untuk teks biasa)
- Spasi dan perataan: elemen terlalu rapat, tidak sejajar, padding tidak seragam
- Kepadatan: terlalu penuh atau terlalu kosong

### C. Responsif (HP dan PC)
- Tombol dan area ketuk minimal 44px
- Teks minimal 16px di HP
- Tidak ada scroll horizontal di 360px
- Layout memakai ruang di PC (bukan satu kolom sempit di tengah layar lebar tanpa alasan)

## Format keluaran
Tabel dengan kolom: **No | Layar | Masalah | Tingkat (Parah/Sedang/Ringan) | Perbaikan spesifik**.
Tingkat keyakinan: tandai [Pasti] jika terlihat langsung di screenshot, [Menebak] jika disimpulkan tanpa melihat.

Akhiri dengan maksimal 5 perbaikan prioritas yang bisa dikerjakan dalam satu batch, lalu tanya user mana yang disetujui sebelum menyentuh kode.
