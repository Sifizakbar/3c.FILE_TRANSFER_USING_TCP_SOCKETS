# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

client.py
```python
import socket
s = socket.socket()
host = socket.gethostname() 
port = 60000 
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True: 
        print('receiving data...') 
        data = s.recv(1024) 
        print('data=%s', (data)) 
        if not data:
            break 
    f.write(data)
    f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```

server.py
```python
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening...")
c, addr = s.accept()
print("Got connection from", addr)
msg = c.recv(1024).decode()
print("Client says:", msg)
filename = "sample.txt"
with open(filename, 'rb') as f:
    data = f.read(1024)
    while data:
        c.send(data)
        data = f.read(1024)
print("File sent successfully")
c.close()
s.close()
```

sample.txt
```
Hello this is a file transfer using Python sockets.
```
## OUPUT
client:
<img width="1072" height="353" alt="Screenshot (476)" src="https://github.com/user-attachments/assets/51a8846c-38ee-4e66-b954-c366a2d90c1c" />
server:
<img width="1098" height="328" alt="Screenshot (478)" src="https://github.com/user-attachments/assets/280d27f1-93fc-45c4-b259-04affaaf9802" />



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
