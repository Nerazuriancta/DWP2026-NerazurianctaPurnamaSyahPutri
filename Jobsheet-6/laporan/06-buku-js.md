## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 6. Penjelasan File 
File `buku.js` digunakan untuk mengambil data buku dari file JSON dan menampilkannya ke dalam tabel pada halaman buku.

Data buku diambil menggunakan Fetch API dari file:
```text
../data/buku.json
```

Setelah data berhasil diambil, setiap data buku dibuat menjadi baris tabel (`<tr>`) menggunakan JavaScript.

File ini memiliki beberapa fungsi, yaitu:
- Menampilkan loading indicator saat data sedang dimuat.
- Mengambil data buku menggunakan fetch().
- Mengecek response dari proses fetch().
- Mengubah response menjadi JSON.
- Menampilkan data buku ke dalam tabel.
- Menangani error menggunakan try...catch.
- Menyembunyikan loading setelah proses selesai menggunakan finally.

## 6.1 Fungi `muatDaftarBuku()`
Fungsi utama pada file ini adalah `muatDaftarBuku()`.
```js
async function muatDaftarBuku() {
    const tbody = document.querySelector(".table-responsive table tbody");
    const loading = document.getElementById("loading-indicator");
    if (!tbody) return;
}
```
Fungsi menggunakan `async` karena terdapat proses asynchronous saat mengambil data dari file JSON.
| Kode | Fungsi |
|---|---|
| `async function` | Membuat fungsi yang dapat menjalankan proses asynchronous |
| `querySelector()` | Mengambil elemen `<tbody>` pada tabel |
| `getElementById()` |Mengambil elemen loading |
| `if (!tbody) return` | Menghentikan fungsi jika elemen tabel tidak ditemukan |

## 6.2 Menampilkan Loading
Sebelum data buku diambil, loading indicator ditampilkan.
```js
loading.style.display = "block";
tbody.innerHTML = "";
```
`display = "block"` digunakan untuk menampilkan loading indicator.

Sedangkan `tbody.innerHTML = ""` digunakan untuk mengosongkan isi tabel sebelum data baru ditampilkan.

## 6.3 Simulasi Delay Jaringan
Pada bagian `try` terdapat simulasi delay.
```js
await new Promise((resolve) => setTimeout(resolve, 600));
```
Kode tersebut memberikan jeda selama 600 milidetik sebelum data buku diambil.

Tujuannya agar proses loading dapat terlihat pada halaman dan dapat digunakan untuk mensimulasikan kondisi ketika jaringan membutuhkan waktu untuk mengambil data.

## 6.4 Mengambil Data dengan `fetch()`
Data buku diambil dari file JSON menggunakan Fetch API.
```js
const res = await fetch("../data/buku.json");
```
`fetch()` digunakan untuk mengambil data dari file `buku.json`.

`await` membuat program menunggu sampai proses pengambilan data selesai.

## 6.5 Mengecek Response
Setelah data diambil, response diperiksa menggunakan `res.ok`.
```js
if (!res.ok) {
    throw new Error("Gagal mengambil data (status " + res.status + ")");
}
```
Jika response tidak berhasil, program akan membuat error menggunakan `throw new Error()`.

`res.status` digunakan untuk mendapatkan kode status dari response.

## 6.6 Mengubah Data menjadi JSON
Setelah response berhasil, data diubah menjadi JSON.
```js
const daftarBuku = await res.json();
```
`res.json()` digunakan untuk membaca data dari `buku.json`.

Data tersebut kemudian disimpan dalam variabel `daftarBuku`.

## 6.7 Melakukan Perulangan Data Buku
Setiap data buku diproses menggunakan `forEach()`.
```js
daftarBuku.forEach(function (buku) {
    const tr = document.createElement("tr");
})
```
`forEach()` digunakan untuk melakukan perulangan terhadap setiap data buku.

Kemudian `document.createElement("tr")` digunakan untuk membuat baris tabel baru.

