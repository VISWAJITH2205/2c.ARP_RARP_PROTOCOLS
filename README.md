# 2c.SIMULATING ARP /RARP PROTOCOLS

## AIM:

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
   
## PROGRAM - ARP:

CLIENT
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

SERVER
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP:

CLIENT

![Screenshot 2025-04-12 055251](https://github.com/user-attachments/assets/86ec9b98-88b1-473a-af60-6173f96c75ca)

SERVER

![Screenshot 2025-04-12 055237](https://github.com/user-attachments/assets/b962383d-1988-4e81-97a2-761af0225ab2)

## PROGRAM - RARP:

CLIENT
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

 SERVER
 ```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP:

CLIENT

![Screenshot 2025-04-12 060603](https://github.com/user-attachments/assets/d99d7a78-a28c-4288-80fd-478481deb87b)

SERVER

![Screenshot 2025-04-12 060406](https://github.com/user-attachments/assets/f80c4f2d-87d1-43d2-ac81-d77d5d310a0a)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
