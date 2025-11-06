# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
# CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
```
# Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
# Client

<img width="797" height="1049" alt="Screenshot 2025-11-06 104627" src="https://github.com/user-attachments/assets/3db1d494-36df-42bb-843d-4c8d6b8ee870" />


# server
<img width="670" height="917" alt="Screenshot 2025-11-06 104547" src="https://github.com/user-attachments/assets/27bb1266-b970-4d05-b365-a4bd587371c7" />


## PROGRAM - RARP
# Client
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
```
# server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
# Client
<img width="710" height="957" alt="Screenshot 2025-11-06 105008" src="https://github.com/user-attachments/assets/71310efe-f7df-4b73-9f01-81e647d54a86" />



## SERVER - RARP
<img width="1136" height="405" alt="image" src="https://github.com/user-attachments/assets/865d80e9-9ea2-4e2b-9290-0d58955022b4" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
