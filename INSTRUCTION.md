# Setup Guide — GitHub Profile README

## 1. Ganti data pribadi

Sebelum di-push, cari & ganti bagian berikut di `README.md`:

| Cari | Ganti dengan |
|---|---|
| `your-email@gmail.com` | alamat Gmail kamu |
| `linkedin.com/in/your-linkedin` | URL profil LinkedIn kamu |
| `falle46` (di URL stats/trophy/streak/snake) | biarkan jika username GitHub kamu tetap `falle46` |

## 2. Struktur folder terbaru

```
.
├── .github/workflows/main.yml
├── assets/
│   └── tech-marquee.svg   ← WAJIB di-upload, dipakai README
├── instruction.md
├── LICENSE
└── README.md
```

Upload folder `assets/` beserta isinya persis di root repository (sejajar dengan `README.md`). README memanggilnya lewat path relatif `./assets/tech-marquee.svg`, jadi kalau foldernya tidak ada, gambar itu akan tampil rusak/broken image.

## 3. Cara kerja tiap komponen

- **Header & footer** — `capsule-render` (waving banner + gradient), otomatis animasi tanpa perlu file tambahan.
- **Nama animasi** — `readme-typing-svg` dengan `repeat=false`, jadi nama diketik sekali lalu tetap tampil (tidak dihapus-tulis ulang terus).
- **Tagline** — `readme-typing-svg` versi kedua, teks bergantian terus-menerus (looping).
- **Tech stack marquee** — `assets/tech-marquee.svg`, file SVG custom berisi barisan logo yang di-scroll otomatis tanpa putus (seamless loop) pakai animasi SVG native, jadi benar-benar bergerak, bukan sekadar gambar diam. Highlight-nya sengaja dibatasi ±12 logo utama supaya loading tetap ringan.
- **Grid lengkap tech stack** — dibungkus `<details>` (collapsible) berisi semua kategori (Languages, Frontend, Backend, Mobile, Database, Cloud/DevOps, Tools, AI/ML). Ini statis (skillicons.dev tidak menyediakan animasi per-logo untuk grid sebesar ini), tinggal hapus baris/nama yang tidak relevan.
- **Stats, top languages, streak** — `github-readme-stats` & `streak-stats`, auto-update setiap README di-load (tidak perlu workflow tambahan).
- **Trophy** — `github-profile-trophy`, auto-update sesuai aktivitas GitHub kamu.
- **Snake animation** — dihasilkan oleh `.github/workflows/main.yml` (workflow yang sudah ada, **tidak perlu diubah**), lalu ditampilkan lewat tag `<picture>` supaya otomatis ganti terang/gelap sesuai tema GitHub pengguna.

## 3. Workflow snake (main.yml)

Workflow yang sudah kamu punya sudah benar dan tidak perlu diubah:
- Berjalan otomatis tiap hari (`cron`), saat push ke `main`, atau manual (`workflow_dispatch`).
- Menghasilkan file SVG snake ke branch `output`.
- README mengambil file itu langsung dari branch `output` via `raw.githubusercontent.com`.

Pastikan repository **Settings → Actions → General → Workflow permissions** diset ke **"Read and write permissions"** agar workflow bisa push ke branch `output`.

## 4. Kredit layanan (opsional, boleh dihapus)

- capsule-render — https://github.com/kyechan99/capsule-render
- readme-typing-svg — https://github.com/DenverCoder1/readme-typing-svg
- github-readme-stats — https://github.com/anuraghazra/github-readme-stats
- github-readme-streak-stats — https://github.com/DenverCoder1/github-readme-streak-stats
- github-profile-trophy — https://github.com/ryo-ma/github-profile-trophy
- skillicons.dev — https://github.com/tandpfun/skill-icons
- Platane/snk (snake animation) — https://github.com/Platane/snk
