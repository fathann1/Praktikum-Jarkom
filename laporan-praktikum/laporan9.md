# Modul 9  WEB SERVER
## Web Server
Web server adalah bagian penting dalam komunikasi di internet. Web server bertugas menerima permintaan dari pengguna melalui browser, lalu mengirimkan halaman web atau data yang diminta. Komunikasi ini biasanya menggunakan protokol HTTP yang berjalan di atas TCP.

##
Tujuan Praktikum 
1.	Mahasiswa bisa membuat program web server sederhana berbasis TCP socket programming

## Langkah-Langkah
  1. mebuat folder week9
  2. Membuat file serverweb.py di VScode
  3. code :

```python
from socket import *
import sys

# membuat socket server (TCP)
serverSocket = socket(AF_INET, SOCK_STREAM)

# Prepare a server socket
serverPort = 6789
serverSocket.bind(('', serverPort))
serverSocket.listen(1)

while True:
    # Establish the connection
    print('Ready to serve...')
    connectionSocket, addr = serverSocket.accept()

    try:
        # menerima request dari client
        message = connectionSocket.recv(1024).decode()
        print(message)

        # mengambil nama file
        filename = message.split()[1]

        # membuka file
        f = open(filename[1:])
        outputdata = f.read()

        # Send HTTP header
        connectionSocket.send("HTTP/1.1 200 OK\r\n".encode())
        connectionSocket.send("Content-Type: text/html\r\n".encode())
        connectionSocket.send("\r\n".encode())

        # kirim isi file
        for i in range(len(outputdata)):
            connectionSocket.send(outputdata[i].encode())

        connectionSocket.send("\r\n".encode())
        connectionSocket.close()

    except IOError:
        # kirim 404 jika file tidak ada
        connectionSocket.send("HTTP/1.1 404 Not Found\r\n".encode())
        connectionSocket.send("Content-Type: text/html\r\n".encode())
        connectionSocket.send("\r\n".encode())
        connectionSocket.send("<html><body><h1>404 Not Found</h1></body></html>".encode())

        # tutup koneksi
        connectionSocket.close()

serverSocket.close()
sys.exit()
```
  4. Setelah itu membuat file HelloWorld.html
  5. lalu diisi
```html
<html>
<head>
    <title>Test Server</title>
</head>
<body>
    <h1>Hello World!</h1>
    <p>Ini hasil server Python TCP</p>
</body>
</html>
```

## Hasilnya
1. Kita buka terminal lalu ketik ini "py serverweb.py" lalu di enter
2. Setelah itu Buka browser ketikan URL "http://localhost:6789/HelloWorld.html"
3. Maka akan muncul tampilan seperti ini:

<img width="1600" height="606" alt="image" src="https://github.com/user-attachments/assets/dc70b55c-0d2f-4fcf-b3a8-d4e5273124d2" />

4. Lalu buka tab lainnya dan ketikkan "http://localhost:6789/salah.html"
5. Maka akan muncul tampilan seperti ini:

<img width="1600" height="714" alt="image" src="https://github.com/user-attachments/assets/d57e7bd2-c97e-4d0c-9fb5-d8d76ab76c48" />

