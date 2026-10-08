# Affiliate AI Studio

Aplikasi web TikTok Affiliate **Affiliate AI Studio**, dibuat oleh Muzammil.

Versi ini menggunakan GitHub Pages sebagai frontend dan Google Apps Script + Google Sheets sebagai backend lisensi.

## Kebijakan lisensi

- **1 kode = 1 perangkat/browser**.
- Pelanggan memasukkan kode **satu kali** pada perangkat tersebut.
- Kunjungan berikutnya tidak meminta kode lagi selama sesi lisensi masih tersimpan dan lisensi tetap aktif.
- Masa akses: **selamanya**, kecuali lisensi dicabut.
- Setiap pelanggan memakai **Gemini API Key miliknya sendiri**.
- Gemini API Key tidak disimpan di Google Sheets.
- Fitur Generate Foto dan Generate Video langsung tidak digunakan; aplikasi fokus pada narasi dan prompt video.

## Struktur proyek

```text
Affiliate-AI-Studio/
├── index.html
├── License.gs
└── README.md
```

## Bagian 1 — Buat Google Sheet

1. Buat Google Sheet baru, misalnya `Affiliate AI Studio Licenses`.
2. Salin ID spreadsheet dari URL:

```text
https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit
```

3. Jangan membagikan spreadsheet ini kepada pelanggan.

## Bagian 2 — Buat Google Apps Script

Buka:

urlGoogle Apps Scripthttps://script.google.com/create

Buat project baru.

Salin seluruh isi `License.gs` ke project Apps Script.

Pada bagian konfigurasi:

```js
const CONFIG = {
  SPREADSHEET_ID: 'PASTE_YOUR_GOOGLE_SHEET_ID_HERE',
  SHEET_NAME: 'Licenses',
  APP_NAME: 'Affiliate AI Studio'
};
```

Ganti `PASTE_YOUR_GOOGLE_SHEET_ID_HERE` dengan ID Google Sheet milikmu.

Apps Script web app menggunakan `doGet()` untuk menerima request dan dapat dideploy sebagai web app. Untuk penggunaan publik, Google menyarankan deployment versi untuk rilis, bukan head deployment. citeturn0search3

## Bagian 3 — Siapkan database kode

Di Apps Script, jalankan fungsi:

```js
setupSheet()
```

Setujui permission Google saat pertama kali diminta.

Kemudian buat kode, misalnya:

```js
generateCodes(20)
```

Fungsi tersebut otomatis menambahkan 20 lisensi `UNUSED` ke sheet dan menampilkan pasangan kode/hash di log eksekusi.

Contoh kode pelanggan:

```text
AAS-K7M2-P9Q4-R8TX
```

**Kode mentah diberikan kepada pembeli.** Sheet lisensi publik hanya menyimpan hash kode pada kolom A.

Kolom database:

| Kolom | Isi |
|---|---|
| A | Code Hash |
| B | Status (`UNUSED`, `ACTIVE`, `REVOKED`) |
| C | Activated At |
| D | Device ID |
| E | Customer |
| F | Notes |

Kamu dapat mengisi kolom `Customer` dan `Notes` secara manual setelah menjual kode.

## Bagian 4 — Deploy backend

Di Apps Script:

**Deploy → New deployment → Web app**

Gunakan pengaturan web app yang memungkinkan pelanggan mengakses endpoint tanpa diberi akses edit ke spreadsheet. Script harus berjalan sebagai pemilik/deployer agar spreadsheet tetap privat.

Setelah deploy, salin URL Web App yang berakhiran:

```text
/exec
```

Gunakan deployment versi untuk rilis publik. Deployment versi membuat snapshot kode yang stabil; ketika backend diperbarui, buat versi baru dan update deployment yang sama. citeturn0search3

## Bagian 5 — Hubungkan GitHub Pages

Buka `index.html` dan cari:

