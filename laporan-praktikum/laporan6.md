# Modul 6 TCP
TCP (Transmission Control Protocol) merupakan protokol pada lapisan transport yang bersifat connection-oriented, yaitu proses pengiriman data harus diawali dengan pembentukan koneksi terlebih dahulu. TCP memastikan data dikirim secara andal melalui penggunaan mekanisme seperti sequence number, acknowledgment, flow control, dan congestion control.

## Analisis Transfer File Menggunakan Protocol TCP
Langkah-Langkahnya:
1. Download file http://gaia.cs.umass.edu/wireshark-labs/alice.txt

   <img width="401" height="125" alt="image" src="https://github.com/user-attachments/assets/40f0eed6-c93d-49e0-9661-3315efb267be" />

2. Buka browser http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html dan pilih file alice.txt
   <img width="1600" height="417" alt="image" src="https://github.com/user-attachments/assets/98b6d3b1-4458-4b50-b4db-213e59b185a1" />

3. Buka wireshark, kemudian pilih wif dan start
   <img width="1600" height="945" alt="image" src="https://github.com/user-attachments/assets/194bd511-8d71-4908-9cd3-b75c922b9e60" />

4. Kembali ke browser klik Upload alice.txt hingga muncul tampilan “Congratulations”
   <img width="1600" height="483" alt="image" src="https://github.com/user-attachments/assets/6fdc3d15-35b1-4370-846a-6e2571799edd" />

5. Stop wireshark kemudian filter "tcp"
    
      <img width="735" height="263" alt="image" src="https://github.com/user-attachments/assets/4a6e327d-651e-4f7e-842f-a54b5c8a9ca9" />
    
    - Paket yang muncul terdiri dari segmen TCP dan beberapa paket HTTP. Hal ini menunjukkan bahwa proses upload file dilakukan menggunakan protokol HTTP, yang berjalan di atas protokol TCP. TCP berperan memastikan data    terkirim dengan aman dan berurutan, sedangkan HTTP digunakan untuk menangani proses pertukaran data antara client dan server saat file diunggah.
    
    - Paket SYN digunakan untuk memulai koneksi TCP antara client dan server melalui proses *three-way handshake*, sehingga koneksi dapat dipastikan siap sebelum pertukaran data dilakukan. Paket ini tidak digunakan untuk mengirim file secara langsung. Setelah koneksi berhasil terbentuk, file akan dikirim dalam beberapa segmen kecil melalui TCP. Pembagian data menjadi bagian-bagian kecil ini bertujuan agar proses pengiriman lebih efisien, mudah dikontrol, serta membantu memastikan seluruh data dapat diterima dengan benar oleh tujuan.
    
      <img width="971" height="549" alt="image" src="https://github.com/user-attachments/assets/0c7fe65e-a25e-47aa-8ed9-8cecd7ead1df" />
    
    - Setelah proses upload selesai, server akan mengirimkan respons HTTP/1.1 200 OK. Pesan ini menandakan bahwa file telah berhasil diterima dan diproses oleh server tanpa kendala. Setelah itu, halaman web menampilkan pesan “Congratulations” sebagai tanda bahwa proses upload file berhasil dilakukan dengan sukses.

### Menjawab Pertanyaan
1) IP dan port TCP komputer klien mencari data di filter "HTTP" dan pilih paket POST
    - IP Server: 128.119.245.12
    
      <img width="1600" height="946" alt="image" src="https://github.com/user-attachments/assets/842f32dd-c86f-4835-93e0-2b59911b4282" />
    - Port server : 54470
   
      <img width="951" height="432" alt="image" src="https://github.com/user-attachments/assets/cf4e4116-cf77-4806-b812-0f4587df6d38" />

2) IP dan port TCP server mencari data di filter "HTTP" dan pilih paket HTTP/1.1 200 OK

      <img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/98fc4572-53f9-4c85-985c-f86591263c94" />
    - IP Server: 192.168.100.132
    
    - Port server : 80

#  Dasar TCP
## Berikut Langkah-Langkahnya:
1. Download dan extrak file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
   <img width="383" height="128" alt="image" src="https://github.com/user-attachments/assets/edc5b685-39fa-450d-929a-5a17f7f360aa" />

2. Buka file dan pilih paket paket tcp-ethereal-trace-1, buka dengan wireshark
   <img width="1600" height="668" alt="image" src="https://github.com/user-attachments/assets/f9557eee-3ac5-4ace-8362-969db500c4b3" />

### Menjawab Pertanyaan
1) Nomor urut SYN, mencari data di filter tcp.flags.syn == 1 && tcp.flags.ack == 0
    
      <img width="1005" height="351" alt="image" src="https://github.com/user-attachments/assets/227bd7d0-a2f0-4874-b8de-7733287f4a59" />
      
    - Nomor urut pada segmen TCP SYN adalah 0. Segmen ini teridentifikasi sebagai SYN karena memiliki flag SYN pada bagian TCP Flags.

      <img width="965" height="785" alt="image" src="https://github.com/user-attachments/assets/867333f4-01ed-46bd-8510-adbbe46d4199" />
      
