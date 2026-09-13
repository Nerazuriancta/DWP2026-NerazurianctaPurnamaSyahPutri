## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 1. Perubahan pada File HTML

## 1.1 `<tbody>` yang sekarang kosong
Perbandingan langsung dengan `buku/list.html` di [Jobsheet1](../../Jobsheet-1/): dulu `<tbody>` berisi 5 baris `<tr>` yang ditulis manual. Sekarang:
```html
<tbody>
    <!-- Baris diisi dinamis oleh assets/js/buku.js via fetch('../data/buku.json') -->
</tbody>
```
`<tbody>` benar-benar kosong — hanya berisi komentar HTML (`<!-- ... -->`, tidak tampil di layar, sekadar catatan untuk siapa pun yang membaca kode) yang menjelaskan bahwa baris-barisnya akan diisi belakangan oleh JavaScript setelah halaman dimuat. Kalau kamu membuka file ini langsung tanpa JavaScript aktif, tabelnya akan tampil kosong — hanya baris judul kolom (`<thead>`) yang terlihat.

## 1.2 Elemen Baru: Loading Indicator
```html
<p id="loading-indicator" style="display:none;">Memuat data...</p>
```
Elemen `<p>` baru diletakkan di antara kolom pencarian dan tabel. Dua hal perlu diperhatikan:
- `id="loading-indicator"`, "kait" yang dicari JavaScript lewat `document.getElementById("loading-indicator")`.
- `style="display: none;"`, ini contoh inline stylem CSS yang ditulis langsung di attribut style sebuah elemen HTML, bukan di file `style.css` Elemen ini sengaja disembunyikan sejak awal (display:none) karena teks "Memuat data..." hanya perlu terlihat sesaat, selama proses pengambilan data berlangsung, JavaScript yang akan menampilkan dan menyembunyikannya kembali secara terprogram, Karena gaya ini hanya dipakai satu kali di satu elemen spesifik dan statusnya akan terus diubah lewat JavaScript (bukan lewat selector CSS), menulisnya inline di sini lebih praktis dibanding membuat aturan baru khusus di `style.css`.

## 1.3 Urutan Tag `<script>` yang Baru
```html
<script src="../assets/js/app.js"></script>
<script src="../assets/js/buku.js"></script>
```
Sekarang ada dua tag `<script>` di `buku/list.html` (dan `anggota/list.html` memuat `app.js` + `anggota.js`), dimuat berurutan dari atas ke bawah, sama seperti browser membaca HTML dari atas kebawah. `app.js` (berisi fungsi-fungsi umum seperti menu hamburger, validasi form, filter tabel) selalu dimuat lebih dulu, baru disusul file khusus halaman (`buku.js` atau `anggota.js`) yang isinya spesifik untuk satu halaman itu saja. Halaman `buku/tambah.html` dan Beranda tidak memuat `buku.js`/`anggota.js` sama sekali, karena halaman itu tidak punya tabel yang perlu diisi data dinamis.

## 1.4 Kenapa `buku.js` dan `anggota.js` Dipisah, Bukan Digabung ke `app.js`?
Ini keputusan desain yang baik untuk dipahami: `app.js` berisi fungsi-fungsi yang relevan di banyak halaman sekaligus (menu hamburger muncul di semua halaman, validasi form hanya di halaman "tambah", filter tabel di halaman "list"). Sedangkan logika mengambil data JSON spesifik untuk satu jenis data (buku atau anggota) — memisahkannya ke file sendiri-sendiri membuat tiap file lebih pendek, lebih mudah dicari, dan halaman yang tidak membutuhkannya (misalnya Beranda) tidak perlu memuat kode yang tidak relevan sama sekali.