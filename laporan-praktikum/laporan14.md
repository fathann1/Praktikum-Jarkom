# Modul 14 - WIFI
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________
Tujuan Praktikum
- Kita sebagai mahasiswa dapat mempelajari cara kerja protokol WIFI menggunakan Wireshark.

## WIFI
Materi minggu ini membahas jaringan Wi-Fi berdasarkan standar IEEE 802.11, yaitu serangkaian protokol internasional yang dirancang oleh Institute of Electrical and Electronics Engineers untuk mengatur komunikasi data pada jaringan nirkabel di lapisan fisik dan lapisan MAC.

Dalam jaringan Wi-Fi, terdapat dua frekuensi utama yang umum digunakan, yaitu 2.4 GHz dan 5 GHz. Keduanya memiliki karakteristik yang berbeda — frekuensi 2.4 GHz unggul dalam hal jangkauan sinyal dan kemampuan menembus dinding, namun memiliki kecepatan transfer yang lebih lambat dan rentan terhadap interferensi karena banyak perangkat rumah tangga menggunakan spektrum yang sama. Sebaliknya, frekuensi 5 GHz menawarkan kecepatan transfer yang jauh lebih tinggi dengan interferensi rendah, sehingga cocok untuk kebutuhan real-time seperti gaming atau streaming, meskipun jangkauannya lebih terbatas dan kurang mampu menembus penghalang fisik seperti dinding beton.

Selain frekuensi, dibahas pula mengenai Access Point (AP) yang berfungsi sebagai jembatan jaringan untuk menghubungkan klien nirkabel ke jaringan kabel lokal sekaligus memperluas jangkauan sinyal. Pengguna dapat berpindah antar Access Point secara otomatis ketika berpindah lokasi, dan perangkat akan menyambung ke AP terdekat tanpa perlu konfigurasi manual.

Konsep penting lainnya adalah Beacon Frame, yaitu paket yang dikirim secara berkala oleh AP kepada perangkat untuk mengkonfirmasi keberadaan dan status koneksi jaringan. Pada Wireshark, beacon frame dapat disaring menggunakan filter wlan.fc.subtype == 8 && wlan.fc.type == 0

## Kita Cek

Disini KIta akan mengecek data Wireshark_802_11.pcap

<img width="1568" height="697" alt="image" src="https://github.com/user-attachments/assets/303e919e-6cff-4ae1-a5c4-afc581c46fcb" />

Berdasarkan hasil tangkapan layar Wireshark, Beacon Frame dikirimkan secara periodik setiap sekitar 102 milidetik (Time delta from previous displayed frame: 102.350000 milliseconds). Tercatat bahwa aktivitas beaconing ini berlangsung dengan total pengiriman sebanyak 2364 paket, dengan 762 paket yang ditampilkan setelah filter diterapkan.

<img width="1918" height="1137" alt="image" src="https://github.com/user-attachments/assets/1a8189ce-b34b-486e-b671-ebcd9507298d" />

Berdasarkan ekspansi detail paket pada Frame 100, ditemukan parameter-parameter berikut:

- PHY Type (802.11b HR/DSSS): Menunjukkan tipe lapisan fisik nirkabel yang digunakan adalah standar 802.11b berkecepatan tinggi dengan modulasi High-Rate Direct Sequence Spread Spectrum.
- Short Preamble (False): Menandakan penggunaan Preamble panjang (Long Preamble). Nilai False berarti sistem memprioritaskan kompatibilitas dengan perangkat lama dibanding optimasi kecepatan.
- Channel (6) / Frequency (2437 MHz): Jaringan ini beroperasi pada Saluran 6 di spektrum frekuensi 2.4 GHz.
- Signal Strength / Noise Level: Kekuatan sinyal yang diterima adalah -30 dBm (sangat kuat/bagus) dengan tingkat gangguan (Noise) berada pada -100 dBm, menghasilkan Signal/Noise Ratio sebesar 70 dB.
- Data Rate: Kecepatan transfer data saat frame ini dikirim adalah 1,0 Mb/s.

Cek Tagged Parameters

- Tag: SSID parameter set: Menampilkan identitas nama jaringan Wi-Fi, yaitu "30 Munroe St".
- Tag: Supported Rates: Menyebutkan kecepatan transfer data yang didukung oleh AP ini, yakni 1, 2, 5.5, dan 11 Mbps.
- Tag: Extended Supported Rates: Menyebutkan kecepatan tambahan yang didukung oleh standar yang lebih baru, berkisar dari 6 Mbps hingga 54 Mbps.

