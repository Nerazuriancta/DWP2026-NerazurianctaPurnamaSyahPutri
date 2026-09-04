## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 5. Penjelasan File `anggota/tambah.html`

File [anggota/tambah.html](../anggota/tambah.html) merupakan halaman yang digunakan untuk **menambahkan data anggota baru** pada sistem SIMPUS-Mini. Halaman ini menyediakan formulir yang digunakan untuk memasukkan data anggota.

Data yang dimasukkan dapat berupa **nomor anggota, nama, alamat, dan nomor HP**. Setelah data diisi, pengguna dapat menekan tombol **Simpan** untuk mengirimkan data anggota.

## 5.1 Fungsi Setiap Bagian

| Bagian/Kode | Fungsi |
|---|---|
| `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| `<html lang="id">` | Membuka dokumen HTML dan menentukan bahasa Indonesia. |
| `<head>` | Berisi informasi halaman yang tidak ditampilkan langsung. |
| `<meta charset="UTF-8">` | Mengatur format karakter. |
| `<title>` | Menentukan judul halaman pada tab browser. |
| `<body>` | Menampung seluruh konten halaman. |
| `<header>` | Menampilkan bagian kepala halaman. |
| `<nav>` | Menampung menu navigasi. |
| `<main>` | Menampung konten utama halaman. |
| `<section>` | Mengelompokkan bagian formulir tambah anggota. |
| `<form>` | Membuat formulir untuk memasukkan data anggota. |
| `<label>` | Menampilkan keterangan setiap input. |
| `<input>` | Membuat kolom untuk memasukkan data. |
| `<button type="submit">` | Membuat tombol untuk mengirimkan data formulir. |
| `required` | Menandakan bahwa kolom wajib diisi. |
| `<footer>` | Menampilkan bagian bawah halaman. |

## 5.2 Penjelasan Kode Per Baris

| Baris | Kode | Penjelasan |
|---|---|---|
| 1 | `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| 2 | `<html lang="id">` | Membuka dokumen HTML dengan bahasa Indonesia. |
| 3 | `<head>` | Membuka bagian informasi dokumen. |
| 4 | `<meta charset="UTF-8">` | Mengatur format karakter menggunakan UTF-8. |
| 5 | `<title>SIMPUS-Mini \| Tambah Anggota</title>` | Menampilkan judul halaman pada tab browser. |
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
| 16–18 | Penutup `ul`, `nav`, dan `header` | Menutup bagian menu navigasi dan header. |
| 20 | `<main>` | Membuka bagian konten utama. |
| 21 | `<section>` | Membuka bagian formulir tambah anggota. |
| 22 | `<h2>Tambah Anggota</h2>` | Menampilkan judul halaman Tambah Anggota. |
| 23 | `<form>` | Membuka formulir untuk memasukkan data anggota. |
| Bagian nomor anggota | `<label>` dan `<input>` | Menampilkan kolom untuk memasukkan nomor anggota. |
| Bagian nama | `<label>` dan `<input>` | Menampilkan kolom untuk memasukkan nama anggota. |
| Bagian alamat | `<label>` dan `<input>` | Menampilkan kolom untuk memasukkan alamat anggota. |
| Bagian nomor HP | `<label>` dan `<input>` | Menampilkan kolom untuk memasukkan nomor HP anggota. |
| `<button type="submit">Simpan</button>` | Membuat tombol untuk mengirimkan data anggota. |
| `</form>` | Menutup formulir. |
| `</section>` | Menutup bagian tambah anggota. |
| `</main>` | Menutup bagian konten utama. |
| `<footer>` | Membuka bagian footer. |
| `<p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 1</p>` | Menampilkan informasi copyright dan Jobsheet 1. |
| `</footer>` | Menutup bagian footer. |
| `</body>` | Menutup seluruh isi halaman. |
| `</html>` | Menutup dokumen HTML. |

## 5.3 Kesimpulan

File [anggota/tambah.html](../anggota/tambah.html) berfungsi sebagai halaman untuk menambahkan data anggota baru ke dalam sistem SIMPUS-Mini. Halaman ini menggunakan elemen `form` untuk mengumpulkan data anggota, seperti nomor anggota, nama, alamat, dan nomor HP. Tombol **Simpan** digunakan untuk mengirimkan data yang telah diisi.