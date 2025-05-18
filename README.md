# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM

ChatClient.py

```
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(("localhost", 12345))
print("Connected to the server. Type 'exit' to quit.")

try:
    while True:
        message = input("Client: ")
        client_socket.send(message.encode())

        if message.lower() == "exit":
            break

        response = client_socket.recv(1024).decode()
        print(f"Server: {response}")
finally:
    client_socket.close()
    print("Disconnected from the server.")
```

Chatserver.py

```

import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("localhost", 12345))
server_socket.listen(1)
print("Server is listening on port 12345...")

conn, addr = server_socket.accept()
print(f"Connection established with {addr}")

while True:
    data = conn.recv(1024).decode()
    if not data or data.lower() == "exit":
        print("Client disconnected.")
        break
    print(f"Client: {data}")
    
    response = input("Server: ")
    conn.send(response.encode())

conn.close()
server_socket.close()


```

## OUPUT

![image](https://github.com/user-attachments/assets/c1e16755-26ab-459f-822a-2337deb46c47)

![image](https://github.com/user-attachments/assets/58bfcef9-720b-49d6-a475-3f1c6b494130)


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
