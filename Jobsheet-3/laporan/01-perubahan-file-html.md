## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. Perubahan File `HTML`

Pada Jobsheet 3, dilakukan beberapa perubahan pada file [index.html](../index.html) untuk mendukung tampilan website yang lebih responsif dan menambahkan menu navigasi berbentuk ikon hamburger.

## 1.1 Perubahan yang Dilakukan

| Bagian | Perubahan | Fungsi |
|---|---|---|
| Meta Viewport | Menambahkan `<meta name="viewport" content="width=device-width, initial-scale=1">` | Agar tampilan website dapat menyesuaikan ukuran layar perangkat. |
| Checkbox | Menambahkan `<input type="checkbox" id="nav-toggle" class="nav-toggle">` | Digunakan sebagai kontrol untuk membuka dan menutup menu navigasi. |
| Ikon Hamburger | Menambahkan `<label for="nav-toggle" class="nav-toggle-label">&#9776;</label>` | Menampilkan ikon hamburger dan menghubungkannya dengan checkbox. |
| Path CSS | Menggunakan `href="../Jobsheet-3/assets/css/style.css"` | Menghubungkan file HTML dengan file CSS yang berada pada folder Jobsheet-3. |

## 1.2 Penjelasan Perubahan

### 1. Penambahan Meta Viewport
```css
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Kode tersebut ditambahkan agar tampilan halaman dapat menyesuaikan dengan ukutan layar perangkat, terutama pada perangkat mobile.

### 2. Penambahan Checkbox
```css
<input type="checkbox" id="nav-toggle" class="nav-toggle">
```
Checkbox digunakan sebagai kontrol menu navigasi. Checkbox ini dapat digunakan bersama CSS untuk menampilkan atau menyembunyikan menu ketika ikon hamburger ditekan.

### 3. Penambahan Ikon Hamburger
```css
<label for="nav-toggle" class="nav-toggle-label">&#9776;</label>
```
Kode tersebut menampilkan ikon hamburger menggunakan karakter `&#9776;` Atribut `for="nav-toggle"` menghubungkan ikon tersebut dengan checkbox yang memiliki `id="nav-toggle"`.

Ketika ikon hamburger ditekan, checkbox akan berubah status dan CSS dapat digunakan untuk mengatur apakah menu navigasi ditampilkan atau disembunyikan.

### 4. Penambahan Path File CSS
```css
<link rel="stylesheet" href="../Jobsheet-3/assets/css/style.css">
```
Path tersebut digunakan untuk menghubungkan halaman HTML dengan file [style.css](../assets/css/style.css) yang berada di dalam folder [style.css](../assets/css/style.css) pada Jobsheet 3.

## 1.3 Kesimpulan

Pada Jobsheet 3, file HTML dimodifikasi dengan menambahkan meta viewport, checkbox, dan ikon hamburger. Perubahan tersebut bertujuan untuk mendukung navigasi yang lebih responsif, terutama pada perangkat dengan ukuran layar yang lebih kecil.