# Modul 7 - SOCKET PROGRAMMING


## Pengertian Socket Programming
Socket programming adalah metode komunikasi antar komputer dalam jaringan dengan menggunakan socket sebagai media pertukaran data. Dalam prosesnya terdapat dua peran utama, yaitu client yang mengirim permintaan dan server yang menerima serta memberikan respons. Komunikasi ini umumnya menggunakan protokol TCP yang lebih stabil dan menjamin data terkirim dengan benar, atau UDP yang lebih cepat namun tanpa jaminan keandalan pengiriman. Dengan socket programming, perangkat dalam jaringan dapat saling bertukar data secara langsung.

## Implementasi TCP
### TCP Client
```python
from socket import * # import all libary

serverName = "localhost" # alamat server
serverPort = 12000 # membuat port untuk komunikasi

clientSocket = socket(AF_INET, SOCK_STREAM) # membuat socket ipv4 dan TCP
clientSocket.connect( # menghubungkan socket ke server
    (serverName, serverPort)
)

print("[SYSTEM] Masukan pesan") # pesan yang akan dikirim ke server

running = True # variabel untuk menjalankan program, jika false program akan berhenti
while running: # loop agar program terus berjalan
    message = input("> ") # input pesan yang akan dikirim ke server
    
    # mengirim pesan ke server, encode untuk mengubah string menjadi byte
    clientSocket.send(message.encode()) 
    if message == "exit": # pesan "exit" untuk keluar dari program
        print("[SYSTEM] keluar dari program")
        running = False # ubah variabel running menjadi false untuk keluar dari loop
        break

    modifiedMessage = clientSocket.recv(2048) # menerima pesan dari server, 2048 adalah ukuran buffer
    print("[SERVER] pesan : ", modifiedMessage.decode()) # decode untuk mengubah byte menjadi string

clientSocket.close() # menutup socket
print("[SYSTEM] socket ditutup")
```
