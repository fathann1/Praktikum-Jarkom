# Modul 4 DNS

DNS (Domain Name System) adalah sistem yang mengubah nama domain (seperti google.com) menjadi alamat IP. DNS bekerja dengan mengirim permintaan ke server DNS lokal, lalu menerima hasilnya.

Sebenarnya, proses yang lebih rumit terjadi di sisi server. Server DNS yang tersusun secara hierarki akan saling berkomunikasi untuk mencari jawaban, baik secara rekursif maupun iteratif, tanpa terlihat oleh pengguna.

## 1. Nslookup
Nslookup adalah perintah yang digunakan untuk melakukan query ke server DNS guna mendapatkan informasi tentang domain atau host, seperti alamat IP, nama domain, dan record DNS lainnya. Perintah ini bekerja dengan mengirim permintaan ke server DNS tertentu, lalu menampilkan hasil responsnya kepada pengguna.

### Contoh Penggunaannya:
1) Perintah nslookup [www.nit.edu](http://www.nit.edu) digunakan untuk mengecek apakah domain tersebut terdaftar dan memiliki alamat IP. Perintah ini mengirim permintaan ke server DNS lalu menampilkan hasilnya. Jika hasilnya domain tidak ditemukan, berarti domain tersebut tidak terdaftar di sistem DNS.
