# Affiliate AI Studio — Versi Basis Fast + Simpan Proyek

Versi ini menggunakan kembali **index-fast-saved.html** sebagai basis, tanpa mengubah desain utama dan alur Gemini yang sudah ada.

## Perubahan
- **Simpan proyek**: nama proyek, informasi produk, foto referensi, narasi, master prompt video, scene, dan output lain disimpan di IndexedDB browser.
- **Buka proyek**: pilih proyek tersimpan dan klik Buka.
- **Hapus proyek**: pilih proyek dan klik Hapus (ada konfirmasi).
- **Proyek baru**: bersihkan formulir untuk memulai proyek berikutnya. Simpan dahulu bila ingin mempertahankan pekerjaan.
- **Product Reference Lock**: instruksi menjaga bentuk, warna, logo, label, ukuran, dan kemasan produk tetap sama dari awal sampai akhir video.
- **Realistic Motion**: instruksi gerakan tangan, ekspresi, kamera, dan transisi yang sederhana serta masuk akal; mencegah adegan janggal.

## Instalasi GitHub Pages
Unggah `index.html` dan `README.md` ke root repository, kemudian aktifkan Settings → Pages → Deploy from branch → main / (root).

## Catatan penyimpanan
Data disimpan **di browser dan origin website yang sama**, bukan di GitHub atau cloud. Data tidak otomatis tersedia di perangkat lain, dan dapat hilang bila data situs/browser dibersihkan. Foto berukuran besar mungkin membuat penyimpanan gagal karena batas kuota browser. API Key tidak dimasukkan ke data proyek (pengaturan ingat API Key yang sudah ada pada aplikasi tetap terpisah). Jangan masukkan API Key ke kode GitHub.

## Catatan kualitas video
Prompt berusaha menjaga konsistensi dan gerakan natural, tetapi generator video yang dipakai tetap menentukan hasil akhir. Jika model video tidak mendukung image reference, instruksi teks saja tidak dapat menjamin identitas produk 100% sama.
