# Modul 7 SOCKET PROGRAMMING
Nama       : Muhammad Rajwa Al Fathan Koessaputra  
NIM        : 103072400113  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________

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
7. Jika kita ketik exit kita akan keluar dan server berhenti

Output Contoh di terminal:
<img width="1132" height="290" alt="image" src="https://github.com/user-attachments/assets/6aa56b73-7c3c-4123-82f3-5f54ff840a14" />


## Implementasi UDP
### UDP Client
```python
from socket import *

serverName = 'localhost'  # ganti dari IP spesifik ke localhost
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_DGRAM)

print("[SYSTEM] Masukkan pesan (ketik 'exit' untuk keluar)\n")

while True:
    message = input("> ")

    if not message:
        continue

    clientSocket.sendto(message.encode(), (serverName, serverPort))

    if message.lower() == 'exit':
        print("[SYSTEM] Keluar dari program.")
        break

    balasan, _ = clientSocket.recvfrom(2048)
    print(f"[SERVER] pesan: {balasan.decode()}\n")

clientSocket.close()
print("[SYSTEM] Socket ditutup.")
```

### UDP Server
```python
from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))

print(f"[SYSTEM] Server UDP siap di port {serverPort}")

while True:
    message, clientAddress = serverSocket.recvfrom(2048)
    original = message.decode().strip()
    print(f"[SERVER] Diterima: {original}")

    if original.lower() == 'exit':
        print("[SYSTEM] Server dimatikan.")
        serverSocket.sendto("Server dimatikan.".encode(), clientAddress)
        break

    balasan = original.upper()
    print(f"[SERVER] Mengirim balik: {balasan}")
    serverSocket.sendto(balasan.encode(), clientAddress)

serverSocket.close()
```
### Alur UDP
1. Server dijalankan
2. Client langsung mengirim data tanpa koneksi
3. Server menerima data
4. Server memproses
5. Server mengirim balasan
6. Client menerima hasil
7. Jika kita ketik exit kita akan keluar dan server berhenti

Output Contoh di terminal:
<img width="1147" height="466" alt="image" src="https://github.com/user-attachments/assets/5f4bbbd3-887c-4128-b813-df5ff275095e" />
