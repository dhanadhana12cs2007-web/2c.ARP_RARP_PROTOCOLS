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
client.arp
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
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
server.arp
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="1325" height="311" alt="Screenshot 2026-11-18 083534" src="https://github.com/user-attachments/assets/8b0b991b-2f31-4808-8389-d6e627b5eb49" />

<img width="1323" height="315" alt="Screenshot 2026-11-18 083524" src="https://github.com/user-attachments/assets/ef7bd0ac-f8a9-426a-9ae3-8d1c5d13295f" />

## PROGRAM - RARP
client.rarp
```
import socket 
s=socket.socket() 
s.bind(('localhost',7000)) 
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
server.rarp
```
import socket 
s=socket.socket() 
s.connect(('localhost',7000))
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP

<img width="1317" height="315" alt="Screenshot 2026-11-18 082932" src="https://github.com/user-attachments/assets/f4f8cd6b-dbd5-4c3c-b5d4-c8496254e81e" />

<img width="1323" height="267" alt="Screenshot 2026-11-18 082900" src="https://github.com/user-attachments/assets/649074d6-f635-4d18-a471-e205fb365d82" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