```js
const LICENSE_API_URL = "PASTE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

Ganti dengan URL Apps Script, contoh:

```js
const LICENSE_API_URL = "https://script.google.com/macros/s/XXXXXXXXXXXX/exec";
```

**Jangan memasukkan URL spreadsheet atau API key Gemini ke kode frontend.**

Upload `index.html` ke repository GitHub Pages.

## Bagian 6 — Cara kerja pelanggan

### Aktivasi pertama

1. Pelanggan membuka URL GitHub Pages.
2. Muncul layar **AKTIFKAN LISENSI**.
3. Pelanggan memasukkan kode yang kamu berikan.
4. Browser membuat `Device ID` acak.
5. Kode diubah menjadi SHA-256 di browser.
6. Hash + Device ID dikirim ke Apps Script.
7. Apps Script mencari hash di Google Sheet.
8. Jika status `UNUSED`, kode diubah menjadi `ACTIVE` dan Device ID disimpan.
9. Sesi lisensi disimpan di browser.
10. Aplikasi terbuka.

### Kunjungan berikutnya

Browser membaca sesi lisensi dan melakukan validasi tanpa meminta pelanggan mengetik kode lagi.

Jika lisensi valid pada Device ID tersebut, aplikasi langsung terbuka.

## Bagian 7 — Satu perangkat/browser

Kode yang sudah `ACTIVE` akan ditolak jika digunakan dengan Device ID lain.

Artinya:

```text
Kode AAS-XXXX
      │
      └── HP/browser pertama → AKTIF

Kode AAS-XXXX
      │
      └── HP/browser kedua  → DITOLAK
```

Jika pelanggan menghapus data situs/browser, sesi lisensi lokal dapat hilang. Karena lisensi tetap terikat pada Device ID lama, pelanggan tidak otomatis bisa memindahkan lisensi.

Untuk memindahkan lisensi secara manual, kamu dapat menghapus Device ID lama dan mengatur status sesuai prosedur penjualanmu.

## Bagian 8 — Mencabut lisensi

Jika kamu ingin mencabut akses pelanggan, ubah:

```text
Status = REVOKED
```

Pada validasi berikutnya, aplikasi akan menolak akses.

## Bagian 9 — Gemini API Key pelanggan

Setiap pelanggan memakai API Key Gemini sendiri.

Pelanggan tidak perlu memiliki akses ke GitHub atau Google Sheet.

Mereka hanya perlu:

1. Membuka aplikasi.
2. Mengaktifkan kode lisensi.
3. Memasukkan API Key Gemini mereka.
4. Menggunakan aplikasi.

Jika fitur **Ingat API Key di perangkat ini** digunakan, API key disimpan di browser pelanggan.

## Bagian 10 — Keamanan dan batasan

Sistem ini jauh lebih baik daripada menyimpan daftar kode langsung di JavaScript, karena daftar lisensi tetap berada di Google Sheet dan verifikasi dilakukan melalui backend.

Namun GitHub Pages tetap merupakan frontend statis. Pengguna teknis dapat melihat atau memodifikasi JavaScript di browser. Karena itu, sistem ini adalah **sistem lisensi aplikasi**, bukan DRM yang tidak mungkin dilewati.

Untuk perlindungan komersial yang sangat kuat, proses penting seperti pemanggilan Gemini perlu dipindahkan ke backend sehingga server benar-benar dapat menegakkan lisensi.

Google Apps Script juga memiliki kuota dan batas penggunaan yang dapat berubah. Pantau halaman Executions dan quota jika jumlah pelanggan meningkat. citeturn0search10

## Bagian 11 — Update aplikasi

Jika hanya mengubah fitur frontend:

1. Edit `index.html`.
2. Commit ke GitHub.
3. GitHub Pages melakukan deployment.

Jika mengubah backend lisensi:

1. Edit `License.gs`.
2. Simpan.
3. Buat versioned deployment baru/update deployment.
4. Pastikan URL `/exec` yang digunakan frontend tetap menunjuk deployment yang benar.

Google mendokumentasikan bahwa deployment versi dapat diarahkan ke versi kode baru tanpa membuat URL deployment baru. citeturn0search3

## Catatan produksi

Jangan:

- Menaruh Gemini API Key milikmu di `index.html`.
- Menaruh daftar kode mentah pelanggan di repository GitHub.
- Membagikan Google Sheet lisensi kepada pelanggan.
- Menggunakan satu API Key Gemini milikmu untuk semua pelanggan jika kebijakannya adalah setiap pelanggan memakai API Key sendiri.
