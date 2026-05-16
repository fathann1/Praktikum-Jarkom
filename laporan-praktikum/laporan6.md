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
    - Paket yang muncul terdiri dari segmen TCP dan beberapa paket HTTP. Hal ini menunjukkan bahwa proses upload file dilakukan menggunakan protokol HTTP, yang berjalan di atas protokol TCP. TCP berperan memastikan data terkirim dengan aman dan berurutan, sedangkan HTTP digunakan untuk menangani proses pertukaran data antara client dan server saat file diunggah.
    - Paket SYN digunakan untuk memulai koneksi TCP antara client dan server melalui proses *three-way handshake*, sehingga koneksi dapat dipastikan siap sebelum pertukaran data dilakukan. Paket ini tidak digunakan untuk mengirim file secara langsung. Setelah koneksi berhasil terbentuk, file akan dikirim dalam beberapa segmen kecil melalui TCP. Pembagian data menjadi bagian-bagian kecil ini bertujuan agar proses pengiriman lebih efisien, mudah dikontrol, serta membantu memastikan seluruh data dapat diterima dengan benar oleh tujuan.
    
    <img width="971" height="549" alt="image" src="https://github.com/user-attachments/assets/0c7fe65e-a25e-47aa-8ed9-8cecd7ead1df" />
    - Setelah proses upload selesai, server akan mengirimkan respons HTTP/1.1 200 OK. Pesan ini menandakan bahwa file telah berhasil diterima dan diproses oleh server tanpa kendala. Setelah itu, halaman web menampilkan pesan “Congratulations” sebagai tanda bahwa proses upload file berhasil dilakukan dengan sukses.

