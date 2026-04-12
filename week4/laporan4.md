# Modul 4 DNS

DNS (Domain Name System) adalah sistem yang berfungsi mengubah nama domain atau host menjadi alamat IP. DNS cukup berperan mengirimkan permintaan ke server DNS lokal dan menerima hasilnya. Proses yang lebih kompleks sebenarnya terjadi di sisi server, di mana server DNS yang tersusun secara hierarkis saling berkomunikasi untuk menyelesaikan permintaan tersebut, baik secara rekursif maupun iteratif, tanpa terlihat oleh klien.

## 1. Nslookup
Nslookup merupakan perintah yang digunakan untuk melakukan query ke server DNS guna memperoleh berbagai informasi terkait domain atau host, seperti alamat IP, nama domain, serta record DNS lainnya. Perintah ini bekerja dengan mengirimkan permintaan ke server DNS tertentu, kemudian menampilkan hasil respons yang diterima kepada pengguna.

### Berikut penggunaan nslookup pada command prompt:
1) Perintah nslookup www.nit.edu digunakan untuk melakukan pencarian informasi DNS terhadap domain tersebut dengan tujuan mengetahui apakah domain tersebut terdaftar dan memiliki alamat IP. Perintah ini bekerja dengan mengirimkan permintaan ke server DNS yang digunakan, kemudian menampilkan hasil respons yang diterima. Pada hasil yang ditunjukkan, domain tidak ditemukan, yang menandakan bahwa domain tersebut tidak tersedia atau tidak terdaftar dalam sistem DNS.
