# Modul 3
HTTP
## Modul 3.2 Basic HTTP GET/response interaction
Pada praktikum week 2 ini masih melanjutkan pembahasan pada modul 3 mengenai HTTP. Namun, pada bagian ini lebih difokuskan pada pemahaman tentang interaksi dasar antara HTTP GET dan response yang terjadi antara client dan server.

langkah langkah percobaan

## Langkah-langkah Percobaan
1. Pertama, jalankan aplikasi Wireshark terlebih dahulu.
![9136662e-8994-4d16-9bd1-80663fae44af](https://github.com/user-attachments/assets/c87bdc52-7725-4245-9f69-1010df51474f)


2. Setelah aplikasi terbuka, pilih jaringan WIFI untuk memulai proses capture paket.
![12329c3e-2d57-4969-85d7-11b97cee64b0](https://github.com/user-attachments/assets/80c29215-4a48-41f7-a255-9236b468bb2a)


3. Pastikan proses capture sudah berjalan, kemudian buka browser dan akses halaman berikut: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
![0a591250-19a9-42c6-a8a8-e2abdd612854](https://github.com/user-attachments/assets/e4c86309-f0a1-4204-aa67-9e2e197e14de)


4. Pakai filter pada Wireshark untuk menampilkan paket dengan protokol HTTP.
![ad64209b-0912-4aa7-8b5e-0f48f24efc07](https://github.com/user-attachments/assets/26e2c784-50ed-41db-a4ec-d64492f0dadd)


5. Hentikan proses capture, lalu pilih salah satu paket untuk melihat detail informasi yang ditampilkan.
![259e3970-bf72-47d4-bcdf-a71dd90f7a24](https://github.com/user-attachments/assets/5b212b2b-fa77-49be-b0f7-ab3bc6a180d4)


---

## Uji Coba Web Tidak Ditemukan
Percobaan ini dilakukan untuk mengamati bagaimana respons server ketika klien mengakses alamat website yang tidak valid, namun tetap menggunakan protokol HTTP. Dengan demikian, percobaan ini bertujuan untuk memahami bagaimana server menangani permintaan yang salah atau tidak ditemukan dalam proses komunikasi berbasis HTTP.

## Langkah-langkah Percobaan
1. Buka Wireshark, pilih jaringan WIFI, lalu mulai proses capture paket.
![c53f0a04-d0a9-469b-9fe8-5d3ae4e21a58](https://github.com/user-attachments/assets/3e610ad0-4c3e-4a5b-bc1b-e7236f3a032f)

2. Terapkan filter HTTP untuk menampilkan paket yang relevan.
![7fb0f419-49af-48a1-afeb-1329fe01af06](https://github.com/user-attachments/assets/5847cf60-3afb-4eae-902c-925f941e619a)

3. Selanjutnya, coba akses link HTTP yang dimodifikasi dengan menambahkan karakter acak, misalnya:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.htmlfathan

4. Setelah itu, periksa kembali di Wireshark dan akan terlihat status error seperti kode 404 pada paket HTTP.
![4e192d2f-8ed0-4739-93cd-453f5629dae6](https://github.com/user-attachments/assets/9121df9c-5917-4d7f-8cb9-99b9d4d739f1)


---

## Modul 3.3 Mengambil Dokumen Berukuran Besar
Pada bagian ini dibahas proses pengambilan data berukuran besar, seperti halaman web atau file, melalui jaringan. Proses tersebut dapat diamati melalui hasil capture paket, yang melibatkan berbagai protokol komunikasi seperti HTTP, TCP, maupun FTP, sehingga memberikan gambaran yang lebih jelas mengenai alur transfer data dari server ke client.

## Langkah-langkah Percobaan
1. Jalankan Wireshark dan pilih jaringan WIFI, kemudian mulai capture paket.
![91557ff1-9127-4ee7-8153-885065c5c529](https://github.com/user-attachments/assets/ec890fa3-a151-4b9b-af4c-8f77c920cb6f)

2. Buka browser dan akses halaman berikut:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
![830c2e41-3067-4fd1-a046-3518d66a69b3](https://github.com/user-attachments/assets/5fc3157a-a61c-46bf-9819-05f2ba29d6ff)

3. Gunakan filter HTTP untuk menampilkan paket yang sesuai. Kemudian pilih salah satu paket untuk melihat detail ![7a1206a3-d985-4281-b0f7-f93c02f4004a](https://github.com/user-attachments/assets/92e05f07-9894-4823-9322-0be23dae341e)
isi paket tersebut.


---

