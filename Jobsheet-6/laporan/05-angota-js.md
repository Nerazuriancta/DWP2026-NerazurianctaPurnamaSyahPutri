## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 5. Penjelasan File
File `anggota.js` digunakan untuk mengambil data anggota dari file JSON dan menampilkannya ke dalam tabel halaman anggota.

Data diambil menggunakan Fetch API dari file:
```text
../data/anggota.json
```
Setelah data berhasil diambil, setiap data anggota dibuat menjadi baris tabel (`<tr>`) menggunakan JavaScript.

File ini juga memiliki fitur:
- Loading indicator saat data sedang dimuat.
- Pengambilan data menggunakan `fetch()`.
- Pemeriksaan status response.
- Parsing data JSON.
- Menampilkan data anggota ke tabel.
- Penanganan error menggunakan `try...catch`.
- Menyembunyikan loading setelah proses selesai menggunakan `finally`.

## 5.1 Fungsi `muatDaftarAnggota()`
Fungsi utama pada file ini adalah `muatDaftarAnggota()`.
```js
async function muatDaftarAnggota() {
    const tbody = document.querySelector(".table-responsive table tbody");
    const loading = document.getElementById("loading-indicator");
    if (!tbody) return;
}
```
Fungsi menggunakan `async` karena di dalamnya terdapat proses pengambilan data yang membutuhkan waktu.

| Kode | Fungsi |
|---|---|
| `async function` | Membuat fungsi yang dapat menjalankan proses asynchronous |
| `querySelector()` | Mengambil elemen `<tbody>` pada tabel |
| `getElementById()` | Mengambil elemen loading berdasarkan ID |
| `if (!tbody) return` | Menghentikan fungsi jika tabel tidak ditemukan |

## 5.2 Menampilkan Loading
Sebelum mengambil data, loading indicator ditampilkan.
```js
    loading.style.display = "block";
    tbody.innerHTML = "";
```
`display = "block"` digunakan untuk menampilkan indikator loading.

Sedangkan `tbody.innerHTML = "" `digunakan untuk mengosongkan isi tabel sebelum data baru dimasukkan.

## 5.3 Menggunakan `try`
Proses pengambilan data diletakkan di dalam `try`.
```js
try {
    await new Promise((resolve) => setTimeout(resolve, 600));

    const res = await fetch("../data/anggota.json");
}
```
Bagian `setTimeout` memberikan jeda selama 600 milidetik sebelum data diambil.

Kemudian `fetch()` digunakan untuk mengambil data dari file `anggota.json`.

**Fungsi `await`**
`await` digunakan agar JavaScript menunggu proses asynchronous selesai sebelum melanjutkan ke baris berikutnya.

## 5.4 Mengecek Response
Setelah data diambil, response diperiksa
```js
if (!res.ok) {
    throw new Error("Gagal mengambil data (status " + res.status + ")");
}
```
`res.ok` digunakan untuk mengecek apakah response berhasil.

Jika response tidak berhasil, `throw new Error()` digunakan untuk membuat error agar dapat ditangani oleh bagian `catch`.

## 5.5 Mengubah Response Menjadi JSON
Data response kemudian diubah menjadi objek JavaScript.
```js
const daftarAnggota = await res.json();
```
`res.json()` digunakan untuk membaca isi file JSON dan mengubahnya menjadi data yang dapat digunakan JavaScript.

Variabel `daftarAnggota` berisi seluruh data anggota.

## 5.6 Menampilkan Data Anggota
Setiap anggota diproses menggunakan `forEach()`.
```js
daftarAnggota.forEach(function (anggota) {
    const tr = document.createElement("tr");
    ...
})
```
`forEach()` digunakan untuk melakukan perulangan terhadap setiap data anggota.

Kemudian `document.createElement("tr")` membuat baris tabel baru.

## 5.7 Membuat Isi Baris Tabel
Isi baris tabel dibuat menggunakan `innerHTML`.
```js
tr.innerHTML = 
    "<td>" + anggota.no_anggota + "</td>" +
    "<td>" + anggota.nama + "</td>" +
    "<td>" + anggota.alamat + "</td>" +
    "<td>" + anggota.no_hp + "/td" +
    "<td>" +
    "<button type=\"button\">Edit</button> " +
    "<button type=\"button\" class=\"btn-hapus\">Hapus</button>" +
    "</td>"
```
Data yang ditampilkan terdiri dari:
| Data JSON | Kolom Tabel |
|---|---|
| `anggota.no_anggota` | Nomor anggota |
| `anggota.nama` | Nama |
| `anggota.alamat` | Alamat |
| `anggota.no_hp` | Nomor HP |
| Tombol Edit | Aksi edit |
| Tombol Hapus | Aksi hapus |
Tombol Hapus diberikan class `btn-hapus`.

Class tersebut nantinya dapat ditangkap oleh fungsi `initHapusConfirm()` pada `app.js`.

## 5.8 Memasukkan Baris ke Tabel
Setelah baris dibuat, baris tersebut dimasukkan ke dalam `<tbody>`.
```js
tbody.appendChild(tr);
```
`appendChild()` digunakan untuk menambahkan elemen `<tr>` ke dalam tabel.

## 5.9 Penanganan Error
Jika terjadi kesalahan saat mengambil atau membaca data, bagian `catch` akan dijalankan.
```js
catch (err) {
    tbody.innerHTML = 
    "<tr><td colspan=\"5\">Gagal memuat data: " + err.message + "</td></tr>";
} 
```
Pesan error akan ditampilkan di dalam tabel.

`err.message` digunakan untuk mengambil pesan kesalahan yang terjadi.

## 5.10 `finally`
Bagian `finally` digunakan untuk menyembunyikan loading setelah proses selesai.
```js
finally {
    loading.style.display = "none";
}
```
`finally` tetap dijalankan baik proses pengambilan data berhasil maupun mengalami error.

Dengan begitu, loading indicator tidak akan terus tampil setelah proses selesai.

## 5.11 Menjalankan Fungsi Saat Halaman Dibuka
Pada bagian akhir terdapat:
```js
document.addEventListener("DOMContentLoaded", muatDaftarAnggota);
```
Kode tersebut membuat fungsi `muatDaftarAnggota()` dijalankan setelah struktur HTML selesai dimuat.

Jadi ketika halaman anggota dibuka, data anggota akan langsung dimuat dari file JSON.

## 5.12 Hubungan dengan `app.js`
File `anggota.js` bekerja bersama dengan `app.js`.

`anggota.js` bertugas mengambil dan menampilkan data anggota, sedangkan `app.js` menangani interaksi seperti konfirmasi hapus.

Contohnya, tombol Hapus yang dibuat oleh `anggota.js` memiliki class:
```js
class="btn-hapus"
```
Class tersebut kemudian dapat ditangkap oleh event delegation pada `app.js`.

Hal ini membuat tombol Hapus tetap dapat berfungsi walaupun tombol tersebut dibuat secara dinamis setelah data JSON selesai diambil.

## 5.13 Kesimpulan
File `anggota.js` digunakan untuk menampilkan data anggota dari `anggota.json` ke dalam tabel secara dinamis menggunakan Fetch API.

Program menggunakan `async/await` untuk menangani proses asynchronous, `try...catch` untuk menangani error, dan `finally` untuk memastikan loading indicator disembunyikan setelah proses selesai.

Dengan adanya `anggota.js`, data anggota tidak perlu ditulis satu per satu langsung di HTML karena data dapat diambil dari file JSON dan ditampilkan secara otomatis menggunakan JavaScript.