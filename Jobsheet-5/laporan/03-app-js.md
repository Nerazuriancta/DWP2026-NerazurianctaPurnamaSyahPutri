## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 3. Penjelasan File `app.js`
File `app.js` digunakan untuk menambahkan interaktivitas pada aplikasi SIMPUS-Mini menggunakan JavaScript. File ini menangani beberapa fungsi pada halaman, yaitu menu hamburger, konfirmasi penghapusan data, pencarian tabel secara langsung, dan validasi form sebelum data dikirim.

## 3.1 Fungsi Utama
| Bagian | Fungsi |
|---|---|
| `initNavToggle()` | Mengatur tombol hamburger untuk membuka dan menutup menu navigasi. |
| `initHapusConfirm()` | Menampilkan konfirmasi sebelum data dihapus |
| `initTableFilter()` | Menampilkan pencarian/filter data pada tabel secara real-time |
| `tampilkanError()` | Menampilkan pesan kesalahan pada input form |
| `hapusError()` | Menghapus pesan kesalahan pada form sebelum dikirim |
| `initValidasiForm()` | Melakukan validasi data pada form sebelum dikirim |
| `DOMContentLoaded` | Menjalankan seluruh fungsi JavaScript setelah halaman selesai dimuat |

## 3.2 Penjelasan Kode
### 1. Hamburger Menu
```js
// === Hamburger menu (JS-driven, menggantikan checkbox hack) ===
function initNavToggle() {
    const toggleBtn =document.getElementById("nav-toggle-btn");
    const nav = document.querySelector("header nav");
    if (!toggleBtn || !nav) return;

    toggleBtn.addEventListener("click", function() {
        nav.classList.toggle("nav-open");
    });
}
```
| Kode | Fungsi |
|---|---|
| `function initNavToggle()` | Membuat fungsi untuk mengatur menu hamburger |
| `getElementById()` | Mengambil elemen tombol hamburger berdasarkan ID |
| `querySelector("header nav")` | Mengambil elemen tombol hamburger berdasarkan ID|
| `if (!toggleBtn  !nav) return` | Menghentikan fungsi jika tombol atau navigasi tidak ditemukan |
| `addEventListener("click", ...` | Menjalankan perintah ketika tombol diklik |
| `classList.toggle("nav-open")` | Menambahkan atau menghapus class `nav-open` untuk membuka atau menutup menu |

2. Konfirmasi Hapus
```js
// === Konfirmasi hapus (front-end only, belum ke server) ===
function initHapusConfirm() {
    document.querySelectorAll(".btn-hapus").forEach(function (btn) {
        btn.addEventListener("click", function (){
            const row = btn.closest("tr");
            const nama = row ? row.querySelector("td")?.textContent : "data ini";
            const yakin = confirm("Yakin ingin menghapus \"" + nama + "\"?");
            if (yakin && row) {
                row.remove();
            }
        });
    });
}
```
| Kode | Fungsi |
|---|---|
| `querySelectorAll(".btn-hapus")` | Mengambil semua tombol dengan class `btn-hapus` |
| `forEach()` | Memproses setiap tombol hapus |
| `addEventListener("click", ...` | Menjalankan fungsi ketika tombol hapus diklik |
| `closest("tr")` | Mengambil baris tabel tempat kolom berada |
| `querySelector("td")` | Mengambil data pada kolom pertama tabel |
| `confirm()` | Menampilkan pertanyaan konfirmasi kepada pengguna |
| `row.remove()` | Menghapus bari dari tampilan tabel jika pengguna memilih yakin |

