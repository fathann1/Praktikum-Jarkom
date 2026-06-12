# Modul 13 - ARP
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________
Tujuan Praktikum
- Kita sebagai mahasiswa dapat mempelajari cara kerja protokol ARP menggunakan Wireshark.

## ARP (Address Resolution Protocol)
Apa Itu ARP? ARP (Address Resolution Protocol) merupakan protokol jaringan yang berfungsi untuk mencari dan mencocokkan alamat MAC berdasarkan alamat IP pada jaringan lokal (LAN). Protokol ini dibutuhkan karena perangkat menggunakan alamat IP untuk identifikasi logis, sedangkan proses pengiriman data pada jaringan lokal dilakukan menggunakan alamat MAC.

## Konsep ARP
ARP berperan sebagai penghubung antara alamat IP dan alamat MAC. Dengan bantuan ARP, perangkat dapat mengetahui alamat fisik dari perangkat tujuan sehingga data dapat dikirim ke lokasi yang tepat dalam jaringan lokal.

## Konsep Dasar ARP
Dalam model OSI, ARP bekerja di antara Network Layer (Layer 3) dan Data Link Layer (Layer 2). Saat sebuah perangkat ingin mengirim data ke perangkat lain dalam LAN, perangkat tersebut harus mengetahui MAC Address tujuan. Jika yang diketahui hanya alamat IP, maka ARP digunakan untuk memperoleh informasi MAC Address yang sesuai.

Agar proses pencarian tidak dilakukan berulang kali, hasil pemetaan IP dan MAC Address akan disimpan sementara pada tabel ARP Cache.

## Mekanisme Kerja ARP
1. Perangkat pengirim menentukan alamat IP tujuan yang akan dihubungi.
2. Sistem memeriksa ARP Cache untuk mencari apakah MAC Address tujuan sudah tersimpan.
3. Jika informasi belum tersedia, perangkat mengirim paket ARP Request ke seluruh perangkat dalam jaringan (broadcast).
4. Perangkat yang memiliki alamat IP sesuai akan merespons dengan mengirim ARP Reply.
5. ARP Reply berisi MAC Address milik perangkat tujuan.
6. Pengirim menyimpan pasangan IP dan MAC Address tersebut ke dalam ARP Cache.
7. Setelah alamat MAC diketahui, data dapat dikirim langsung ke perangkat tujuan.

## Jenis Pesan pada ARP

- ARP Request

  ARP Request merupakan pesan permintaan yang digunakan untuk mencari MAC Address dari suatu alamat IP. Pesan ini dikirim secara broadcast sehingga dapat diterima oleh semua perangkat dalam jaringan lokal.

- ARP Reply

  ARP Reply adalah pesan balasan dari perangkat yang alamat IP-nya sesuai dengan permintaan. Balasan ini berisi informasi MAC Address dan dikirim langsung kepada perangkat yang meminta.

- ARP Cache

  ARP Cache adalah tempat penyimpanan sementara yang berisi daftar pasangan alamat IP dan MAC Address yang telah diketahui sebelumnya. Keberadaan ARP Cache membantu mengurangi jumlah ARP Request sehingga komunikasi menjadi lebih cepat dan  efisien.
