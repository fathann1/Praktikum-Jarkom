# Modul 4 DNS

DNS (Domain Name System) adalah sistem yang mengubah nama domain (seperti google.com) menjadi alamat IP. DNS bekerja dengan mengirim permintaan ke server DNS lokal, lalu menerima hasilnya.

Sebenarnya, proses yang lebih rumit terjadi di sisi server. Server DNS yang tersusun secara hierarki akan saling berkomunikasi untuk mencari jawaban, baik secara rekursif maupun iteratif, tanpa terlihat oleh pengguna.

## 1. Nslookup
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

## 2. Ipconfig
Ipconfig digunakan untuk mengelola informasi DNS yang tersimpan di komputer (host). Komputer dapat menyimpan hasil DNS yang baru saja didapat. Untuk melihat data yang tersimpan, setelah prompt C:> masukkan perintah berikut:

1) Tulis "ipconfig /all" digunakan untuk menampilkan informasi lengkap konfigurasi jaringan pada komputer, seperti nama host, status jaringan, alamat IP, subnet mask, gateway, DNS server, dan informasi lain dari adaptor jaringan.
![82105b20-e900-44f1-8db8-5b3f23528501](https://github.com/user-attachments/assets/75fbb0f0-f9d0-4a70-a02d-2019f51d58bd)

2) Tulis "ipconfig /all > networkinfo.txt" digunakan untuk menampilkan semua informasi konfigurasi jaringan lalu menyimpannya ke file networkinfo.txt, sehingga bisa dibaca atau dianalisis tanpa harus melihat di Command Prompt.
![96d18130-f67f-4d43-af75-50d8e2157673](https://github.com/user-attachments/assets/704a370a-22c9-4111-b996-21908299e008)

4) selanjutnya tulis "ipconfig /flushdns" digunakan untuk menghapus cache DNS di komputer. Dengan menghapus cache ini, sistem akan mengambil ulang data DNS terbaru dari server, dan biasanya dipakai untuk mengatasi masalah koneksi atau error DNS.