## Kita Cek Data Transfer
Disini Kita mengecek perpindahan data, diterapkan filter alamat IP server Untuk menganalisis perpindahan data, diterapkan filter alamat IP server ip.addr == 128.119.245.12

<img width="1600" height="944" alt="image" src="https://github.com/user-attachments/assets/31faf052-b57b-42c6-87b6-ea83cffccfe8" />

Hasil menunjukkan proses Three-Way Handshake TCP (SYN → SYN-ACK → ACK) yang dimulai pada Frame 474 diikuti oleh paket HTTP GET pada Frame 480 untuk mengunduh dokumen teks /wireshark-labs/alice.txt dengan protokol HTTP/1.1.

Setelah Kita Cek, Paket data dibungkus menggunakan protokol IEEE 802.11 plus radiotap header sebelum diteruskan melalui lapisan Logical-Link Control (LLC) ke Internet Protocol Version 4 (IPv4) dengan alamat asal klien 192.168.1.109 dan alamat tujuan server 128.119.245.12. Paket HTTP GET ini dikirimkan pada frekuensi 2437 MHz (Channel 6, 2.4 GHz) menggunakan standar 802.11g (ERP) dengan kecepatan data 48,0 Mb/s, dengan kekuatan sinyal sebesar -38 dBm dan rasio sinyal terhadap noise sebesar 62 dB.

## Mengecek Association & Disassociation

tulis filter "wlan.fc.type_subtype == 0"

<img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/9db787f5-ebe4-4ce1-8175-006a4b2f0030" />

### Expand paket awal

<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/8b672526-1bcb-4f9f-99fc-57141da49bde" />

Pada Frame 1750, perangkat Intel_d1:b6:4f (00:13:02:d1:b6:4f) mengirimkan Association Request kepada AP CiscoLinksys_f5:ba:bb (00:18:39:f5:ba:bb) dengan SSID "linksys_SES_24086". Detail frame menunjukkan:

- Type/Subtype: Association Request (0x0000)
- Frame Control Field: 0x0000
- Duration: 314 mikrodetik
- Sequence Number: 1607
- BSS Id: CiscoLinksys_f5:ba:bb (00:18:39:f5:ba:bb)
- WLAN Flags: ........C


### Expand paket akhir

<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/050a87fa-6c7f-40d3-a5f6-135506ebc7fe" />

Pada Frame 2162, klien Intel_d1:b6:4f (00:13:02:d1:b6:4f) berpindah dan mengirimkan Association Request baru ke AP CiscoLinksys_f7:1d:51 (00:16:b6:f7:1d:51) dengan SSID "30 Munroe St". Detail frame menunjukkan:

- Type/Subtype: Association Request (0x0000)
- Frame Control Field: 0x0000
- Duration: 44 mikrodetik
- Sequence Number: 1648
- BSS Id: CiscoLinksys_f7:1d:51 (00:16:b6:f7:1d:51)
- WLAN Flags: ........C

Jika membandingkan paket permintaan asosiasi teratas (Frame 1750) dengan paket asosiasi terbawah (Frame 2162), terjadi perubahan pada bagian parameter SSID:

Pada Frame 1750, klien mencoba berasosiasi ke AP dengan SSID "linksys_SES_24086".
Pada Frame 2162 (paling bawah), klien berpindah dan mengirim permintaan asosiasi baru ke AP dengan SSID "30 Munroe St".

Tanggapan Asosiasi (Association Response) dianalisis melalui filter subtype respon: wlan.fc.type_subtype == 1
Ditemukan Frame 2166 yang merupakan Association Response dengan detail sebagai berikut:

<img width="1600" height="754" alt="image" src="https://github.com/user-attachments/assets/9b7403a4-e5a9-47d4-92fc-af6489f94e5b" />

- Type/Subtype: Association Response (0x0001)
- Frame Control Field: 0x1000
- Duration: 314 mikrodetik
- Sequence Number: 3728
- Receiver address: Intel_d1:b6:4f (00:13:02:d1:b6:4f)
- Transmitter address: CiscoLinksys_f7:1d:51 (00:16:b6:f7:1d:51)
- BSS Id: CiscoLinksys_f7:1d:51 (00:16:b6:f7:1d:51)

Di sini, Transmitter Address diisi oleh MAC Address milik perangkat pengirim respon, yaitu CiscoLinksys_f7:1d:51, sebagai tanda bahwa Access Point menyetujui permintaan koneksi dari klien (Intel_d1:b6:4f).
