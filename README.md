# Sliding-Window-Protocol

IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

EXP: 2

DATE: 20.03.23

AIM:

To write a python program to perform sliding window protocol

ALGORITHM:

1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it
will send NACKsignal to client.
6. Stop the program

PROGRAM:

CLIENT:

```
import socket

sock = socket.socket()
sock.bind(('localhost', 8000))
sock.listen(5)

c, addr = sock.accept()

size = int(input("Enter number of frames to send: "))
frames = list(range(size))

window_size = int(input("Enter Window Size: "))

start = 0
i = 0

while i < len(frames):
    start += window_size
    c.send(str(frames[i:start]).encode())

    ack = c.recv(1024).decode()
    if ack:
        print(ack)
    i += window_size

c.close()

```

SERVER:

```
import socket

sock = socket.socket()
sock.connect(('localhost', 8000))

while True:
    data = sock.recv(1024).decode()
    if not data:
        break
    print("Received frames:", data)
    sock.send("Acknowledgement received from the receiver".encode())

sock.close()

```

OUTPUT:

CLIENT:
![Screenshot from 2023-05-12 20-53-20](https://github.com/Harsayazheni/Sliding-Window-Protocol/assets/118708467/356d4080-f672-4597-a550-f9ce8866b931)

SERVER:
![Screenshot from 2023-05-12 20-53-29](https://github.com/Harsayazheni/Sliding-Window-Protocol/assets/118708467/7734005b-5c45-41f3-88c3-cac48a2d95dd)

RESULT:

Thus, python program to perform stop and wait protocol was successfully executed.
