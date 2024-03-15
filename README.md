## M.HARINI 212222240035
# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to perform implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
   
## PROGRAM:

### client:

```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

size = int(input("Enter number of frames to send: "))
frames = list(range(size))
window_size = int(input("Enter Window Size: "))
start = 0

while start < size:
    end = min(start + window_size, size)
    frame_to_send = frames[start:end]
    c.send(str(frame_to_send).encode())
    
    ack = c.recv(1024).decode()
    if ack:
        print(ack)
    
    start += window_size

c.close()

```
### Server:

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    received_data = s.recv(1024).decode()
    
    if not received_data:
        break

    print("Received frames:", received_data)
    s.send("Acknowledgement received from the server".encode())

s.close()

```


## PROGRAM:

![image](https://github.com/Harinimuthu17/2b_SLIDING_WINDOW_PROTOCOL/assets/130278614/867a1a5d-0d24-45af-8e26-8883c9ae2136)

## OUTPUT:

![image](https://github.com/Harinimuthu17/2b_SLIDING_WINDOW_PROTOCOL/assets/130278614/9b7cee08-1988-41c1-b8a8-66d7dbd6b72b)

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed
