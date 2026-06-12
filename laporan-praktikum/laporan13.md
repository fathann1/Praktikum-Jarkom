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

## Analisis ARP pada Wireshark
1. Buka Command Prompt (CMD) sebagai Administrator, lalu jalankan perintah arp -d * untuk menghapus seluruh isi ARP Cache. Setelah itu, komputer akan melakukan proses ARP kembali saat berkomunikasi dengan perangkat lain di jaringan.

  <img width="1088" height="642" alt="image" src="https://github.com/user-attachments/assets/e14db040-fb3c-44b2-981b-1b14118cbad8" />

2. Buka **Wireshark**, kemudian pilih menu **Analyze → Enabled Protocols → IPv4** untuk mengaktifkan atau memeriksa protokol IPv4 yang akan dianalisis.

   <img width="1230" height="777" alt="image" src="https://github.com/user-attachments/assets/cfea1cdb-fded-46c6-930f-23bada4bfbc7" />

3. Start capture Wireshark
4. Membuka browser dan ketik http://gaia.cs.umass.edu/wireshark-labs/HTTP-ethereal-lab-file3.html
5. Stop capture Wireshark
6. Ketik filter: arp

   <img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/73140040-9f63-4de0-aaba-53508128aa07" />

7. Pilih salah satu paket untuk diCek

   <img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/997f0c02-68f2-4546-b3fd-085c66ca7f64" />

**Kita Cek Paket**
Berdasarkan hasil capture Wireshark, paket yang dipilih adalah ARP Request (Opcode = request/1). Perangkat dengan IP 192.168.68.1 dan MAC address 3c:6a:d2:c6:a6:cc (TPLink_c6:a6:cc) mengirimkan permintaan untuk mencari MAC address milik IP 192.168.68.136. Karena MAC address tujuan belum diketahui, Target MAC address bernilai ff:ff:ff:ff:ff:ff dan paket dikirim ke alamat Broadcast (ff:ff:ff:ff:ff:ff) agar diterima seluruh perangkat di jaringan lokal. Paket ini pada dasarnya menanyakan: "Siapa yang memiliki IP 192.168.68.136?" Dari hasil tersebut dapat disimpulkan bahwa ARP digunakan untuk menerjemahkan alamat IP menjadi alamat MAC sebelum perangkat dapat mengirim frame Ethernet ke tujuan yang benar di jaringan lokal.
