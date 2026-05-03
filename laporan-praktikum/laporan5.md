# UDP
UDP (User Datagram Protocol) adalah salah satu protokol di lapisan transport pada model TCP/IP yang digunakan untuk mengirim data secara langsung tanpa perlu membangun koneksi terlebih dahulu. Artinya, sebelum data dikirim, tidak ada proses “jabat tangan” seperti pada TCP data bisa langsung dikirim begitu saja.

## Langkah-Langkah Praktikum
1. Download file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
   <img width="401" height="164" alt="image" src="https://github.com/user-attachments/assets/1fcc86aa-e487-49e6-a524-9bef9d42a7d7" />

2. Extract file dan cari file http-ethereal-trace-5
   <img width="1206" height="129" alt="image" src="https://github.com/user-attachments/assets/d4648a58-ba28-42c4-b9d3-3074e022b2d6" />

3. Klik kanan pada file tersebut, kemudian buka dengan wireshark
   <img width="1600" height="948" alt="image" src="https://github.com/user-attachments/assets/8dda4c6f-4f67-44c5-8227-227c029547d0" />

4. Lakukan filter UDP dan pilih salah satu paket UDP
   <img width="1600" height="951" alt="image" src="https://github.com/user-attachments/assets/4750973f-101b-4c70-884e-fd6c76b37709" />



### Menjawab Pertanyaan
1) Field UDP
   <img width="1600" height="947" alt="image" src="https://github.com/user-attachments/assets/1e06b74b-bbdc-4627-93cb-0d82c7052bdb" />
   Jawab: Terdapat 4 field : Source Port, Destination Port, Length, Checksum
   
2. Panjang masing - masing dari dari field yang ada pada soal 1 yaitu :
   - Source port: 2 byte
   - Destination port: 2 byte
   - Lenght: 2 byte
   - Checksum: 2 byte 
   - di karenakan Header UDP selalu memiliki ukuran tetap 8 byte dan pada percobaan di atas ada 4 field jadi setiap field memiliki panjang 2 byte

3) Length
   <img width="968" height="309" alt="image" src="https://github.com/user-attachments/assets/d1edf579-9d22-495f-a99f-d64ebb7e1789" />
   Pada foto tersebut terlihat bahwa nilai Length  adalah 58. Artinya, panjang total paket UDP terdiri dari payload sebesar 50 byte ditambah header UDP sebesar 8 byte, sehingga 50 + 8 = 58. Dengan demikian, nilai Length memang menunjukkan ukuran keseluruhan paket UDP, yaitu gabungan antara header dan payload.

4) Jumlah maksimum byte UDP
   Jawab: Header UDP memiliki ukuran tetap sebesar 8 byte, sementara ukuran maksimum paket IP adalah 65.535 byte. Pada IPv4, header IP umumnya berukuran 20 byte. Jadi, untuk menghitung kapasitas maksimum data (payload) UDP, kita kurangi total ukuran paket IP dengan header IP dan header UDP:

65.535 − 20 − 8 = 65.507 byte.

Dengan demikian, ukuran maksimum payload yang bisa dikirim menggunakan UDP adalah 65.507 byte.

5) Port terbesar
    Jawab: Nomor port terbesar pada protokol UDP adalah 65535. Hal ini karena field **source port** dan **destination port** di header UDP masing-masing memiliki ukuran 16 bit. Dengan 16 bit, nilai maksimum yang bisa direpresentasikan adalah 2¹⁶ − 1, yaitu 65535.

Jadi, rentang nomor port UDP berada dari 0 sampai 65535.

