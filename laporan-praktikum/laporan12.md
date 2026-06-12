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

## Analisis ICMP yang Dihasilkan Oleh Ping
1. Pertama kitabuka wireshark dan pilih jaringan Wifi
2. Buka CMD, kemudian ketikan perintah ping -n 10 www.ust.hk

<img width="982" height="628" alt="image" src="https://github.com/user-attachments/assets/d0c3902f-61cc-4b65-90c4-80dbc032ef4b" />

3. Stop capture pada wireshark
4. Isi filter ICMP
5. Pilih dan expand satu paket ICMP Echo Request
6. Pilih dan expand satu paket ICMP Echo Reply

## Kita Cek
- Pesan ICMP yang dihasilkan program Ping
  <img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/83809a3c-1e5e-4f7e-8a0f-67f0200c821f" />

  <img width="1918" height="1133" alt="image" src="https://github.com/user-attachments/assets/fd1451a1-cb1e-4415-a5c6-fa2b445dae37" />
  
  Hasil capture Wireshark menunjukkan adanya dua tipe pesan ICMP yang dihasilkan oleh program ping, yakni Echo Request dan Echo Reply. Berdasarkan data yang tertangkap, ping dilakukan sebanyak 10 kali yang dapat diidentifikasi dari nilai sequence number yang tercatat mulai dari seq=1/256 hingga seq=10/2560. Setiap satu kali proses ping akan menghasilkan satu paket request dan satu paket reply, sehingga total keseluruhan paket ICMP yang tertangkap berjumlah 20 paket. Di luar paket ping tersebut, terdapat satu paket bertipe Destination Unreachable yang berasal dari host 35.211.225.161, yang mengindikasikan bahwa port pada tujuan tidak dapat dijangkau.

- Format Isi Pesan ICMP
  1. ICMP Echo Request
     
     <img width="1417" height="840" alt="image" src="https://github.com/user-attachments/assets/92234d76-3c88-4f75-87a2-31964d36737f" />

       (expand packet 413 — Frame 413, 74 bytes, src: 192.168.68.155 → dst: 143.89.209.9)

      - Type = 8 → menandakan paket adalah Echo Request atau permintaan ping
      - Code = 0 → menunjukkan tidak ada detail error tambahan pada pesan ICMP tersebut
      - Checksum = 0x4d5a [correct] → checksum valid sehingga paket tidak mengalami kerusakan/error saat dikirim
      - Identifier = 1 (0x0001) → digunakan sebagai penanda agar Echo Reply dapat dikenali sebagai balasan dari request yang sama
      - Sequence Number = 1 (0x0001) → menunjukkan bahwa paket ini merupakan urutan ping ke-1 yang dikirim
  2. ICMP Echo Reply
     
     <img width="1417" height="840" alt="image" src="https://github.com/user-attachments/assets/827ee022-45a5-40bb-94df-9b406f563709" />

       (expand packet 414 — Frame 414, 78 bytes, src: 143.89.209.9 → dst: 192.168.68.155)

      - Type = 0 → menunjukkan bahwa paket merupakan Echo Reply atau balasan ping
      - Code = 0 → tidak terdapat informasi tambahan atau error pada paket balasan
      - Checksum = 0x555a [correct] → checksum valid sehingga paket reply diterima tanpa kerusakan data
      - Identifier = 1 (0x0001) → identifier sama dengan paket request agar sistem dapat mencocokkan balasan dengan permintaan sebelumnya
      - Sequence Number = 1 (0x0001) → menunjukkan bahwa paket reply ini merupakan balasan untuk paket request urutan ke-1
      - Response time = 74,827 ms → waktu yang dibutuhkan dari request dikirim hingga reply diterima
