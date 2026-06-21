# Rencana Perombakan Responsivitas & Keterbacaan (Responsive Redesign Plan)

Rencana ini disusun untuk memastikan presentasi Pitch Deck HTML memiliki keterbacaan penuh (100% readability) dan kenyamanan navigasi ketika ditampilkan di layar proyektor (saat presentasi) maupun ketika dibaca di layar Handphone (HP) dan Tablet oleh juri.

## 1. Strategi Tipografi & Skala Visual (Untuk Proyektor & HP)
*   **Masalah saat ini:** Ukuran teks statis terkadang terlalu kecil jika diproyeksikan ke dinding proyektor, namun terlalu besar dan memicu pemotongan kata jika dibaca di HP.
*   **Rencana Perbaikan:**
    *   Menggunakan ukuran font dinamis berbasis variabel CSS dan media queries.
    *   Untuk proyektor/layar lebar (lebar layar >= 1200px), ukuran teks deskripsi akan dinaikkan agar panelis di baris belakang tetap bisa membaca dengan jelas tanpa memicingkan mata.
    *   Kontras warna latar belakang terang (off-white) dengan teks gelap (charcoal) akan dioptimalkan untuk menjaga keterbacaan di bawah cahaya lampu ruangan presentasi.

## 2. Restrukturisasi Navigasi Multi-Halaman di Berbagai Layar
*   **Masalah saat ini:** Sidebar kiri memakan ruang 280px. Pada tablet dan HP, sidebar ini akan menutup sebagian besar konten atau membuat tampilan menjadi sempit.
*   **Rencana Perbaikan:**
    *   **Desktop/Proyektor (>= 1024px):** Tetap menggunakan sidebar kiri statis yang elegan.
    *   **Tablet (768px - 1023px):** Sidebar kiri diringkas menjadi bar navigasi horizontal di bagian atas (top bar) untuk memperluas area konten.
    *   **Mobile Phone (< 768px):** Sidebar dihilangkan penuh. Sebagai gantinya, akan dipasang header minimalis di bagian atas dengan tombol **Hamburger Menu (☰)**.
    *   Ketika tombol Hamburger ditekan, menu navigasi akan meluncur keluar sebagai laci penuh (*slide-out menu drawer*) dengan tombol yang besar dan mudah ditekan oleh jari tangan.

## 3. Penataan Ulang Komponen Khusus (Section-by-Section)
Beberapa bagian memerlukan penyesuaian khusus agar tidak berantakan di layar kecil:

### A. Tabel Parameter & Formulasi (`teknologi.html`)
*   **Masalah:** Tabel perbandingan formulasi terpotong secara horizontal pada layar HP (lebar < 400px).
*   **Perbaikan:** Dibungkus dalam container dengan `overflow-x: auto` dan ditambahkan animasi indikator visual "Geser Kanan ➔" yang memberi petunjuk kepada pembaca bahwa tabel dapat digeser ke samping untuk melihat kelanjutan data.

### B. Neraca Massa / Mass Balance (`teknologi.html`)
*   **Masalah:** Aliran proses horizontal `Input ➔ Proses ➔ Output` terlalu panjang untuk layar vertikal HP.
*   **Perbaikan:** Menggunakan media query khusus mobile untuk mengubah alur baris menjadi bertumpuk vertikal:
    ```
    [Nama Tahap]
    ↓ Input: xxx
    ↓ Output: yyy
    ```
    Ini menjamin data angka neraca massa tetap terbaca utuh tanpa terpotong batas layar.

### C. Alur 11 Tahap Flowchart / Timeline (`teknologi.html`)
*   **Masalah:** Garis timeline vertikal dan margin terlalu lebar di layar HP sehingga menyisakan sedikit ruang untuk teks.
*   **Perbaikan:** Mempersempit margin kiri timeline dari `40px` menjadi `20px` di layar mobile, memindahkan penanda angka di atas teks, dan menyelaraskan tata letak agar teks penjelasan mendapatkan porsi lebar layar yang maksimal.

## 4. Sistem Smart Image Placeholder
Untuk mempermudah penempatan aset gambar/dokumen visual pendukung presentasi:
*   **Daftar Aset Gambar yang Disiapkan:**
    1.  `assets/hero-image.png` (Untuk cover/sampul di `index.html` - gambar inovasi utama).
    2.  `assets/raw-material.png` (Untuk visualisasi **Bahan Baku** buah pinang sirih muda di `inovasi.html`).
    3.  `assets/process-delignification.png` (Untuk visualisasi **Proses Utama: Delignifikasi/Pemasakan NaOH** di `teknologi.html` pada langkah ke-7).
    4.  `assets/process-pulping.png` (Untuk visualisasi **Proses Pengolahan Pulp: Penghalusan/Pencucian** di `teknologi.html` pada langkah ke-8).
    5.  `assets/product-sample.png` (Untuk sampel produk hilir kertas/kemasan di `manfaat.html` atau `komersialisasi.html`).
*   **Mekanisme Deteksi Otomatis (JavaScript-powered):**
    *   Kami akan membuatkan berkas PNG transparan berukuran kecil (1x1 piksel) sebagai *default placeholder*.
    *   Di setiap halaman HTML, jika browser mendeteksi gambar tersebut masih berupa *default placeholder* (lebar gambar <= 10px), HTML akan menampilkan **Kotak Penjelasan Overlay** berwarna abu-abu yang menerangkan *"Gambar apa yang harus diletakkan di sini beserta instruksi dimensinya"*.
    *   Begitu Anda mengganti (overwrite) file PNG tersebut dengan gambar asli Anda (yang ukurannya pasti lebih dari 10px), kode JavaScript akan mendeteksinya secara otomatis saat halaman dibuka dan **menyembunyikan teks penjelasan tersebut**, lalu menampilkan gambar asli Anda secara penuh.

---
**Apakah poin-poin rencana perombakan responsivitas dan sistem image placeholder ini sudah sesuai dengan ekspektasi Bapak/Ibu? Jika disetujui, saya akan segera melanjutkan ke pengodean kode CSS/HTML-nya.**
