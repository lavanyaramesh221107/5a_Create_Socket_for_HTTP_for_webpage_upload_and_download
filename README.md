# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program:
## server:
```
import socket
import os

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for client
s.listen(5)

print("Server waiting for connection...")

# Accept connection
c, addr = s.accept()

print("Connected to:", addr)

while True:

    # Receive hostname
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    # Ping command
    response = os.popen(f"ping {hostname}").read()

    # Send result
    c.send(response.encode())

# Close socket
c.close()
s.close()
```

##client:

```
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

while True:

    # Get website name
    ip = input("Enter the website you want to ping: ")

    # Send to server
    s.send(ip.encode())

    # Receive result
    result = s.recv(1024).decode()

    print(result)
```
## OUTPUT
## server:
<img width="1344" height="266" alt="image" src="https://github.com/user-attachments/assets/58b35ba2-c47e-4ead-9c9f-d74e0937430c" />

## client:

<img width="1503" height="336" alt="image" src="https://github.com/user-attachments/assets/9bea5a50-5a9c-487e-8ead-146b9d1f9bc1" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
