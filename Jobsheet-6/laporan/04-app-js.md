## Nama     : Nerazuriancta Purnama Syah Putri
## NIM      : 254107020117
## Kelas    : TI-2D

# 4. Perubahan Pada File `app.js`
Perubahan pada file `app.js` untuk menyesuaikan JavaScript dengan data yang sekarang dirender secara dinamis menggunakan `fetch`.

Perubahan utama terdapat pada fungsi `initHapusConfirm()`. Sebelumnya tombol hapus dicari langsung menggunakan `querySelectorAll()`, sedangkan sekarang menggunakan event delegation pada `document`.

Selain itu, fungsi hamburger menu, pencarian tabel, validasi form, dan `DOMContentLoaded` tetap digunakan.

## 4.1 Konfirmasi Hapus dengan Event Delegation
Perubahan utama terdapat pada fungsi `initHapusConfirm()`.
```js
function initHapusConfirm() {
    document.addEventListener("click", function (e) {
        const btn = e.target.closest(".btn-hapus");
        if (!btn) return;

        const row = btn.closest("tr");
        const nama = row ? row.querySelector("td")?.textContent : "data ini";
        const yakin = confirm("Yakin ingin menghapus \"" + nama + "\"?");
        if (yakin && row) {
            row.remove();
        }
    });
}
```
**Event Delegation**
Event delegation digunakan karena baris tabel sekarang dapat dibuat secara dinamis melalui `fetch`. Artinya, tombol `.btn-hapus` belum tentu sudah ada ketika halaman pertama kali selesai dimuat.

Dengan memasang event pada `document`, klik pada tombol hapus yang dibuat kemudian tetap dapat ditangkap.

**Penjelasan Kode**
| Kode | Fungsi |
|---|---|
| `document.addEventListener("click", ...)` | Menangkap event klik dari halaman |
| `e.target` | Mengetahui elemen yang diklik |
| `.closest(".btn-hapus")` | Mencari tombol hapus terdekat |
| `if (!btn) return` | Menghentikan fungsi jika yang diklik bukan tombol hapus |
| `btn.closest("tr")` | Mengambil baris tabel tempat tombol berada |
| `querySelector("td")` | Mengambil isi kolom pertama |
| `confirm()` | Menampilkan konfirmasi sebelum menghapus |
| `row.remove()` | Menghapus baris dari tampilan tabel |

> Catatan: proses hapus pada bagian ini masih bersifat front-end. `row.remove()` hanya menghilangkan baris dari tampilan dan belum menghapus data dari database/server.

## 4.2 Kesimpulan
Pada perubahan `app.js`, bagian utama yang diperbarui adalah fungsi `initHapusConfirm()`. Fungsi tersebut sekarang menggunakan event delegation agar tombol hapus tetap dapat bekerja pada data tabel yang dibuat secara dinamis menggunakan `fetch`.

Fungsi lain seperti hamburger menu, pencarian tabel, validasi form, dan `DOMContentLoaded` tetap digunakan untuk mendukung interaksi pada aplikasi SIMPUS-Mini.

Meskipun tombol hapus sudah dapat menghapus baris dari tampilan, proses tersebut masih berada di sisi front-end dan belum menghapus data secara permanen dari database.