## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 4. Penjelasan File `anggota/list.html`

File [anggota/list.html](../anggota/list.html) merupakan halaman yang digunakan untuk menampilkan **daftar anggota perpustakaan** pada sistem SIMPUS-Mini. Halaman ini berisi menu navigasi, tabel data anggota, serta tombol aksi untuk mengedit dan menghapus data anggota.

Data anggota ditampilkan dalam bentuk tabel yang berisi **nomor anggota, nama, alamat, nomor HP, dan aksi**. Setiap anggota ditampilkan dalam satu baris tabel.

## 4.1 Fungsi Setiap Bagian

| Bagian/Kode | Fungsi |
|---|---|
| `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| `<html lang="id">` | Membuka dokumen HTML dan menentukan bahasa Indonesia. |
| `<head>` | Berisi informasi halaman yang tidak ditampilkan langsung. |
| `<meta charset="UTF-8">` | Mengatur format karakter. |
| `<title>` | Menentukan judul halaman pada tab browser. |
| `<body>` | Menampung seluruh konten halaman. |
| `<header>` | Menampilkan bagian kepala halaman. |
| `<h1>` | Menampilkan judul utama SIMPUS-Mini. |
| `<nav>` | Menampung menu navigasi. |
| `<a href="...">` | Membuat tautan menuju halaman lain. |
| `<main>` | Menampung konten utama halaman. |
| `<section>` | Mengelompokkan bagian daftar anggota. |
| `<table>` | Membuat tabel untuk menampilkan data anggota. |
| `<thead>` | Menampung bagian kepala tabel. |
| `<tbody>` | Menampung isi data tabel. |
| `<tr>` | Membuat satu baris tabel. |
| `<th>` | Membuat judul setiap kolom tabel. |
| `<td>` | Menampilkan data anggota pada tabel. |
| `<button>` | Membuat tombol Edit dan Hapus. |
| `<footer>` | Menampilkan bagian bawah halaman. |

## 4.2 Penjelasan Kode Per Baris

| Baris | Kode | Penjelasan |
|---|---|---|
| 1 | `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| 2 | `<html lang="id">` | Membuka dokumen HTML dengan bahasa Indonesia. |
| 3 | `<head>` | Membuka bagian informasi dokumen. |
| 4 | `<meta charset="UTF-8">` | Mengatur format karakter menggunakan UTF-8. |
| 5 | `<title>SIMPUS-Mini \| Daftar Anggota</title>` | Menampilkan judul halaman pada tab browser. |
| 6 | `</head>` | Menutup bagian `head`. |
| 7 | `<body>` | Membuka bagian isi halaman. |
| 8 | `<header>` | Membuka bagian header. |
| 9 | `<h1>SIMPUS-Mini</h1>` | Menampilkan judul utama aplikasi. |
| 10 | `<nav>` | Membuka bagian navigasi. |
| 11 | `<ul>` | Membuka daftar menu navigasi. |
| 12 | Link `../index.html` | Mengarahkan pengguna ke halaman beranda. |
| 13 | Link `../buku/list.html` | Mengarahkan pengguna ke halaman daftar buku. |
| 14 | Link `list.html` | Mengarahkan pengguna ke halaman daftar anggota. |
| 15 | Link `tambah.html` | Mengarahkan pengguna ke halaman tambah anggota. |
| 16–18 | Penutup `ul`, `nav`, dan `header` | Menutup bagian daftar menu, navigasi, dan header. |
| 20 | `<main>` | Membuka bagian konten utama. |
| 21 | `<section>` | Membuka bagian daftar anggota. |
| 22 | `<h2>Daftar Anggota</h2>` | Menampilkan judul halaman Daftar Anggota. |
| 23 | `<table>` | Membuat tabel untuk menampilkan data anggota. |
| 24 | `<thead>` | Membuka bagian kepala tabel. |
| 25 | `<tr>` | Membuat satu baris judul tabel. |
| 26 | `<th>No. Anggota</th>` | Menampilkan judul kolom nomor anggota. |
| 27 | `<th>Nama</th>` | Menampilkan judul kolom nama anggota. |
| 28 | `<th>Alamat</th>` | Menampilkan judul kolom alamat anggota. |
| 29 | `<th>No. HP</th>` | Menampilkan judul kolom nomor HP anggota. |
| 30 | `<th>Aksi</th>` | Menampilkan judul kolom aksi. |
| 31–33 | Penutup `tr` dan `thead` | Menutup baris dan bagian kepala tabel. |
| 34 | `<tbody>` | Membuka bagian isi tabel. |
| Baris data anggota | `<tr>` | Membuat satu baris untuk setiap data anggota. |
| `<td>A001</td>` dan seterusnya | Menampilkan nomor anggota. |
| `<td>Nama Anggota</td>` | Menampilkan nama anggota. |
| `<td>Alamat</td>` | Menampilkan alamat anggota. |
| `<td>No. HP</td>` | Menampilkan nomor HP anggota. |
| `<button type="button">Edit</button>` | Membuat tombol untuk mengedit data anggota. |
| `<button type="button">Hapus</button>` | Membuat tombol untuk menghapus data anggota. |
| `</tbody>` | Menutup bagian isi tabel. |
| `</table>` | Menutup tabel. |
| `</section>` | Menutup bagian daftar anggota. |
| `</main>` | Menutup bagian konten utama. |
| `<footer>` | Membuka bagian footer. |
| `<p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 1</p>` | Menampilkan informasi copyright dan Jobsheet 1. |
| `</footer>` | Menutup bagian footer. |
| `</body>` | Menutup seluruh isi halaman. |
| `</html>` | Menutup dokumen HTML. |

## 4.3 Kesimpulan

File [anggota/list.html](../anggota/list.html) berfungsi untuk menampilkan daftar anggota perpustakaan dalam sistem SIMPUS-Mini. Data anggota disajikan dalam bentuk tabel yang berisi nomor anggota, nama, alamat, nomor HP, dan aksi. Tombol **Edit** dan **Hapus** disediakan sebagai bagian dari pengelolaan data anggota.