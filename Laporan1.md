# Laporan Praktikum Week 1
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________
## Instalasi Wireshark (modul 1)
Awal dari praktikum ini dimulai dengan instalasi Wireshark. Ini adalah langkah penting agar bisa melanjutkan ke tugas-tugas berikutnya. Berikut adalah prosedur yang saya lakukan:
1. Kunjungi situs web resmi Wireshark melalui browser di alamat https://www.wireshark.org/download.html.
2. Unduh installer yang sesuai dengan OS yang digunakan (seperti Windows atau Linux), pastikan memilih versi stabil terbaru.
3. Setelah unduhan selesai, klik dua kali pada file installer untuk menjalankannya.
4. Ikuti panduan instalasi step by step hingga prosesnya berakhir; tentukan folder instalasi dan tunggu sampai selesai.
Instalasi berjalan tanpa kendala, hanya butuh waktu beberapa menit hingga Wireshark siap digunakan.
### Dokumentasi Instalasi
Saya mengambil beberapa screenshot selama proses instalasi untuk dokumentasi:
- Halaman download Wireshark:
![12ebcd9a-6725-4f61-9232-f9c29a027933](https://github.com/user-attachments/assets/c393ea6b-5670-433d-9874-2ae9416ddb55)
 -Langkah awal setup:
![cb281b91-d33b-43ae-849e-19786a563e88](https://github.com/user-attachments/assets/5ac018ee-7f9a-4c03-b7e3-5a808e11f31b)

- Persetujuan lisensi:
![9d7d6b94-53b2-4685-ac3b-39622e2110da](https://github.com/user-attachments/assets/510e79fa-8555-4a6b-9e70-04b6b0102cf4)

- Pemilihan fitur yang akan diinstal:
![046f7740-bd2b-4a6b-ba18-2cc7e0fa7720](https://github.com/user-attachments/assets/48d30757-e0eb-4fff-9d0a-6aef0c51654c)

- Konfigurasi lokasi instalasi:
![5fd13c7d-d205-4e89-87dc-8d5e78f04a46](https://github.com/user-attachments/assets/f3f521d9-e2cf-48bf-adf5-b3a1f50bbb01)

- Proses instalasi sedang berjalan:
![8b60d22c-f450-46b4-b458-cd5ad429d653](https://github.com/user-attachments/assets/e37f5d2c-c540-444b-b083-94378867b3d9)
![3eb7cc8c-47a8-4c02-9884-e24f5f2b1307](https://github.com/user-attachments/assets/df413ab7-faf6-4241-81fd-84f8259724e3)

- Penambahan komponen WinPcap/Npcap:
![2ede6c5d-d481-4be1-8a7f-b3e7ed84db7a](https://github.com/user-attachments/assets/5b19e43e-ab7b-400f-b81e-5fa47cc52e60)

- Tahap akhir instalasi:
![73b8fb35-620b-4b7b-95cd-02869a8733ef](https://github.com/user-attachments/assets/95b846a0-b497-4c94-b9df-ab1f267a5746)
- Instalasi berhasil diselesaikan:
![06f0ac0d-54dc-4bb1-b4bd-be58a923ca02](https://github.com/user-attachments/assets/2a30c414-6818-4b3d-a4d5-4fffeda45ec7)
## Tugas Praktikum Week 1 (modul 2)
Dengan Wireshark sudah terinstal, saya lanjut ke bagian kedua modul 2 yang fokus pada pengamatan interaksi HTTP GET dan response.
1. Buka aplikasi Wireshark dan pilih interface jaringan aktif (dalam kasus saya, Wi-Fi). Pastikan VPN dimatikan jika sedang aktif untuk menghindari gangguan dalam penangkapan paket.
2. Buka browser dan akses URL berikut: http://gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.html. Halaman web tersebut menampilkan pesan singkat: "Congratulations! You've downloaded the first Wireshark lab file!"
3. Kembali ke Wireshark, masukkan kata "http" di kolom filter tanpa tanda kutip, kemudian tekan Enter untuk memfilter paket HTTP saja.
4. Cari entri dengan label "(text/html)" di daftar paket, lalu klik ikon panah untuk memperluas detailnya.
5. Pada bagian "Line-based text data", isi HTML yang diterima terlihat seperti ini:
6. Untuk mengakhiri, klik tombol stop capture di menu dan tutup sesi tangkapan tersebut.
Melalui aktivitas ini, saya belajar lebih dalam tentang mekanisme permintaan HTTP dari browser dan bagaimana respons ditampilkan dalam Wireshark.
### Lampiran
Screenshot-screenshot berikut diambil saat melakukan tugas praktikum:
- Antarmuka utama Wireshark setelah aplikasi diluncurkan:
![f8c2fe3e-4fca-4d8e-a204-3097071ea72e](https://github.com/user-attachments/assets/3b93599a-fac0-4811-9f91-1d7d30d79a86)
- Daftar paket yang berhasil ditangkap melalui koneksi Wi-Fi:
![5c2ed4ad-6d7d-4952-89a1-da049b6be9a4](https://github.com/user-attachments/assets/56342482-a7c9-4bc0-bdea-20ce8d97d4cf)

- Tampilan browser yang menunjukkan halaman lab sederhana:
![bd20df49-24ab-453b-bf89-d6f704f58fb8](https://github.com/user-attachments/assets/84e0bc21-32f8-42a3-bfda-d5678612916a)

- Hasil filter paket menggunakan kata kunci "http":
![883fcc18-b5f6-4b40-ae96-f0446a523e26](https://github.com/user-attachments/assets/9e6af497-89af-42c9-b588-0d8a35b33a99)

- Isi dari "Line-based text data" yang berisi respons HTML:
![10ef3187-3095-4c05-9401-eaf0c5eb509d](https://github.com/user-attachments/assets/56ea9b29-aa0d-4137-992f-41d670f5df38)


  Gambar ini menunjukkan contoh output yang wajib dicantumkan dalam laporan.
