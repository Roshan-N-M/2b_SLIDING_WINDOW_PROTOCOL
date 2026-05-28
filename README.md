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
~~~
CLIENT

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode()) 

SERVER
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
## OUPUT
CLIENT

<img width="892" height="139" alt="image" src="https://github.com/user-attachments/assets/de554ace-e0bc-452c-88f3-6178ca6569ae" />

SERVER

<img width="886" height="184" alt="image" src="https://github.com/user-attachments/assets/517fa2af-14c5-47a3-b320-51f847042105" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
