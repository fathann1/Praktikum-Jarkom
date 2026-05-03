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
