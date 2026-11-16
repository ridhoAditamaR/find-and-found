# PRD: FIND & FOUND

**Product Requirements Document** · Modul 6
**Desain:** https://www.figma.com/design/x9sLfizRo6rn7Do5p1Irqc
**Status:** Draf untuk direview tim

---

## 1. Product Overview

### 1.1 Ringkasan

FIND & FOUND adalah website untuk melaporkan, mencari, dan mengklaim barang hilang maupun temuan di lingkungan kampus. Semua laporan dikumpulkan di satu tempat dan klaim diverifikasi admin sebelum barang diserahkan.

### 1.2 Masalah yang dipecahkan

| Masalah | Dampak |
| --- | --- |
| Informasi barang hilang tersebar di grup chat dan media sosial | Mudah terlewat dan cepat tenggelam |
| Pencarian tidak terstruktur (tanpa kategori, lokasi, tanggal) | Pemilik sulit menemukan barangnya |
| Tidak ada verifikasi kepemilikan | Barang berisiko jatuh ke orang yang salah |
| Penemu tidak tahu harus menyerahkan barang ke mana | Barang temuan tidak kembali ke pemilik |

### 1.3 Tujuan

1. Mengumpulkan laporan barang hilang dan temuan dalam satu platform.
2. Mempercepat pencarian lewat filter kategori, lokasi, tanggal, dan status.
3. Memastikan barang kembali ke pemilik yang tepat lewat verifikasi klaim.
4. Memberi pengguna kepastian status laporan dan klaim.

### 1.4 Target pengguna (persona)

Persona di bawah disusun dari hasil perancangan Modul 1 sampai 5 dan bersifat asumsi sampai divalidasi lewat wawancara.

| Persona | Kebutuhan | Masalah saat ini |
| --- | --- | --- |
| Mahasiswa Pencari (kehilangan barang) | Menemukan barang cepat dan mengklaimnya dengan aman | Harus bertanya ke banyak grup, tidak tahu statusnya |
| Mahasiswa Penemu (menemukan barang) | Cara mudah menyerahkan barang dan melapor | Bingung menitipkan ke siapa dan takut salah serah |
| Admin / petugas kampus | Memverifikasi klaim dan mencatat barang | Pencatatan manual, sulit memastikan pemilik asli |

### 1.5 User story utama

- Sebagai mahasiswa pencari, saya ingin mencari barang dengan filter agar cepat menemukannya.
- Sebagai mahasiswa pencari, saya ingin mengajukan klaim dengan bukti agar barang bisa diverifikasi.
- Sebagai mahasiswa penemu, saya ingin melaporkan barang temuan lengkap dengan foto dan tempat penyimpanan.
- Sebagai admin, saya ingin memeriksa klaim dan mengubah status barang agar barang kembali ke pemilik yang benar.

### 1.6 Indikator keberhasilan (target awal)

- Mahasiswa dapat menyelesaikan laporan dalam waktu kurang dari 3 menit.
- Sedikitnya 80% klaim dapat diselesaikan tanpa bantuan.
- Tingkat kepuasan pengguna pada uji prototipe (diukur lewat survei singkat).

Angka di atas adalah target yang perlu disepakati tim.

### 1.7 Ruang lingkup

| Termasuk (MVP) | Tidak termasuk (tahap berikutnya) |
| --- | --- |
| Login, pencarian dan filter, detail barang | Aplikasi mobile native |
| Klaim bertahap dengan unggah bukti dan kode tiket | Notifikasi push dan email otomatis |
| Lapor kehilangan dan lapor penemuan | Pencocokan otomatis laporan hilang dan temuan |
| Dashboard admin untuk verifikasi | Statistik dan laporan analitik |

## 2. Alur Sistem (ringkas)

1. **Autentikasi:** login dengan email kampus; jika gagal, tampil pesan error dan pengguna mengulang.
2. **Pencarian:** Beranda atau Katalog, lalu filter, lalu Detail barang. Jika hasil kosong, tampil layar Data tidak ditemukan (Reset filter atau Lapor kehilangan).
3. **Klaim:** Detail, pilih jadwal, formulir 2 langkah, modal konfirmasi, lalu halaman Sukses dengan kode tiket.
4. **Verifikasi (admin):** memeriksa ciri khusus dan bukti, lalu klaim disetujui atau ditolak beserta alasannya.
5. **Pelaporan:** Lapor kehilangan atau Lapor penemuan, lalu halaman Sukses dengan kode laporan.
6. **Dashboard admin:** admin masuk lewat Login, melihat ringkasan di dashboard, memilih klaim yang diperiksa, lalu menyetujui atau menolak klaim.
7. **Status laporan:** pengguna memantau status laporan dan klaim beserta timeline dan notifikasi.