## 6.8 Menampilkan Data Buku
Data buku dimasukkan ke dalam baris tabel menggunakan `innerHTML`.
```js
tr.innerHTML =
    "<td>" + buku.judul + "</td>" +
    "<td>" + buku.pengarang + "</td>" +
    "<td>" + buku.tahun + "</td>" +
    "<td>" + buku.stok + "</td>" +
    "<td>" +
    "<button type=\"button\">Edit</button> " +
    "<button type=\"button\" class=\"btn-hapus\">Hapus</button>" +
    "</td>";
```
Data yang ditampilkan terdiri dari:
| Data JSON | Kolom Tabel |
|---|---|
| `buku.judul` | Judul buku |
| `buku.pengarang` | Pengarang |
| `buku.tahun` | Tahun terbit |
| `buku.stok` | Jumlah stok |
| Tombol Edit | Aksi edit |
| Tombol Hapus | Aksi hapus |
Tombol Hapus menggunakan class `btn-hapus`.

Class tersebut dapat digunakan oleh `app.js` untuk menjalankan konfirmasi sebelum baris dihapus dari tampilan.

## 6.9 Menambahkan Baris ke Tabel
Setelah baris tabel dibuat, baris tersebut dimasukkan ke dalam `<tbody>`.
```js
tbody.appendChild(tr);
```
`appendChild()` digunakan untuk menambahkan elemen `<tr>` ke dalam tabel.

## 6.10 Penanganan Error
Jika terjadi kesalahan ketika mengambil atau membaca data, bagian catch akan dijalankan.
```js
catch (err) {
    tbody.innerHTML =
        "<tr><td colspan=\"5\">Gagal memuat data: " + err.message + "</td></tr>";
}
```
Pesan kesalahan akan ditampilkan di dalam tabel.

`err.message` digunakan untuk mengambil pesan error yang terjadi.

## 6.11 Menyembunyikan Loading dengan `finally`
Setelah proses selesai, loading indicator disembunyikan.
```js
finally {
    loading.style.display = "none";
}
```
Bagian `finally` tetap dijalankan baik ketika data berhasil diambil maupun ketika terjadi error.

Dengan demikian, loading indicator tidak akan terus tampil setelah proses selesai.

## 6.12 Menjalankan Fungsi Saat Halaman Dibuka
Pada bagian akhir terdapat:
```js
document.addEventListener("DOMContentLoaded", muatDaftarBuku);
```
Kode tersebut membuat fungsi `muatDaftarBuku()` dijalankan setelah struktur HTML selesai dimuat.

Jadi ketika halaman buku dibuka, data buku akan langsung diambil dari `buku.json` dan ditampilkan ke dalam tabel.

## 6.13 Hubungan dengan `app.js`
File `buku.js` bekerja bersama dengan `app.js`.

`buku.js` bertugas mengambil dan menampilkan data buku secara dinamis, sedangkan `app.js` menangani beberapa interaksi seperti konfirmasi tombol Hapus.

Tombol Hapus yang dibuat oleh `buku.js` memiliki class:
```js
class="btn-hapus"
```
Class tersebut kemudian dapat ditangkap oleh event delegation pada `app.js`.

Hal ini membuat tombol Hapus tetap dapat berfungsi walaupun tombol tersebut baru dibuat setelah data buku selesai diambil menggunakan `fetch()`.

## 6.14 Kesimpulan 
File `buku.js` digunakan untuk mengambil data buku dari `buku.json` dan menampilkannya secara dinamis ke dalam tabel menggunakan JavaScript.

Program menggunakan Fetch API, `async/await`, `forEach()`, `try...catch`, dan `finally`. Program juga memiliki loading indicator dan penanganan error agar proses pengambilan data lebih jelas bagi pengguna.

Dengan adanya `buku.js`, data buku tidak perlu ditulis secara manual satu per satu pada HTML karena data dapat diambil dari file JSON dan ditampilkan secara otomatis.