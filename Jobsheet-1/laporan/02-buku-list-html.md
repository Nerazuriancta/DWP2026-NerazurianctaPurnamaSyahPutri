## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. Penjelasan File `buku/list.html`

File [buku/list.html](../buku/list.html) merupakan halaman yang digunakan untuk menampilkan **daftar buku** pada sistem SIMPUS-Mini. Halaman ini berisi menu navigasi, tabel daftar buku, informasi setiap buku, serta tombol aksi untuk mengedit dan menghapus data.

Bagian utama halaman menampilkan tabel yang berisi informasi **judul buku, pengarang, tahun terbit, stok, dan aksi**. Data buku ditampilkan menggunakan beberapa baris tabel (`tr`).

## 2.1 Fungsi Setiap Bagian

| Bagian/Kode | Fungsi |
|---|---|
| `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| `<html lang="id">` | Membuka dokumen HTML dengan bahasa Indonesia. |
| `<head>` | Berisi informasi halaman yang tidak ditampilkan langsung. |
| `<meta charset="UTF-8">` | Mengatur format karakter agar dapat ditampilkan dengan benar. |
| `<title>` | Menentukan judul halaman pada tab browser. |
| `<body>` | Menampung seluruh konten halaman. |
| `<header>` | Menampilkan bagian kepala halaman. |
| `<h1>` | Menampilkan judul utama SIMPUS-Mini. |
| `<nav>` | Menampung menu navigasi. |
| `<a href="../index.html">` | Membuat tautan kembali ke halaman beranda. |
| `<a href="list.html">` | Membuat tautan menuju halaman daftar buku. |
| `<a href="tambah.html">` | Membuat tautan menuju halaman tambah buku. |
| `<main>` | Menampung konten utama halaman. |
| `<section>` | Mengelompokkan konten daftar buku. |
| `<table>` | Membuat tabel untuk menampilkan data buku. |
| `<thead>` | Menampung bagian kepala tabel. |
| `<tbody>` | Menampung isi atau data tabel. |
| `<tr>` | Membuat satu baris tabel. |
| `<th>` | Membuat judul kolom tabel. |
| `<td>` | Menampilkan data pada setiap kolom tabel. |
| `<button>` | Membuat tombol Edit dan Hapus. |
| `<footer>` | Menampilkan bagian bawah halaman. |

## 2.2 Penjelasan Kode Per Baris

| Baris | Kode | Penjelasan |
|---|---|---|
| 1 | `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| 2 | `<html lang="id">` | Membuka dokumen HTML dan menentukan bahasa Indonesia. |
| 3 | `<head>` | Membuka bagian informasi dokumen. |
| 4 | `<meta charset="UTF-8">` | Mengatur format karakter menggunakan UTF-8. |
| 5 | `<title>SIMPUS-Mini \| Daftar Buku</title>` | Menampilkan judul halaman pada tab browser. |
| 6 | `</head>` | Menutup bagian `head`. |
| 7 | `<body>` | Membuka bagian isi halaman. |
| 8 | `<header>` | Membuka bagian header. |
| 9 | `<h1>SIMPUS-Mini</h1>` | Menampilkan judul utama aplikasi. |
| 10 | `<nav>` | Membuka bagian navigasi. |
| 11 | `<ul>` | Membuka daftar menu. |
| 12 | Link `../index.html` | Mengarahkan pengguna ke halaman beranda. |
| 13 | Link `list.html` | Mengarahkan pengguna ke halaman daftar buku. |
| 14 | Link `tambah.html` | Mengarahkan pengguna ke halaman tambah buku. |
| 15 | Link `../anggota/list.html` | Mengarahkan pengguna ke halaman daftar anggota. |
| 16–18 | Penutup `ul`, `nav`, dan `header` | Menutup bagian daftar menu, navigasi, dan header. |
| 20 | `<main>` | Membuka bagian konten utama. |
| 21 | `<section>` | Membuka bagian daftar buku. |
| 22 | `<h2>Daftar Buku</h2>` | Menampilkan judul halaman Daftar Buku. |
| 23 | `<table>` | Membuat tabel untuk data buku. |
| 24 | `<thead>` | Membuka bagian kepala tabel. |
| 25 | `<tr>` | Membuat baris judul kolom. |
| 26–30 | `<th>` | Menampilkan judul kolom Judul, Pengarang, Tahun, Stok, dan Aksi. |
| 31–33 | Penutup `tr` dan `thead` | Menutup baris dan bagian kepala tabel. |
| 34 | `<tbody>` | Membuka bagian isi tabel. |
| Baris data buku | `<tr>` dan `<td>` | Menampilkan data setiap buku dalam bentuk baris dan kolom. |
| Kolom Judul | `<td>` | Menampilkan judul buku. |
| Kolom Pengarang | `<td>` | Menampilkan nama pengarang buku. |
| Kolom Tahun | `<td>` | Menampilkan tahun terbit buku. |
| Kolom Stok | `<td>` | Menampilkan jumlah stok buku yang tersedia. |
| Kolom Aksi | `<td>` | Menampung tombol untuk melakukan aksi pada data. |
| `<button type="button">Edit</button>` | Membuat tombol untuk mengedit data buku. |
| `<button type="button">Hapus</button>` | Membuat tombol untuk menghapus data buku. |
| `</tbody>` | Menutup bagian isi tabel. |
| `</table>` | Menutup tabel. |
| `</section>` | Menutup bagian daftar buku. |
| `</main>` | Menutup konten utama. |
| `<footer>` | Membuka bagian footer. |
| `<p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 1</p>` | Menampilkan informasi copyright dan Jobsheet 1. |
| `</footer>` | Menutup bagian footer. |
| `</body>` | Menutup seluruh isi halaman. |
| `</html>` | Menutup dokumen HTML. |

## 2.3 Kesimpulan

File [buku/list.html](../buku/list.html) berfungsi untuk menampilkan daftar buku yang tersedia pada sistem SIMPUS-Mini. Informasi buku ditampilkan dalam bentuk tabel yang terdiri dari judul, pengarang, tahun, stok, dan aksi. Halaman ini juga menyediakan tombol **Edit** dan **Hapus** sebagai persiapan untuk melakukan pengelolaan data buku.