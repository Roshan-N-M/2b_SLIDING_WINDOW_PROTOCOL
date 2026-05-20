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
s = socket.socket()
s.connect(('localhost', 8000))
n = int(input("Enter number of frames: "))
w = int(input("Enter window size: "))
frames = list(range(1, n+1))
i = 0
while i < n:
      send_frames = frames[i:i+w]
      msg = " ".join(map(str, send_frames))
      print("Sending frames:", msg)
      s.send(msg.encode())
      ack = s.recv(1024).decode()
      print("Received:", ack)
      i += w
s.close()

SERVER

client.py
import socket
s = socket.socket()
s.connect(('localhost', 8000))
n = int(input("Enter number of frames: "))
w = int(input("Enter window size: "))
frames = list(range(1, n+1))
i = 0
while i < n:
      send_frames = frames[i:i+w]
      msg = " ".join(map(str, send_frames))
      print("Sending frames:", msg)
      s.send(msg.encode())
      ack = s.recv(1024).decode()
      print("Received:", ack)
      i += w
s.close()
~~~
## OUPUT
CLIENT
<img width="1453" height="397" alt="image" src="https://github.com/user-attachments/assets/e2e4dd21-39c9-4282-b73a-14819fe6e39d" />

SERVER
<img width="1449" height="241" alt="image" src="https://github.com/user-attachments/assets/a70b05bd-3734-47ad-aff6-7ffe92bec2c1" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
