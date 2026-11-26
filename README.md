# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
server
~~~
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(("127.0.0.1", 8000))
server.listen(1)

print("Server is waiting for a client...")

connection, address = server.accept()
print("Client connected:", address)

while True:
    data = connection.recv(1024)

    if not data:
        break

    message = data.decode()
    print("Client:", message)

    connection.sendall(message.encode())

connection.close()
server.close()
print("Server closed.")
~~~

client
~~~
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(("127.0.0.1", 8000))

print("Connected to the echo server.")
print("Type exit to stop.")

while True:
    message = input("Client: ")

    if message.lower() == "exit":
        break

    client.sendall(message.encode())

    reply = client.recv(1024).decode()
    print("Server:", reply)

client.close()
~~~


## OUPUT
<img width="1917" height="1015" alt="Screenshot 2026-11-26 142807" src="https://github.com/user-attachments/assets/89e637c0-b52a-42cc-ba98-f2b0e3f0eed6" />


## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
