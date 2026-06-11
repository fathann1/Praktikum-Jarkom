# Modul 10 - IP
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________
Tujuan Praktikum
- Mahasiswa dapat mempelajari cara kerja protokol IP menggunakan Wireshark.

## 1. IP address
IP Address (Internet Protocol Address) adalah alamat unik yang digunakan untuk mengenali perangkat dalam jaringan. IP address berfungsi untuk membantu data dikirim ke perangkat tujuan dengan benar.

**Jenis-jenis**
- IPv4 : menggunakan 32-bit contoh:  192.168.184.1
- IPv6 : menggunakan 128-bit contoh: 2001:db8::1

Seperti ini

<img width="837" height="215" alt="image" src="https://github.com/user-attachments/assets/c0fa051a-eb8f-49ae-92e8-40fbb1792eaf" />

- Link-local IPv6 Address . . . . . : fe80::da35:2b4:714c:d372%3
- IPv4 Address. . . . . . . . . . . : 192.168.100.132

## 2. Traceroute dari suatu website
Traceroute adalah metode yang digunakan untuk mengetahui jalur atau hop yang dilewati paket data dari komputer menuju server tujuan.

**Fungsi Traceroute**
- Menampilkan jalur (hop) yang dilewati data.
- Mengetahui waktu tempuh pada setiap hop.
- Membantu mendeteksi masalah jaringan.

**Cara Melihat Traceroute dari Website**
1. Buka CMD
2. Ketik tracert google.com
<img width="918" height="786" alt="image" src="https://github.com/user-attachments/assets/6b0c1842-0b24-4565-853c-ba0327a3efde" />

Paket melewati 25 hop sebelum sampai ke server Google. Hop 1 (192.168.100.1) adalah router lokal / gateway Wi-Fi yang digunakan. Hop 2–3 (10.112.0.1 dan 180.250.252.69) adalah jaringan internal ISP. Hop 4–6 (180.240.190.77 dan 180.240.205.92) sudah masuk ke jaringan publik. Hop 7–12 (72.14.221.180 hingga 216.239.35.173) sudah masuk ke jaringan Google. RTO pada hop 13–24 terjadi karena router tidak merespon traceroute (firewall memblokir paket ICMP). Pada hop ke 25 paket berhasil sampai ke server Google (sa-in-f100.1e100.net = 74.125.200.100 = google.com). Waktu yang ditempuh relatif cepat dalam kisaran 1 ms – 40 ms, maka jaringan dalam kondisi yang baik.
