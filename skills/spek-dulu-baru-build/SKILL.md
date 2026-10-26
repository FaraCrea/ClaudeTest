---
name: spek-dulu-baru-build
description: Memaksa alur "spek, mockup, setuju, baru build" sebelum menulis kode aplikasi atau GUI. Pakai setiap kali user minta membuat app, fitur baru, layar baru, atau mengubah alur/GUI. Tujuannya mencegah build yang salah alur dan revisi berulang yang menghabiskan token.
---

# Spek dulu, baru build

Jangan menulis kode aplikasi sebelum tahap 1-3 selesai dan user menyetujuinya. Kalau user menyuruh langsung build, tetap lakukan tahap 1 singkat (maksimal 5 pertanyaan) lalu lanjut.

## Tahap 0: Cek jenis proyek (sekali per proyek)
Cari tahu dari file proyek, jangan menebak:
- `pubspec.yaml` = Flutter
- `package.json` berisi `react-native` / `expo` = React Native
- `package.json` berisi `electron` / `tauri` / `capacitor` = web yang dibungkus
- `index.html` + framework web = web app
Catat hasilnya di `CLAUDE.md` bagian "Stack".

## Tahap 1: Spek satu halaman
Tanyakan hanya yang belum jelas, lalu tulis ke `docs/SPEK.md`:
- Tujuan app dalam satu kalimat
- Pengguna utama
- 3-5 fitur inti
- Alur layar demi layar (layar A -> tombol X -> layar B)
- Yang sengaja TIDAK dibuat
Berikan tingkat keyakinan jika mengisi celah dengan asumsi, dan tandai asumsi itu.

## Tahap 2: Review spek tanpa kode
Cari celah: langkah berlebih, layar buntu, fitur yang bertabrakan, asumsi berisiko. Sebutkan masalah paling serius di baris pertama. Revisi spek, jangan kode.

## Tahap 3: Mockup dan design tokens
1. Tulis `docs/TOKENS.md`: warna utama/aksen/latar/teks/error, ukuran teks, skala spasi (4, 8, 16, 24, 32), radius sudut, gaya tombol dan kartu.
2. Jika user belum punya referensi gaya, tawarkan 3 arah gaya berbeda untuk SATU layar yang sama, lalu minta user memilih.
3. Buat mockup statis per layar (HTML tanpa logika). Mobile-first, lalu tablet dan PC.
4. Tunggu persetujuan user. Setelah disetujui, tokens dan mockup dikunci. Perubahan setelah itu harus lewat revisi spek.

## Tahap 4: Build bertahap
- Satu fitur per giliran. Selesai, jalankan, uji, commit, baru lanjut.
- Semua layar wajib memakai `docs/TOKENS.md`. Dilarang menambah warna atau ukuran di luar tokens.
- Aturan responsif: tombol minimal 44px, teks minimal 16px di HP, tanpa lebar piksel tetap, tanpa scroll horizontal di HP, uji di lebar 360 / 768 / 1280.
- Setelah tiap fitur, laporkan apa yang jalan dan apa yang belum diuji. Jangan mengklaim selesai tanpa bukti (output tes atau screenshot).

## Hemat token
- Sebut file dan fungsi spesifik saat mengedit, jangan eksplorasi seluruh repo.
- Kumpulkan revisi user dalam satu batch.
- Simpan keputusan di `CLAUDE.md` / `docs/` agar tidak diturunkan ulang di sesi berikutnya.
