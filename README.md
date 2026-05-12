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
## client
~~~
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"169.254.74.176":"B8:F7:75:50:12:3E"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())

~~~
## server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical address : ")
    s.send(ip.encode())
    print("MAC address",s.recv(1024).decode())
~~~
## OUPUT - ARP
<img width="763" height="233" alt="Screenshot 2026-05-12 134739" src="https://github.com/user-attachments/assets/47b73f80-e8f5-43fd-8f02-71420f602140" />

## PROGRAM - RARP
## client
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"B8:F7:75:50:12:3E":"169.254.74.176"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
~~~
## server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC  address : ")
    s.send(ip.encode())
    print("logical address",s.recv(1024).decode())

~~~
## OUPUT -RARP
<img width="859" height="592" alt="Screenshot 2026-05-12 135034" src="https://github.com/user-attachments/assets/2468b52b-4f24-4276-80a2-701bab8d2b34" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
