# Modul 7 SOCKET PROGRAMMING

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

### TCP Server
```python
from socket import * # import all library 

serverPort = 12000  # membuat port untuk komunikasi
serverSocket = socket(AF_INET, SOCK_STREAM) # membuat socket ipv4 dan TCP

serverSocket.bind( #menghubungkan socket dengan alamat dan port
    ('', serverPort) # alamat kosong 
)

serverSocket.listen(1) # server siap menerima 1 koneksi dari client
print("[SYSTEM] server TCP siap digunakan") # menampilkan pesan server siap digunakan

running = True # variabel untuk menjalankan program, jika false program akan berhenti
while running: # loop agar program terus berjalan
    connectionSocket, addr = serverSocket.accept() # menerima koneksi dari client, addr untuk menyimpan alamat client
    while True: # loop untuk menerima pesan dari client
        message = connectionSocket.recv(2448).decode() # menerima pesan dari client, decode untuk mengubah byte menjadi string

        if not message: # jika pesan kosong, berarti client sudah keluar
            break

        if message.lower() == "exit": # pesan "exit" untuk keluar dari program
            print("[SYSTEM] client ingin keluar") # menampilkan pesan client ingin keluar
            running = False # ubah variabel running menjadi false untuk keluar dari loop
            break

        modifiedMessage = message.upper() # mengubah pesan menjadi capslock
        print("[SERVER] diterima: ",modifiedMessage) # menampilkan pesan yang diterima dari client

        connectionSocket.send( # mengirim pesan ke client 
            modifiedMessage.encode() # encode untuk mengubah string menjadi byte
        )
        
    connectionSocket.close() # menutup koneksi dengan client
serverSocket.close() # menutup socket
```

### Alur TCP
1. Server dijalankan terlebih dahulu
2. Client melakukan koneksi ke server
3. Client mengirim data
4. Server memproses data
5. Server mengirim hasil ke client
6. Client menampilkan hasil