3. Filter/Pencarian Tabel
```js
// === Filter/pencarian tabl real-time ===
function initTableFilter() {
    const input = document.getElementaryById("search-input");
    const table = document.querySelector(".table-responsive table");
    if (!input || !table) return;

    input.addEventListener("keyup", function () {
        const keyword = input.value.toLowerCase();
        const rows = table.querySelectorAll("tbody ty");
        rows.forEach(function (row) {
            const teks = row.textContent.toLowerCase();
            row.computedStyleMap.display = teks.includes(keyword) ? "" : "none";
        });
    });
}
```
| Kode | Fungsi |
|---|---|
| `getElementaryById()` | Digunakan untuk mengambil elemen pencarian berdasarkan ID|
| `querySelector()` | Mengambil tabel yang berada di dalam `.table-responsive` |
| `keyup` | Menjalankan filter ketika pengguna mengetik pada kolom pencarian |
| `toLowerCase()` | Mengubah teks menjadi huruf kecil agar pencarian tidak membedakan huruf besar dan kecil |
| `querySelectorAll(""tbody tr)` | Mengambil seluruh baris data pada tabel |
| `textContent` | Mengambil teks yang terdapat pada setiap baris |
| `includes(keyword)` | Mengecek apakah teks baris mengandung kata yang dicari |
| `display` | Mengatur baris agar ditampilkan atau disembunyikan |

4. Menampilkan Pesan Error
```js
function tampilkanError(input, pesan) {
    hapusError(input);
    const span = document.createElement("span");
    span.className = "error";
    span.textContent = pesan;
    input.insertAdjacentEelement("afterend", span);
}
```
| Kode | Fungsi |
|---|---|
| `tampilkanError()` | Membuat fungsi untuk menampilkan pesan kesalahan |
| `hapusError(input)` | Menghapus pesan error sebelumnya agar tidak muncul ganda |
| `createElement("span")` | Membuat elemen `<span>` baru |
| `className = "error"` | Memberikan class `error` pada elemen |
| `textContent = pesan` | Mengisi elemen dengan pesan kesalahan |
| `insertAdjacentElement()` | Menempatkan pesan error setelah elemen input |

5. Menghapus Pesan Error
```js
function hapusError(input) {
    const next = input.nextElementSibling;
    if (next && next.classList.contains("error")) {
        next.remove();
    }
}
```
| Kode | Fungsi |
|---|---|
| `nextElementSibling` | Mengambil elemen yang berada setelah input |
| `classList.contains("error")` | Mengecek apakah elemen tersebut memiliki class `error` |
| `remove()` | Menghapus pesan error di halaman |

6. Validasi Form
```js
function initValidasiForm() {
    const form = document.getElementById("form-tambah");
    if (!form) return;

    form.addEventListener("submit", function (e) {
        let valid = true;
    
    ....

    });
}
```
Bagian ini digunakan untuk melakukan pengecekan data sebelum form dikirim.
| Data | Validasi |
|---|---|
| Judul/Nama | Tidak boleh kosong |
| Pengarang	| Tidak boleh kosong |
| Tahun	| Harus berada di antara 1900–2026 |
| Stok | Tidak boleh kosong atau bernilai negatif |
Jika terdapat data yang tidak sesuai, fungsi `tampilkanError()` digunakan untuk memberikan pesan kesalahan dan `e.preventDefault()` mencegah form dikirim.

7. Menjalankan JavaScript
```js
document.addEventListener("DOMContentLoaded", function () {
    initNavToggle();
    initHapusConfirm();
    initTableFilter();
    initValidasiForm();
})
```
| Kode | Fungsi |
|---|---|
| `DOMContentLoaded` | Menunggu sampai struktur HTML selesai dimuat |
| `initNavToggle()` | Menjalankan fungsi menu hamburger |
| `initHapusConfirm()` | Menjalankan fungsi konfirmasi hapus |
| `initTableFilter()` | Menjalankan fungsi pencarian tabel |
| `initValidasiForm()` | Menjalankan fungsi validasi form |

## 3.3 Kesimpulan 
File `app.js` digunakan untuk menambahkan fungsi interaktif pada SIMPUS-Mini. JavaScript digunakan untuk mengatur menu hamburger, memberikan konfirmasi saat menghapus data, melakukan pencarian tabel, serta memvalidasi data pada form. Dengan adanya JavaScript, halaman SIMPUS-Mini menjadi lebih interaktif dan tidak hanya menampilkan halaman HTML secara statis.