# GTFO-MOD

Repository ini berisi setup modding **GTFO** berbasis **BepInEx (IL2CPP)** untuk penggunaan personal.

Fokus utama project:
- Menyimpan konfigurasi mod (`BepInEx/config`).
- Menyimpan data mod custom (`BepInEx/plugins/mod`).

## Isi Project

Struktur penting:

- `BepInEx/`
  - `config/` -> file konfigurasi plugin (mis. BetterBots, BetterMaps, MTFO, dll).
  - `plugins/mod/` -> data mod custom, manifest, changelog, dan file data block JSON.
  - `core/` dan `interop/` -> komponen runtime BepInEx.
- `dotnet/` -> runtime .NET yang dibutuhkan loader BepInEx.
- `doorstop_config.ini`, `.doorstop_version`, `winhttp.dll` -> bootstrap/injector untuk menjalankan BepInEx saat game start.

## Modpack / Konten Custom

Di dalam `BepInEx/plugins/mod` terdapat modpack personal:
- **Name:** For Personal Use
- **Author:** Byzi
- **Description:** For personal use

Konten weapon pack mengacu pada dokumentasi internal `BepInEx/plugins/mod/README.md` (MoreGuns).

## Cara Pakai Singkat

1. Pastikan GTFO sudah terpasang.
2. Salin isi repository ini ke direktori game GTFO (atau sinkronkan file yang dibutuhkan).
3. Jalankan game seperti biasa.
4. BepInEx akan memuat plugin dan konfigurasi dari folder `BepInEx`.

## Catatan

- Project ini disusun untuk kebutuhan personal, jadi kompatibilitas dengan setup orang lain belum tentu sama.
