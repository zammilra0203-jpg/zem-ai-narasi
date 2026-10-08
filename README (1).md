# Affiliate AI Studio

**Affiliate AI Studio** adalah aplikasi web statis untuk membantu
membuat materi TikTok affiliate dari informasi produk dan referensi yang
diberikan pengguna.

**Dibuat oleh Muzammil**

## Fitur

-   Upload beberapa foto referensi:
    -   Foto produk
    -   Foto deskripsi/informasi produk
    -   Foto model yang memakai atau memegang produk
-   Input nama produk dan deskripsi produk.
-   Banyak pilihan gaya konten dan gaya intonasi.
-   Pilihan karakter pembicara, target audiens, CTA, dan durasi.
-   Menghasilkan:
    -   Analisis produk
    -   5 hook
    -   Narasi TikTok sekitar 10 detik
    -   Master prompt video 10 detik
    -   4 scene/beat detail
    -   Arahan visual
    -   Negative prompt
    -   Catatan akurasi produk
-   Untuk intonasi cepat/energik, narasi dibuat sedikit lebih panjang
    agar tetap terasa natural ketika dibaca cepat.
-   Master prompt video menyesuaikan pilihan gaya, intonasi, audiens,
    CTA, referensi, gerakan model, ekspresi, gestur, product handling,
    kamera, lighting, transisi, continuity, dan timeline 0--10 detik.
-   Tombol salin untuk hasil narasi dan prompt.
-   Jika Gemini sedang padat atau request terkena rate limit, aplikasi
    dapat melakukan retry dan menyediakan mode cadangan lokal agar
    pengguna tetap mendapatkan draft narasi dan prompt.

## Yang tidak termasuk

Fitur **Generate Foto** dan **Generate Video langsung** sengaja tidak
digunakan dalam versi ini.

Aplikasi berfungsi sebagai **generator narasi dan prompt video**. Prompt
video dapat disalin ke generator video AI lain.

## Cara menjalankan

Aplikasi tidak membutuhkan Node.js, npm, database, atau build process.

Cukup buka:

``` text
index.html
```

## Publikasi melalui GitHub Pages

1.  Buat repository baru di GitHub.
2.  Upload `index.html` dan `README.md`.
3.  Buka **Settings → Pages**.
4.  Pada bagian source, pilih branch utama, misalnya `main`, dan folder
    `/ (root)`.
5.  Simpan pengaturan.
6.  Tunggu GitHub Pages melakukan deployment.
7.  Buka URL GitHub Pages yang diberikan GitHub.

## Gemini API Key

Aplikasi dapat menggunakan Gemini API dari browser.

Masukkan API key pada kolom **Gemini API Key**, kemudian tekan **BUAT
NARASI SEKARANG**.

### Keamanan

Versi ini adalah aplikasi client-side. API key yang dimasukkan ke
browser **bukan tempat yang aman untuk menyimpan secret produksi**.

Untuk penggunaan pribadi/prototipe, pendekatan ini dapat digunakan
dengan memahami risikonya. Untuk aplikasi publik/komersial, sebaiknya
pemanggilan Gemini dipindahkan ke backend/server yang aman agar API key
tidak terekspos kepada pengunjung.

## Ketika Gemini sedang padat

Aplikasi memiliki mekanisme retry untuk kondisi sementara seperti rate
limit atau server sedang sibuk.

Jika semua percobaan model gagal, aplikasi dapat menggunakan **Mode
Cadangan Lokal** untuk tetap membuat draft berdasarkan data yang
dimasukkan pengguna.

Mode cadangan lokal tidak dapat melihat isi foto sedalam model
multimodal. Karena itu, **nama produk dan deskripsi produk sebaiknya
diisi dengan jelas**.

## Format narasi

Target utama adalah **10 detik**.

Untuk intonasi cepat/energik, narasi dibuat sedikit lebih panjang agar
cocok dengan delivery cepat. Untuk intonasi santai, narasi dibuat lebih
ringkas agar tersedia ruang untuk jeda dan artikulasi.

## Format master prompt video

Master prompt dibuat dalam **satu paragraf** agar mudah disalin ke
generator video.

Prompt mengarahkan video untuk:

1.  Hook
2.  Product reveal
3.  Demonstration/benefit yang didukung informasi produk
4.  CTA

Timeline diarahkan tepat **0--10 detik** dan setiap adegan harus menyatu
secara visual.

Prompt juga mempertimbangkan:

-   Gerakan model
-   Ekspresi wajah
-   Gestur tangan
-   Cara memegang/memperlihatkan produk
-   Posisi produk
-   Framing
-   Camera movement
-   Lens/look
-   Lighting
-   Focus
-   Transition
-   Continuity
-   Tempo berdasarkan intonasi
-   Voice-over Bahasa Indonesia
-   CTA

## Struktur repository

``` text
Affiliate-AI-Studio/
├── index.html
└── README.md
```

## Lisensi

Belum menetapkan lisensi open-source khusus. Jika repository akan dibuka
untuk publik, tambahkan file `LICENSE` sesuai lisensi yang ingin
digunakan.

## Catatan

Gunakan klaim produk yang jujur dan sesuai informasi penjual. Jangan
membuat klaim manfaat, harga, spesifikasi, atau hasil penggunaan yang
tidak didukung oleh informasi produk.
