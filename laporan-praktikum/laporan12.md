# Modul 11 - ICMP
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________
Tujuan Praktikum
- Kita sebagai mahasiswa dapat mempelajari cara kerja protokol ICMP menggunakan Wireshark.

## ICMP
ICMP (Internet Control Message Protocol) digunakan untuk membantu proses komunikasi dan pemantauan jaringan. Fungsi utamanya adalah:
1. Mendiagnosis jaringan untuk mengetahui apakah koneksi berjalan dengan baik.
2. Memeriksa kondisi jaringan dan memastikan host tujuan dapat dijangkau.
3. Memberikan laporan kesalahan (error reporting) jika terjadi masalah dalam pengiriman paket.
4. Membantu proses troubleshooting saat terjadi gangguan jaringan.

## ICMP Digunakan Untuk
1. Mengecek host dalam jaringan menggunakan perintah ping untuk mengetahui apakah perangkat tujuan aktif dan dapat dihubungi.
2. Mengetahui jalur paket data menggunakan traceroute/tracert, sehingga dapat diketahui router (hop) yang dilewati paket.
3. Memberikan informasi error, misalnya saat tujuan tidak dapat dijangkau (Destination Unreachable).
4. Memberikan informasi TTL habis, yaitu pesan Time Exceeded ketika paket melewati batas hop yang diizinkan.

## Hubungan IP dengan ICMP
ICMP bekerja bersama protokol IP. Saat paket IP dikirim melalui jaringan, ICMP digunakan untuk membawa pesan kontrol dan informasi kesalahan yang berkaitan dengan proses pengiriman tersebut. Dengan kata lain, ICMP tidak digunakan untuk mengirim data pengguna, melainkan untuk membantu IP dalam memantau dan mengelola komunikasi jaringan.

## Isi Paket ICMP

Paket ICMP terdiri dari beberapa bagian penting, yaitu:

1. Type
   Menunjukkan jenis pesan ICMP yang dikirim, misalnya Echo Request, Echo Reply, atau Destination Unreachable.
2. Code
   Memberikan informasi lebih rinci mengenai jenis pesan ICMP.
3. Checksum
   Digunakan untuk memeriksa integritas data dan mendeteksi kesalahan pada paket.
4. Identifier
   Berfungsi sebagai penanda untuk membedakan paket ICMP yang satu dengan yang lainnya.
5. Sequence Number
   Menunjukkan nomor urut paket yang dikirim sehingga paket dapat dicocokkan dengan respons yang diterima.
6. Data/Payload
   Berisi data tambahan yang dikirim bersama pesan ICMP, misalnya data yang digunakan pada proses ping.

Dengan komponen-komponen tersebut, ICMP dapat membantu administrator jaringan dalam memantau konektivitas, mendeteksi kesalahan, dan menganalisis kinerja jaringan.
