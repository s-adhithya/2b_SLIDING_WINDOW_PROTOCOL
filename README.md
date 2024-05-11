# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s
```
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### Client
![310865044-bbf7f1da-e462-4fe5-966c-e955294daa1d](https://github.com/s-adhithya/2b_SLIDING_WINDOW_PROTOCOL/assets/113497423/692965bb-4a63-4a75-9dab-b98e0794bb46)
### Server
![310865044-bbf7f1da-e462-4fe5-966c-e955294daa1d](https://github.com/s-adhithya/2b_SLIDING_WINDOW_PROTOCOL/assets/113497423/d3785ee1-fb3c-422a-a83d-5762b7367355)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
