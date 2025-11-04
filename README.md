# 3b.CREATION FOR CHAT USING TCP SOCKETS
-AADHITHAN B 212224040001
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
CLIENT:
```import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost', 8000))
print("Connected to server on port 8000")

try:
    while True:
        msg = input("Client > ")
        if msg.lower() in ["exit", "quit"]:
            print("Closing connection...")
            s.close()
            break
        s.send(msg.encode())
        data = s.recv(1024)
        if not data:
            print("Server disconnected.")
            break
        print("Server >", data.decode())
except KeyboardInterrupt:
    print("\nClient manually stopped.")
finally:
    s.close()
```
SERVER:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('localhost', 8000))
s.listen(5)
print("Server is listening on port 8000")

c, addr = s.accept()
print("Connected with", addr)

while True:
    ClientMessage = c.recv(1024).decode()
    if not ClientMessage:
        break
    print("Client >", ClientMessage)
    c.send(ClientMessage.encode())

c.close()
s.close()
```
## OUPUT
CLIENT:

<img width="1096" height="283" alt="image" src="https://github.com/user-attachments/assets/08c2bfce-59ab-4ac7-b5c4-aaadf8ccf2b3" />

SERVER:

<img width="1085" height="242" alt="image" src="https://github.com/user-attachments/assets/ab2dc5ae-4457-45e5-9c93-357b2b42283d" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
