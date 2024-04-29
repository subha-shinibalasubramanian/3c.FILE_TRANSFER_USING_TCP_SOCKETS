# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.  
**NAME :SUBHASHINI.B**   
**REGISTER NUMBER :212223040211**  
## PROGRAM
## SERVER
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'C:\\Users\\admin\\OneDrive\\Desktop\\cnfile.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()

```
## CLIENT

```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('connection closed')

```

## OUPUT
## SERVER

![image](https://github.com/subha-shinibalasubramanian/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/164154478/d163cdff-2fe5-4245-b414-72561b578ffb)

## CLIENT

![Screenshot 2024-04-29 140106](https://github.com/subha-shinibalasubramanian/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/164154478/875f9ebb-378b-4ddb-9008-e70133894836)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
