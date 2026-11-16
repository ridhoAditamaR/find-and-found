# FIND & FOUND

Platform web untuk melaporkan, mencari, dan mengklaim **barang hilang maupun temuan** di lingkungan kampus, supaya informasi tidak lagi tersebar di grup chat dan media sosial.

> Status: **Modul 6, fondasi repositori dan dokumentasi.** Kode website dikerjakan pada Modul 7.

## Tentang proyek

Mahasiswa yang kehilangan dompet, ponsel, laptop, kartu mahasiswa, atau kunci biasanya bertanya di grup chat. Informasinya cepat tenggelam, dan tidak ada cara pasti untuk memastikan barang kembali ke pemilik yang benar.

FIND & FOUND menyatukan semua laporan di satu tempat, menyediakan pencarian dengan filter, dan menambahkan **verifikasi klaim** oleh admin sebelum barang diserahkan.

## Fitur utama

- Login dengan email kampus.
- Pencarian dan filter barang (nama, kategori, lokasi, tanggal, status).
- Detail barang dengan pilihan jadwal pengambilan.
- Pengajuan klaim bertahap dengan unggah bukti kepemilikan dan kode tiket.
- Lapor kehilangan dan lapor penemuan.
- Pemantauan status laporan dan klaim lewat halaman Status laporan.
- Dashboard admin untuk memeriksa klaim dan memperbarui status barang.

Rincian lengkap ada di [PRD.md](PRD.md). Panduan kerja Git tim ada di [docs/git-workflow.md](docs/git-workflow.md).

## Tim dan peran

| Peran | Tanggung jawab | Anggota | GitHub |
| --- | --- | --- | --- |
| Repo Maintainer | Inisialisasi repo, undang tim, `.gitignore`, struktur folder | [isi nama] | [@username] |
| PRD: Scope & User Flow | Latar belakang produk, target pengguna, alur sistem | [isi nama] | [@username] |
| PRD: Tech & Components | Daftar section Figma, token desain, rencana teknologi | [isi nama] | [@username] |
| README & PR Reviewer | README profil tim dan validasi PR rekan sebelum merge | [isi nama] | [@username] |

Jika tim hanya 3 orang, satu anggota memegang dua peran.

## Desain

- Desain Figma: https://www.figma.com/design/x9sLfizRo6rn7Do5p1Irqc
- Prototipe interaktif: [isi link Figma Prototype publik]

Prototipe terdiri dari 17 frame (01_Login sampai 17_Status_Laporan, termasuk dashboard admin dan verifikasi klaim) dan dibuat dengan Auto Layout serta Figma Variables dua tingkat (Primitives dan Semantics).

## Struktur repositori

```
find-and-found/
├── README.md        # profil tim, peran, tautan Figma
├── PRD.md           # product requirements document
├── .gitignore
└── docs/
    ├── git-workflow.md  # panduan Git dan pembagian branch tim
    ├── user-flow/       # diagram alur (draw.io dan gambar)
    └── wireframe/       # wireframe dan tangkapan layar prototipe
```

Folder kode (misalnya `src/`) ditambahkan pada Modul 7.

## Alur kerja Git

1. **Clone:** `git clone <url-repo>` lalu `git pull origin main` sebelum mulai.
2. **Branch:** jangan commit langsung ke `main`. Buat branch per tugas.
   - Dokumen: `docs/prd-scope`, `docs/prd-tech`, `docs/readme-setup`
   - Fitur (Modul 7): `feat/nama-fitur`
3. **Commit:** pesan singkat dengan awalan, misalnya:
   - `docs: tambah product overview pada PRD`
   - `docs: lengkapi tabel peran di README`
   - `fix: perbaiki tautan Figma`
4. **Push:** `git push -u origin nama-branch`
5. **Pull Request:** buka PR ke `main`, minta review minimal satu rekan, tulis komentar review, lalu merge setelah disetujui.

```bash
git clone <url-repo>
git checkout -b docs/prd-scope
git add PRD.md
git commit -m "docs: tambah product overview pada PRD"
git push -u origin docs/prd-scope
```

## Rencana berikutnya

- **Modul 7:** implementasi antarmuka berdasarkan section Figma dan token desain pada PRD.
