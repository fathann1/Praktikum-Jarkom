# Modul 4 DNS

DNS (Domain Name System) adalah sistem yang mengubah nama domain (seperti google.com) menjadi alamat IP. DNS bekerja dengan mengirim permintaan ke server DNS lokal, lalu menerima hasilnya.

Sebenarnya, proses yang lebih rumit terjadi di sisi server. Server DNS yang tersusun secara hierarki akan saling berkomunikasi untuk mencari jawaban, baik secara rekursif maupun iteratif, tanpa terlihat oleh pengguna.

## 4.2 Nslookup
Nslookup adalah perintah yang digunakan untuk melakukan query ke server DNS guna mendapatkan informasi tentang domain atau host, seperti alamat IP, nama domain, dan record DNS lainnya. Perintah ini bekerja dengan mengirim permintaan ke server DNS tertentu, lalu menampilkan hasil responsnya kepada pengguna.

### Contoh Penggunaannya:
1) Perintah nslookup [www.mit.edu](http://www.mit.edu) digunakan untuk mengecek apakah domain tersebut terdaftar dan memiliki alamat IP. Perintah ini mengirim permintaan ke server DNS lalu menampilkan hasilnya. Jika hasilnya domain tidak ditemukan, berarti domain tersebut tidak terdaftar di sistem DNS.
<p align="center">
  <img src="https://github.com/user-attachments/assets/35096e0b-67d0-4b09-8e81-fb71a95dd0fe" width="600"/>
</p>

2) Perintah nslookup -type=NS mit.edu digunakan untuk mengetahui Name Server (NS) yang menangani domain mit.edu. Perintah ini mengirim permintaan ke server DNS untuk melihat server mana saja yang mengelola domain tersebut.
![3ec2a305-25a8-4099-a65e-b472469d8ccb](https://github.com/user-attachments/assets/1a221639-5f7d-4b0d-9355-836cc6adc873)

3) tulis nslookup [www.aiit.or.kr](http://www.aiit.or.kr) bitsy.mit.edu digunakan untuk mencari informasi DNS dari domain [www.aiit.or.kr](http://www.aiit.or.kr) dengan menggunakan server DNS tertentu, yaitu bitsy.mit.edu.
![49567cd9-1419-4ddf-9615-db529bea7615](https://github.com/user-attachments/assets/5e51c37c-2915-479d-bc91-357b97e65580)

## 4.3 Ipconfig
Ipconfig digunakan untuk mengelola informasi DNS yang tersimpan di komputer (host). Komputer dapat menyimpan hasil DNS yang baru saja didapat. Untuk melihat data yang tersimpan, setelah prompt C:> masukkan perintah berikut:

1) Tulis "ipconfig /all" digunakan untuk menampilkan informasi lengkap konfigurasi jaringan pada komputer, seperti nama host, status jaringan, alamat IP, subnet mask, gateway, DNS server, dan informasi lain dari adaptor jaringan.
![82105b20-e900-44f1-8db8-5b3f23528501](https://github.com/user-attachments/assets/75fbb0f0-f9d0-4a70-a02d-2019f51d58bd)

2) Tulis "ipconfig /all > networkinfo.txt" digunakan untuk menampilkan semua informasi konfigurasi jaringan lalu menyimpannya ke file networkinfo.txt, sehingga bisa dibaca atau dianalisis tanpa harus melihat di Command Prompt.
![96d18130-f67f-4d43-af75-50d8e2157673](https://github.com/user-attachments/assets/704a370a-22c9-4111-b996-21908299e008)

3) habis itu tulis "ipconfig /displaydns" Fungsinya untuk menampilkan dns
![209cffc3-2927-4df1-b5cf-7fc76b98a4e7](https://github.com/user-attachments/assets/d31c3dc3-c0be-4ac2-b07c-c06ac3053a0b)

4) selanjutnya tulis "ipconfig /flushdns" digunakan untuk menghapus cache DNS di komputer. Dengan menghapus cache ini, sistem akan mengambil ulang data DNS terbaru dari server, dan biasanya dipakai untuk mengatasi masalah koneksi atau error DNS.
![8e95b9dc-1dd8-4644-bc35-24adac154571](https://github.com/user-attachments/assets/039db82e-a2ad-4ba3-9cd4-9106fac8c1e8)

# 4.4 Tracing DNS dengan Wireshark
Mempelajari cara memantau dan menganalisis paket data DNS yang dikirim dan diterima oleh komputer, sehingga kita bisa melihat bagaimana permintaan domain dikirim ke server dan bagaimana responsnya diterima. Hal ini berguna untuk memahami cara kerja DNS dan membantu dalam troubleshooting jaringan.

## A. Analisis DNS Request dan Response pada Akses Website (www.ietf.org)
Berikut langkah-langkah untuk tracing DNS dengan Wireshark:

1) Buka command prompt (CMD) dan ketikan ipconfig untuk menyalin IP Address "192.168.1.104"
![cb78eb20-ad87-4ef1-b17e-f3383995bfb4](https://github.com/user-attachments/assets/113fc00d-47c0-4795-895c-2090fc485bb9)

2) Buka aplikasi wireshark kemudian pilih jaringan wifi, karena kita menggunakan wifi. Setelah itu filter IP Address "
![87058418-1c40-4c41-b67a-4f1f6060a36e](https://github.com/user-attachments/assets/f49928a9-3ce0-468e-88a2-b82f21a50284)

3) Buka browser http://www.ietf.org/
![5662412e-df6d-4397-ad74-8ab15b5f9495](https://github.com/user-attachments/assets/dd1aa45f-db67-45cf-953d-cd4edb13b610)

4) Tambahkan filter lagi ip.addr == 192.168.1.104 && dns.qry.name contains "ietf"
![14ca8ff6-2317-4ab4-8bff-0401d7af7fb2](https://github.com/user-attachments/assets/9885f7c1-a88c-4a78-b513-6f042969a47a)

## Pertanyaan
1. Apakah DNS menggunakan UDP atau TCP?
![71487c76-a598-47b7-9853-7cdba3ec646b](https://github.com/user-attachments/assets/e7ac18f6-dfad-403b-92f6-3ac6f37d061e)

Dari percobaan yang di lakukan terilhat bahwa DNS menggunakan TCP

2. Port tujuan pada DNS request & port sumber pada DNS response
![71487c76-a598-47b7-9853-7cdba3ec646b](https://github.com/user-attachments/assets/e7ac18f6-dfad-403b-92f6-3ac6f37d061e)

Source Port → 53 (dari server DNS)

Destination Port → 63199 (kembali ke client)

## B. Analisis DNS Menggunakan Perintah nslookup (www.mit.edu)
Berikut langkah-langkah untuk tracing DNS dengan Wireshark:

1) Buka command prompt (CMD) dan ketikan nslookup www.mit.edu
![91b3eb7d-ece3-4194-b766-ad7aa5e08633](https://github.com/user-attachments/assets/163d9ba4-bca2-4f80-aaca-1bb9645d5647)

2) Buka aplikasi wireshark kemudian pilih jaringan wifi, karena kita menggunakan wifi. Setelah itu filter DNS, lalu ambil data dari Standard query (request) dan Standard query response dari www.mit.edu
![2d0c3659-591f-4806-b8b4-ef7e30d8b502](https://github.com/user-attachments/assets/999e6bbe-def1-4f9a-b4e7-756c7fd25cdb)

