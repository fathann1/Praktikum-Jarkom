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

3. Gunakan filter HTTP untuk menampilkan paket yang sesuai. Kemudian pilih salah satu paket untuk melihat detail isi paket tersebut.
![7a1206a3-d985-4281-b0f7-f93c02f4004a](https://github.com/user-attachments/assets/92e05f07-9894-4823-9322-0be23dae341e)


---

## Modul 3.4 Dokumen HTML dengan Embedded Objects
Pada modul ini dipelajari dokumen HTML yang memuat berbagai objek tambahan seperti gambar, CSS, dan JavaScript. Saat halaman dibuka, browser akan mengirimkan beberapa request HTTP untuk mengambil seluruh elemen tersebut. Proses ini dapat diamati melalui hasil capture paket menggunakan Wireshark, sehingga membantu memahami bagaimana sebuah halaman web dimuat secara lengkap oleh browser.

## Langkah-langkah Percobaan
1. Buka Wireshark, pilih jaringan WIFI, lalu mulai capture paket.
![7d5ba07d-a56c-4a10-b140-4d80ae3024f8](https://github.com/user-attachments/assets/29b172fa-73b9-45ca-9691-974069aec599)

2. Buka browser dan akses halaman berikut:
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
![57a57c84-c725-4a93-9bd6-07c91ec5db29](https://github.com/user-attachments/assets/dcf24cee-6198-4dba-b0b1-60fd00e682c3)


3. Kembali ke Wireshark dan gunakan filter HTTP untuk melihat paket yang ditangkap. Setelah halaman dibuka, pada Wireshark akan terlihat data seperti format JPEG, karena halaman tersebut memuat gambar yang ikut dikirim melalui request HTTP.
![70fb611d-58cd-43f0-ab86-9afa4a4343ec](https://github.com/user-attachments/assets/e2878ff0-6f18-410e-b25a-af1a9e28b749)


---

## Modul 3.5 HTTP Authentication
Pada bagian ini dibahas proses autentikasi HTTP, yaitu mekanisme login yang terjadi ketika client mengakses halaman yang memerlukan username dan password. Proses ini dapat diamati melalui paket HTTP yang ditangkap menggunakan Wireshark, sehingga memberikan pemahaman mengenai bagaimana data autentikasi dikirim dan diproses dalam komunikasi antara client dan server.

## Langkah-langkah Percobaan
1. Jalankan Wireshark, pilih jaringan WIFI, lalu mulai capture paket.
![d95e8679-fac7-4f79-a44f-7f47464c2022](https://github.com/user-attachments/assets/e4e40182-0aa3-46a2-a2a0-5ef26766a9e0)

2. Buka browser dan akses halaman berikut:
http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
![5df11a6b-a5c8-41dd-bb99-a97f6647ed81](https://github.com/user-attachments/assets/a5f14db7-e6ca-44a2-abc2-780679cad9b4)
akan muncul perintah di minta untuk masukkan username dan password

3. Masukkan username **wireshark-students** dan password **network**, lalu tekan enter.
![556cb4d7-973a-4fde-b89c-531a81392377](https://github.com/user-attachments/assets/7a1b68ef-b342-4e21-b2a2-407f2138a587)

4. Setelah berhasil, pada Wireshark akan terlihat respon seperti "Unauthorized" pada salah satu paket HTTP.
![84fe07b8-9fa0-469c-8970-2906d0859a7b](https://github.com/user-attachments/assets/561a83be-c0a4-4052-9e7a-93c0ddf49f26)
