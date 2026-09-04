## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 3. Penjelasan File `buku/tambah.html`

File [buku/tambah.html](../buku/tambah.html) merupakan halaman yang digunakan untuk **menambahkan data buku baru** pada sistem SIMPUS-Mini. Halaman ini menyediakan sebuah formulir yang harus diisi pengguna.

Data yang dapat dimasukkan meliputi **judul buku, nama pengarang, tahun terbit, ISBN, stok, dan kategori buku**. Setelah semua data yang diperlukan diisi, pengguna dapat menekan tombol **Simpan** untuk mengirimkan data.

## 3.1 Fungsi Setiap Bagian

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
| `<section>` | Mengelompokkan bagian formulir tambah buku. |
| `<form>` | Membuat formulir untuk memasukkan data buku. |
| `<label>` | Menampilkan keterangan untuk setiap input. |
| `<input type="text">` | Membuat kolom untuk memasukkan teks. |
| `<input type="number">` | Membuat kolom untuk memasukkan angka. |
| `<select>` | Membuat pilihan kategori buku. |
| `<option>` | Menampilkan pilihan di dalam kategori. |
| `<button type="submit">` | Membuat tombol untuk mengirimkan data formulir. |
| `required` | Menandakan bahwa kolom wajib diisi. |
| `min` dan `max` | Menentukan batas nilai angka yang dapat dimasukkan. |
| `<footer>` | Menampilkan bagian bawah halaman. |

## 3.2 Penjelasan Kode Per Baris

| Baris | Kode | Penjelasan |
|---|---|---|
| 1 | `<!DOCTYPE html>` | Menentukan bahwa dokumen menggunakan HTML5. |
| 2 | `<html lang="id">` | Membuka dokumen HTML dengan bahasa Indonesia. |
| 3 | `<head>` | Membuka bagian informasi dokumen. |
| 4 | `<meta charset="UTF-8">` | Mengatur format karakter menggunakan UTF-8. |
| 5 | `<title>SIMPUS-Mini \| Tambah Buku</title>` | Menampilkan judul halaman pada tab browser. |
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
| 16–18 | Penutup `ul`, `nav`, dan `header` | Menutup bagian menu navigasi dan header. |
| 20 | `<main>` | Membuka bagian konten utama. |
| 21 | `<section>` | Membuka bagian formulir tambah buku. |
| 22 | `<h2>Tambah Buku</h2>` | Menampilkan judul halaman Tambah Buku. |
| 23 | `<form>` | Membuka formulir untuk memasukkan data buku. |
| 24–27 | Input Judul | Menampilkan label dan kolom untuk memasukkan judul buku. |
| 28–31 | Input Pengarang | Menampilkan label dan kolom untuk memasukkan nama pengarang. |
| 32–35 | Input Tahun Terbit | Menampilkan kolom angka untuk memasukkan tahun terbit antara 1900 sampai 2026. |
| 36–39 | Input ISBN | Menampilkan kolom untuk memasukkan nomor ISBN buku. |
| 40–43 | Input Stok | Menampilkan kolom angka untuk memasukkan jumlah stok buku dengan nilai minimal 0. |
| 44–50 | Pilihan Kategori | Menampilkan pilihan kategori Fiksi, Non-Fiksi, dan Referensi. |
| 51–53 | Tombol Simpan | Membuat tombol untuk mengirimkan data formulir. |
| 54 | `</form>` | Menutup formulir. |
| 55 | `</section>` | Menutup bagian tambah buku. |
| 56 | `</main>` | Menutup bagian konten utama. |
| 58 | `<footer>` | Membuka bagian footer. |
| 59 | `<p>&copy; 2026 SIMPUS-Mini &mdash; Jobsheet 1</p>` | Menampilkan informasi copyright dan Jobsheet 1. |
| 60 | `</footer>` | Menutup bagian footer. |
| 61 | `</body>` | Menutup seluruh isi halaman. |
| 62 | `</html>` | Menutup dokumen HTML. |

## 3.3 Kesimpulan

File [buku/tambah.html](../buku/tambah.html) berfungsi sebagai halaman untuk menambahkan data buku baru ke dalam sistem SIMPUS-Mini. Halaman ini menggunakan elemen `form` untuk mengumpulkan data buku, seperti judul, pengarang, tahun terbit, ISBN, stok, dan kategori. Penggunaan atribut `required`, `min`, dan `max` membantu memastikan data yang dimasukkan sesuai dengan ketentuan yang telah dibuat.