2) SYN-ACK, mencari data di filter tcp.flags.syn == 1 && tcp.flags.ack == 1

      <img width="912" height="211" alt="image" src="https://github.com/user-attachments/assets/4903744d-c784-499f-8190-04d928fe0da4" />

    - Nomor urut (sequence number) pada segmen SYN-ACK adalah 0, sedangkan nilai acknowledgment adalah 1. Nilai acknowledgment diperoleh dari sequence number pada segmen SYN sebelumnya yang ditambah 1. Segmen ini dapat diidentifikasi sebagai SYN-ACK karena memiliki flag SYN dan ACK pada bagian TCP Flags

      <img width="965" height="865" alt="image" src="https://github.com/user-attachments/assets/03d8559c-950f-45b4-a826-d5984ad30526" />

3) Sequence number POST, mencari data di filter tcp.port == 1161 && tcp contains "POST"

      <img width="1462" height="218" alt="image" src="https://github.com/user-attachments/assets/9358bd0a-3448-4626-8d3f-39a9404f52c1" />
      
    - Nomor urut segmen TCP yang berisi perintah HTTP POST adalah 1

      <img width="962" height="905" alt="image" src="https://github.com/user-attachments/assets/5d18a0e9-f6f9-4e4c-b289-b5f8c9e88f5d" />

4) 6 segmen pertama + RTT

      <img width="1265" height="915" alt="image" src="https://github.com/user-attachments/assets/ac36e648-62e0-49d7-9490-50ce56c47d93" />

    - Nilai RTT (*Round Trip Time*) diperoleh dari selisih waktu antara saat segmen TCP dikirim dan saat acknowledgment (ACK) diterima kembali. Berdasarkan grafik *Round Trip Time*, nilai RTT berada pada kisaran sekitar 100 ms hingga 300 ms. Perbedaan nilai RTT ini menunjukkan bahwa kondisi jaringan selama proses transfer tidak selalu stabil, sehingga waktu yang dibutuhkan paket untuk pergi dan kembali dapat berubah-ubah.

5) Panjang 6 segmen
   
      <img width="972" height="587" alt="image" src="https://github.com/user-attachments/assets/8c6d28bd-d0b3-4619-aa6d-5290d05473d0" />

    - Panjang 6 segmen adalah 7865 byte

6) Buffer receiver
    
      <img width="961" height="701" alt="image" src="https://github.com/user-attachments/assets/7fa55a26-efb6-49d1-aab8-4137b6415f48" />

    - Nilai minimum ruang buffer yang tersedia pada penerima adalah 17520 byte, yang terlihat dari nilai window size pada segmen TCP
  
7) Retransmission

      <img width="1600" height="945" alt="image" src="https://github.com/user-attachments/assets/91a56dd8-e8de-45de-82f6-466e822a8d10" />

    - Tidak ditemukan retransmission / ditemukan retransmission. Hal ini dapat dilihat dari tidak adanya / adanya label “TCP Retransmission” pada Wireshark.

8) ACK behavior

      <img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/3592855b-7812-4b6f-a0db-022f8fadc2da" />

    - Jumlah data yang di-ACK tidak tetap dan bisa banyak. Penerima dapat mengakui beberapa segmen sekaligus, tidak selalu satu per satu
  
9) Thoroughtput

      <img width="1266" height="922" alt="image" src="https://github.com/user-attachments/assets/5130280b-f9b2-407a-8bb2-fbfecd65b05e" />

    - Throughput merupakan jumlah data yang berhasil ditransfer dalam setiap satuan waktu. Berdasarkan grafik throughput, kecepatan transfer data meningkat secara bertahap hingga mencapai sekitar 200 kbps sampai 270 kbps. Hal ini menunjukkan bahwa performa koneksi TCP selama proses pengiriman data berjalan cukup baik dan mampu menjaga laju transfer data secara stabil.

# Congestion Control pada TCP
## Berikut Langkah-Langkahnya dan Menjawab Pertanyaan:
1. Identifikasi Slow Start & Congestion Avoidance (file tcp-ethereal-trace-1)

    - Buka file tcp-ethereal-trace-1 dengan wireshark
    - Filter "TCP"
    - Klik Statistics -> TCP Stream Graph -> Time-Sequence Graph (Stevens)
      <img width="1267" height="916" alt="image" src="https://github.com/user-attachments/assets/629367a9-c8c1-4829-936b-f90861e8f86d" />
    - Fase *slow start* terjadi pada awal koneksi (sekitar 0 hingga ±1 detik) dengan pertumbuhan data secara eksponensial hingga mencapai *threshold*, lalu berubah menjadi fase *congestion avoidance* dengan pertumbuhan linear. Data nyata menunjukkan sedikit perbedaan dari teori karena dipengaruhi kondisi jaringan seperti delay dan variasi ACK. Secara keseluruhan, koneksi TCP pada grafik terlihat cukup stabil karena tidak ada penurunan drastis yang menunjukkan *packet loss* besar atau *timeout*, meskipun grafik tidak sepenuhnya mulus seperti model TCP ideal.



