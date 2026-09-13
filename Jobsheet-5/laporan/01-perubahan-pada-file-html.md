## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. Perubahan Di File HTML
Perubahan kecil di HTML yang menjadi "kait" (hook) bagi JavaScript untuk mencari elemen yang perlu dimanipulasi. Tanpa perubahan-perubahan ini, `app.js` tidak
akan punya elemen yang bisa ditemukan lewat `getElementById`/`querySelector`.

## 1.1 Hamburger: dari Checkbox ke Tombol Asli
Sebelumnya menu hamburger dibuat dari pasangan `<input type="checkbox">` + `<label>`.
Sekarang:
```html
<button type="button" id="nav-toggle-btn" class="nav-toggle-label" aria-label="Menu">&#9776;</button>
```
- Elemen `<input type="checkbox">` dihapus - tidak dibutuhkan karena status buka/tutup menu sekarang disimpan lewat class CS yang ditambahkan JavaScript, bukan status "tercentang" checkbox.
- `<label>` diganti jadi `<button type="button">` - tombol asli memang dirancang untuk diklik, dengan `id="nav-toggle-btn"` sebagai "kait" supaya `document.getElementById("nav-toggle-btn")` di `app.js` bisa menemukannya.
- Class `nav-toggle-label` tetap dipertahankan namanya (meski elemennya sudah bukan `<label>` lagi) supaya gaya CSS yang sudah ada (ukuran, warna, font, dll.) tidak perlu ditulis ulang.
- `aria-label="Menu"` adalah atribut baru untuk aksesibilitas - memberi tahu pembaca layat (screen reader) bahwa tombol berisi simbol ☰ ini fungsinya adalah "Menu", karena teks `&#9776;` sendiri tidak bermakna apapun kalau dibacakan sebagai teks biasa.

## 1.2 Kolom Pencarian Baru di Halaman Daftar
Di `buku/list.html` dan `anggota/list.html`, ada `<div>` baru sebelum tabel:
```html
<div class="search-box">
    <label for="search-input">Cari Judul Buku</label>
    <input type="text" id="search-input" placeholder="Ketik judul buku...">
</div>
```
- Pola `<label for="...">` + `<input id="...">` ini sama persis dengan pola form pada jobsheet 1 meskipun `<input>` ini tidak berasa dalam `<form>`, karena memang tidak dimaksudkan untuk "disimpan" atau di-submit, hanya untuk dibaca nilainya secara langsung oleh JavaScript setiap kali diketik.
- Atribut `placeholder` adalah atribut HTML yang belum pernah dipakai di jobsheet-jobsheet sebelumnya - menampilkan teks abu-abu (misalnya "Ketik judul buku...") du dalam kotak input selama masih kosong, teka itu otomatis hilang begitu pengguna mulai mengetik. Beda dengan `value`, teks placeholder tidak ikut terkirim kalau form di-submit.
- `id="search-input"` adalah "kait" yang dicari `documen.getElemntById("search-input")` di `app.js`.

## 1.3 Class `btn-hapus` di Tombol Hapus
```html
<button type="button">Edit</button>
<button type="button" class="btn-hapus">Hapus</button>
```
Dari Jobsheet 1, kedua tombol Edit dan Hapus di kolom "Aksi" sejak awal memang belum berfungsi (`type="button"` tanpa aksi apapun). Sekarang tombol Hapus diberi `class"btn-hapus"` bukan untuk keperluan gaya CSS (warnanya tetap diatur lewat `:last-of-type`), melainkan supaya `document.querySelectorAll(".btn-hapus")` di `app.js` bisa menemukan semua tombol Hapus sekaligus di satu halaman. Tombol Edit tidak diberi class apapun karena jobsheet ini memang belum menambahkan fungsi apapun untuknya.

## 1.4 `id="form-tambah"` di Form Tambah Buku/Anggota
```html
<form id="form-tambah">
```
Kedua form (buku/tambah.html dan anggota/tambah.html) sekarang punya `id="form-tambah"` di tag `<form>`nya, sebelumnya tag `<form>` tidak punya atribut apapun. `id` ini adalah "kait" yang dicari `document.getElementById("form-tambah")` supaya JavaScript bisa memasang event listener submit untuk validasi. Perhatikan kedua form memakai `id` yang sama (`form-tambah`) meskipun field-fieldnya berbeda (Judul/Pengarang untuk buku, Nama/No. Anggota untuk anggota) — ini aman karena `id` hanya perlu unik di dalam satu halaman, dan kedua form ini
berada di halaman yang berbeda.