# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program for implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client
~~~
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
~~~

Server

~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
   print(s.recv(1024).decode())
   s.send("acknowledgement recived from the server".encode())
~~~



## OUPUT

Client

![324156816-6ea99178-a72d-4f4d-8dd9-9b58b3de224c](https://github.com/user-attachments/assets/8f1fe9c6-09d0-4f76-8b49-8e8cb19b9cb2)

server
![324156848-afd8da0f-2c7e-4b39-a482-4d3150599f4a](https://github.com/user-attachments/assets/7251f059-647a-460d-892d-aa1cae1f07d5)






## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
