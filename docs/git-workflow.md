# Panduan Git dan Pembagian Branch Tim

Dokumen ini menjelaskan langkah kerja Git dari nol sampai Pull Request pertama, sesuai alur Modul 6: **Init dan Clone, Docs Branching, Commit Markdown, PR dan Merge**.

## 1. Persiapan (semua anggota)

1. Pasang Git, lalu atur identitas (sekali saja):
   ```bash
   git config --global user.name "Nama Kamu"
   git config --global user.email "email-github-kamu@contoh.com"
   ```
2. Pastikan sudah punya akun GitHub dan sudah login.

## 2. Repo Maintainer: membuat repositori

1. Di GitHub: **New repository**, nama `find-and-found`, centang **Add a README file**, lalu **Create repository**.
2. Undang anggota: **Settings, Collaborators, Add people**.
3. (Disarankan) Lindungi `main`: **Settings, Branches, Add rule** untuk `main`, aktifkan **Require a pull request before merging** agar tidak ada yang push langsung ke `main`.
4. Clone ke komputer:
   ```bash
   git clone https://github.com/<username>/find-and-found.git
   cd find-and-found
   ```
5. Commit awal (satu kali, langsung ke `main` sebelum perlindungan diaktifkan): tambahkan `.gitignore` dan folder `docs/`, lalu:
   ```bash
   git add .gitignore docs/
   git commit -m "chore: inisialisasi struktur repositori"
   git push origin main
   ```

## 3. Alur kerja tiap anggota

```bash
git clone https://github.com/<username>/find-and-found.git   # sekali saja
cd find-and-found
git checkout main
git pull origin main                  # selalu ambil versi terbaru
git checkout -b docs/nama-tugas       # buat branch sendiri
# ... edit file Markdown ...
git status                            # cek berkas yang berubah
git add NAMA_FILE.md
git commit -m "docs: ringkasan perubahan"
git push -u origin docs/nama-tugas
```

Lalu di GitHub klik **Compare and pull request**, isi judul dan deskripsi, dan pilih reviewer.

## 4. Pembagian branch per peran

| Peran | Branch | Berkas yang dikerjakan |
| --- | --- | --- |
| Repo Maintainer | `chore/repo-setup` | `.gitignore`, struktur `docs/`, pengaturan repo |
| PRD: Scope & User Flow | `docs/prd-scope` | `PRD.md` bagian 1 sampai 2 |
| PRD: Tech & Components | `docs/prd-tech` | `PRD.md` bagian 3 sampai 5 |
| README & PR Reviewer | `docs/readme-setup` | `README.md` (profil tim, peran, tautan Figma) |

Tiap PR sebaiknya direview oleh anggota lain, misalnya:

| PR milik | Direview oleh |
| --- | --- |
| Repo Maintainer | README & PR Reviewer |
| PRD: Scope & User Flow | PRD: Tech & Components |
| PRD: Tech & Components | PRD: Scope & User Flow |
| README & PR Reviewer | Repo Maintainer |

## 5. Cara melakukan review

1. Buka Pull Request rekan, lalu tab **Files changed**.
2. Klik tanda **+** di samping baris untuk memberi komentar spesifik (misalnya typo, bagian PRD yang kurang jelas).
3. Klik **Review changes**, tulis ringkasan, lalu pilih **Approve** atau **Request changes**.
4. Setelah disetujui, klik **Merge pull request**, lalu **Confirm merge**.

Komentar dan persetujuan ini adalah **bukti review** yang dinilai (10% kolaborasi dan review).

## 6. Setelah PR di-merge

```bash
git checkout main
git pull origin main
git branch -d docs/nama-tugas        # hapus branch lokal
```

## 7. Menangani konflik

Konflik muncul jika dua orang mengubah baris yang sama pada `PRD.md`. Cara mencegahnya:

- Kerjakan **bagian yang berbeda** (lihat tabel pembagian di atas).
- Jalankan `git pull origin main` sebelum mulai dan sebelum push.

Jika tetap terjadi konflik, Git menandai bagian bentrok dengan `<<<<<<<`, `=======`, `>>>>>>>`. Edit berkas agar isinya benar, hapus tanda tersebut, lalu:

```bash
git add PRD.md
git commit -m "fix: selesaikan konflik pada PRD"
git push
```

## 8. Bukti untuk penilaian

- **Riwayat branch:** setiap anggota punya commit di branch masing-masing. Lihat dengan `git log --oneline --graph --all`.
- **Riwayat PR:** tab **Pull requests** di GitHub menunjukkan PR yang sudah di-merge beserta komentar review.
- **Commit message** jelas, dengan awalan `docs:`, `chore:`, atau `fix:`.

## 9. Perintah yang sering dipakai

| Perintah | Fungsi |
| --- | --- |
| `git status` | Melihat berkas yang berubah |
| `git diff` | Melihat isi perubahan |
| `git log --oneline` | Melihat riwayat commit singkat |
| `git branch` | Melihat daftar branch lokal |
| `git checkout -b nama` | Membuat dan pindah ke branch baru |
| `git pull origin main` | Mengambil versi terbaru `main` |
| `git push -u origin nama` | Mengirim branch ke GitHub |
