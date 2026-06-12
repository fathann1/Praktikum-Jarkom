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

Konsep penting lainnya adalah Beacon Frame, yaitu paket yang dikirim secara berkala oleh AP kepada perangkat untuk mengkonfirmasi keberadaan dan status koneksi jaringan. Pada Wireshark, beacon frame dapat disaring menggunakan filter wlan.fc.subtype == 8 && wlan.fc.type == 0, dan dari hasil analisis terlihat bahwa beacon frame dikirimkan dengan interval setiap 8 milidetik.
