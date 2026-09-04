## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 2. Penjelasan File `style.css`

File `style.css` digunakan untuk mengatur **tampilan dan desain** website SIMPUS-Mini. SS ini mengatur warna, ukuran teks, jarak, tata letak, tabel, formulir, tombol, header, dan footer.

Pada file inin digunakan **Flexbox** untuk mengatur tata letak header dan navigasi, serta **CSS GRID** untuk mengatur kartu statistik pada halaman beranda.

## 2.1 Fungsi Setiap Bagian

| Bagian/Kode | Fungsi |
|---|---|
| `*` | Melakukan pengaturan dasar pada seluruh elemen. |
| `body` | Mengatur tampilan dasar halaman seperti font, warna teks, background, dan jarak antarbaris. |
| `a` | Mengatur tampilan semua link. |
| `a:hover` | Mengatur tampilan link ketika kursor diarahkan ke link. |
| `header` | Mengatur tampilan bagian header dan navigasi menggunakan Flexbox. |
| `header h1` | Mengatur ukuran judul utama. |
| `header nav ul` | Mengatur daftar menu agar tampil secara horizontal. |
| `main` | Mengatur ukuran maksimal dan posisi konten utama. |
| `section` | Mengatur tampilan setiap bagian konten seperti background, padding, dan bayangan. |
| `section h2` | Mengatur tampilan judul pada section. |
| `main section:nth-of-type(2)` | Mengatur section kedua menggunakan CSS Grid untuk kartu statistik. |
| `main section:nth-of-type(2) h2` | Membuat judul Ringkasan memenuhi seluruh kolom Grid. |
| `article` | Mengatur tampilan kartu statistik. |
| `table` | Mengatur ukuran dan struktur tabel. |
| `th, td` | Mengatur isi dan judul kolom tabel. |
| `thead` | Mengatur warna bagian kepala tabel. |
| `tbody tr:nth-child(even)` | Memberikan warna berbeda pada baris tabel genap. |
| `tbody tr:hover` | Mengubah warna baris tabel ketika diarahkan kursor. |
| `td button` | Mengatur tampilan tombol pada tabel. |
| `form` | Mengatur jarak antar bagian pada formulir. |
| `form label` | Mengatur tampilan label input. |
| `form input, form select` | Mengatur tampilan kolom input dan pilihan. |
| `form button[type="submit"]` | Mengatur tampilan tombol Simpan. |
| `footer` | Mengatur tampilan bagian bawah halaman. |

## 2.2 Penjelasan Kode

### 1. Reset & Base
```css
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```
Kode tersebut digunakan untuk menghapus margin dan padding bawaan browser serta mengatur ukuran elemen menggunakan `border-box`.

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
    color: #2b2b2b;
    background-color: #f5f6f8;
    line-height: 1.5;
}
```
Bagian `body` mengatur jenis font, warna text, warna latar belakang, dan jarak antarbaris pada halaman.

### 2. Link
```css
a{
    color: #1d5b8a;
    text-decoration: none;
}
```
Mengatur warna link dan menghilangkan garis bawah;

```css
a:hover {
    text-decoration: underline;
}
```
Menampilkan garis bawah ketika kursor diarahkan ke link.

### 3. Header dan Navbar
```css
header {
    background-color: #1d5b8a;
    color: #fff;
    padding: 1rem 1.5rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
}
```
Bagian ini mengatur tampilan header menggunakan **Flexbox**. Judul dan menu navigasi dapat tersusun secara horizontal dan memiliki jarak yang sesuai.

```css
header nav ul {
    list-style: none;
    display: flex;
    gap: 1.25rem;
}
```
Mengatur menu navigasi agar tampil secara horizontal dan menghilangkan tanda daftar.

### 4. Main Layout dan Section
```css
main {
    max-width: 1000px;
    margin: 2rem auto;
    padding: 0 1.5rem;
}
```
Mengatur lebar maksimal konten utama dan menempatkannya di tengah halaman.

```css
section {
    background-color: #fff;
    border-radius: 8px;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
}
```
Mengatur tampilan setiap section dengan background putih, sudut membulat, jarak dalam, dan bayangan.

### 5. Kartu Statistik
```css
main section:nth-of-type(2) {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}
```
Menggunakan **CSS Grid** untuk membuat tiga kolom kartu statistik.

```css
main section:nth-of-type(2) h2 {
    grid-column: 1 / -1;
}
```
Membuat judul Ringkasan memenuhi seluruh lebar Grid sehingga berada di atas kartu statistik.

```css
main section-:nth-of-type(2) article {
    background-color: #eef4fa;
    border-radius: 8px;
    padding: 1.25rem;
    text-align: center;
}
```
Mengatur tampilan kartu statistik.

### 6. Tabel
```css
table {
    width: 100%;
    border-collapse: collapse;
}
```
Membuat tabel menggunakan seluruh lebar container dan menggabungkan garis antar sel.

```css
th, td {
    text-align: left;
    padding: 0.65rem 0.75rem;
    border-bottom: 1px solid #e2e6ea;
}
```
Mengatur posisi teks, jarak dalam, dan garis bawah pada setiap kolom tabel.

```css
thead {
    background-olor: #1d5b8a;
    color #fff;
}
```
Memberikan warna biru pada bagian judul tabel

```css
tbody tr:nth-child(even) {
    background-color: #f7f9fb;
}
```
Memberikan warna berbeda pada setiap baris tabel genap

```css
tbody tr:hover {
    background-color: #eef4fa;
}
```
Mengubah warna baris tabel ketika kursor diarahkan ke baris tersebut

### 7. Tombol
```css
td button {
    padding: 0.35rem 0.7rem;
    margin-right: 0.35rem;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
```
Mengatur ukuran, jarak, bentuk, dan tampilan kursor pada tombol

```css
td button:first-of-type {
    background-color: #f0ad4e;
    color: #fff;
}
```
Memberikan warna kuning pada tombol Edit.

```css
td button:last-of-type {
    background-color: #d9534f;
    color: #fff;
}
```
Memberikan warna merah pada tombol Hapus

### 8. Form
```css
form input, form select { 
    width: 100%; 
    max-width: 400px; 
    padding: 0.55rem 0.7rem; 
    border: 1px solid #cdd4da; 
    border-radius: 4px; 
}
```
Mengatur ukuran, padding, garis, dan sudut pada input dan select

```css
form button[type="submit"] { 
    background-color: #1d5b8a; 
    color: #fff; 
    border: none; 
    padding: 0.6rem 1.5rem; 
    border-radius: 4px; 
    cursor: pointer; }
```
Mengatur tampilan tombol Simpan.

### 9. Footer
```css
footer { 
    text-align: center; 
    padding: 1.25rem; 
    color: #7a8794; 
    font-size: 0.9rem; 
}
```
Mengatur footer agar teks berada di tengah dengan ukuran dan warna yang lebih kecil

## 2.3 Kesimpulan

File [style.css](../assets/css/style.css) berfungsi untuk mengatur tampilan seluruh halaman pada website SIMPUS-Mini. CSS digunakan untuk membuat tampilan website lebih rapi dan konsisten, mulai dari header, navigasi, konten utama, kartu statistik, tabel, formulir, tombol, hingga footer. Dalam file ini digunakan Flexbox untuk mengatur header dan navigasi serta CSS Grid untuk mengatur kartu statistik.