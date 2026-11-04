# Ex. No: 2a – Stop and Wait Protocol

## Computer Networks Lab

### AIM
To write and execute a Python program to implement the Stop and Wait Protocol using client-server socket programming.

## STUDENT DETAILS

- **Name:** MANORAJAPRIYAN.L.E
- **Register Number:** 212225040227
- **Department:** B.E. Computer Science and Engineering
- **College:** Saveetha Engineering College

## ALGORITHM

1. Start the program.
2. Create a server socket and bind it to the localhost address and port number 8000.
3. Make the server listen for incoming client connections.
4. Create a client socket and connect it to the server.
5. Get the number of frames to be transmitted from the user.
6. Read each frame from the user and send it to the server.
7. The server receives the frame and displays the received data.
8. The server sends an acknowledgment (ACK) to the client after receiving each frame.
9. The client receives and displays the acknowledgment.
10. Repeat the process until all frames are transmitted.
11. Close the sockets and stop the program.

## PROGRAM

### Server Program

```python
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
s.close()
```

### Client Program

```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```

## EXECUTION PROCEDURE

1. Save the server program as `server.py`.
2. Save the client program as `client.py`.
3. Open two terminals in VS Code.
4. Run the server program first:

   ```bash
   python server.py
   ```

5. Run the client program in the second terminal:

   ```bash
   python client.py
   ```

6. Enter the number of frames and the frame data.
7. Observe the frames received by the server and the ACK messages received by the client.

## OUTPUT

### Server Output

```text
Waiting for connection...
Connected to ('127.0.0.1', 58654)
Frame received: mano
Frame received: messi
Frame received: dhoni
Frame received: kohli
Frame received: barcelona
```

### Client Output

```text
Enter number of frames: 5
Enter frame: mano
Received: ACK
Enter frame: messi
Received: ACK
Enter frame: dhoni
Received: ACK
Enter frame: kohli
Received: ACK
Enter frame: barcelona
Received: ACK
```
## OUTPUT

<img width="1920" height="1080" alt="Screenshot (74)" src="https://github.com/user-attachments/assets/eca6751a-4291-4418-8016-52546536dfe8" />



## RESULT

Thus, the Python program to implement the Stop and Wait Protocol using client-server socket programming was successfully executed, and acknowledgment (ACK) messages were received for each transmitted frame.

## CONCEPT

The Stop and Wait Protocol is a flow control technique in which the sender transmits one frame at a time and waits for an acknowledgment from the receiver before sending the next frame. This ensures reliable frame transmission and prevents the sender from transmitting multiple frames simultaneously.