## 3. Feature Breakdown (per section Figma)

Prioritas: **P1** wajib MVP, **P2** sebaiknya ada, **P3** opsional.

| Frame Figma | Fitur | Komponen utama | State penting | Prioritas |
| --- | --- | --- | --- | --- |
| 01_Login | Masuk dengan email kampus dan kata sandi | TextField, PasswordField, Button | Default, error | P1 |
| 02_Login_Error | Pesan kesalahan kredensial | Banner error, field state Error | Error | P1 |
| 03_Beranda | Pencarian cepat, tombol lapor, cara kerja, laporan terbaru | NavBar, FilterChip, ItemCard, Button | Default, hover | P1 |
| 04_Katalog | Daftar barang dengan filter kategori dan status | FilterChip, ItemCard, pagination | Chip terpilih, hasil banyak | P1 |
| 05_Detail | Detail barang, jadwal pengambilan, rincian biaya | Badge, FilterChip (jadwal), Button | Slot terpilih, status barang | P1 |
| 06_Form_Data | Klaim langkah 1: data barang | Stepper, TextField | Terisi otomatis dari Detail | P1 |
| 07_Form_Bukti | Klaim langkah 2: ciri khusus dan unggah bukti | Stepper, area teks, zona unggah | Unggah berhasil | P1 |
| 08_Modal_Konfirmasi | Konfirmasi sebelum kirim klaim | Modal overlay, Button | Tampil, tutup | P1 |
| 09_Sukses | Kode tiket dan ringkasan klaim | Kartu tiket, Badge | Status Proses klaim | P1 |
| 10_Kosong | Data tidak ditemukan | Ilustrasi, Button | Filter aktif | P1 |
| 11_Lapor_Kehilangan | Formulir lapor kehilangan | TextField, area teks, zona unggah | Terisi, error | P1 |
| 12_Lapor_Penemuan | Formulir lapor penemuan | FilterChip (penyimpanan), zona unggah | Terisi, error | P1 |
| 13 dan 14 Sukses lapor | Kode laporan dan status | Kartu tiket, Badge | Hilang, Ditemukan | P2 |
| 15_Dashboard_Admin | Ringkasan angka, daftar klaim perlu verifikasi, laporan terbaru, ubah status barang | Sidebar, kartu angka, tabel, Badge, Button | Klaim menunggu | P1 |
| 16_Verifikasi_Klaim | Memeriksa jawaban dan bukti pengklaim, mencocokkan dengan ciri khusus tercatat, setujui atau tolak | Kartu data, daftar pemeriksaan, Button | Disetujui, ditolak | P1 |
| 17_Status_Laporan | Daftar laporan dan klaim pengguna, timeline proses, notifikasi | NavBar, FilterChip, tabel, Badge | Per tahap proses | P2 |

### 3.1 Aturan bisnis penting

- Ciri khusus barang **tidak ditampilkan** di halaman publik; hanya dipakai admin untuk verifikasi klaim.
- Nomor kontak tidak dipublikasikan sebelum klaim disetujui.
- Satu barang yang sedang diklaim berstatus **Proses klaim** dan tidak dapat diklaim ulang oleh orang lain.
- Status barang: Hilang, Ditemukan, Proses klaim, Dikembalikan.
- Kode tiket klaim berformat `FF-TAHUN-NNNN`; kode laporan `FF-L-` (kehilangan) atau `FF-T-` (penemuan).

### 3.2 Rencana model data (usulan)

| Tabel | Isi utama |
| --- | --- |
| users | id, nama, email kampus, kata sandi (hash), role (mahasiswa atau admin) |
| items | id, tipe (hilang atau temuan), nama, kategori, deskripsi umum, ciri khusus (tersembunyi), lokasi, tanggal, tempat penyimpanan, status, foto, pelapor |
| categories | id, nama |
| locations | id, nama |
| claims | id, item, pengklaim, ciri khusus yang dijawab, bukti, jadwal pengambilan, kode tiket, status, catatan admin |
| notifications | id, user, pesan, dibaca |

## 4. Design Tokens dan Komponen (untuk Modul 7)

### 4.1 Figma Variables

Dua tingkat: **Primitives** (28 variabel: warna, spasi, radius) dan **Semantics** (36 variabel). Implementasi kode memakai nama Semantics sebagai CSS variable atau konfigurasi tema.

| Kelompok | Token Semantics (contoh) |
| --- | --- |
| Latar | `color/bg/page`, `color/bg/surface`, `color/bg/subtle`, `color/bg/brand`, `color/bg/brand-subtle` |
| Teks | `color/text/primary`, `secondary`, `muted`, `inverse`, `brand`, `error` |
| Aksi | `color/action/primary`, `primary-hover`, `primary-pressed`, `disabled` |
| Status | `color/status/found-*`, `lost-*`, `claim-*`, `error-bg` |
| Spasi | `space/xs` 8, `sm` 16, `md` 24, `lg` 32, `xl` 48, `2xl` 64 |
| Radius | `radius/sm` 8, `md` 16, `pill` penuh |

### 4.2 Tipografi

Font Inter. Skala 12, 16, 20, 24, 32, 40 px: Display/40 (Bold), Heading/1 32 (Bold), Heading/2 24 dan Heading/3 20 (Semi Bold), Body/16 (Regular dan Semi Bold), Caption/12 (Regular dan Semi Bold).

### 4.3 Komponen yang harus dibangun

| Komponen | Varian dan state | Catatan perilaku |
| --- | --- | --- |
| Button | Primary dan Secondary; Default, Hover, Pressed, Disabled | Disabled jika kolom wajib belum terisi |
| FilterChip | Selected False dan True | Klik untuk memilih atau membatalkan |
| PasswordField | Visible False dan True; Default dan Error | Ikon mata menampilkan atau menyembunyikan kata sandi |
| TextField | Default, Filled, Error | Border merah dan pesan saat error |
| Badge | Ditemukan, Hilang, Proses klaim, Dikembalikan | Warna sesuai token status |
| NavBar | Active Beranda, Cari barang, atau Status laporan | Tautan ke Beranda, Katalog, dan Status laporan |
| Stepper | Langkah 1 dan 2 | Langkah selesai ditandai centang |
| ItemCard | Foto, badge, nama, lokasi, tanggal | Klik membuka Detail |

### 4.4 Aksesibilitas dan layout

- Kontras teks minimal 4,5:1 (WCAG 2.2 AA).
- Jarak mengikuti kelipatan 8 piksel.
- Desain acuan desktop 1440 px; layout responsif ditentukan pada Modul 7.

## 5. Tech Stack Plan

Usulan awal (perlu disepakati tim sebelum Modul 7):

| Lapisan | Usulan | Alasan |
| --- | --- | --- |
| Frontend | HTML, CSS (Tailwind CSS), JavaScript | Cepat mengubah token Figma menjadi kelas utilitas |
| Backend | PHP | Sesuai kebutuhan form, sesi login, dan unggah berkas |
| Basis data | MySQL | Cocok untuk relasi pengguna, barang, dan klaim |
| Autentikasi | Sesi PHP, kata sandi di-hash | Cukup untuk MVP |
| Penyimpanan berkas | Folder `uploads/` di server | Foto barang dan bukti (maks 5 MB, JPG atau PNG) |
| Kontrol versi | Git dan GitHub | Branch per fitur dan Pull Request |
| Desain | Figma | Sumber acuan komponen dan token |

Alternatif yang dapat dipertimbangkan: framework frontend (misalnya React) dengan API terpisah, jika seluruh anggota tim terbiasa.

## 6. Kebutuhan Non-Fungsional

- **Keamanan:** kata sandi di-hash, validasi unggahan (tipe dan ukuran), ciri khusus tidak terekspos ke publik.
- **Kinerja:** halaman Katalog memuat 6 kartu per halaman dengan pagination.
- **Kegunaan:** formulir panjang dipecah per langkah; setiap layar punya jalur kembali.
- **Privasi:** kontak pelapor hanya terlihat oleh admin atau pihak yang klaimnya disetujui.
