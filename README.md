# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
Name:T.Manikandan
Register number:212224110037
```
## server.py
```python
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server listening...")

c, addr = s.accept()
print("Connected:", addr)

while True:
    data = c.recv(1024)
    if not data: break
    msg = data.decode()
    print("Client:", msg)
    c.send(b"ACK")
    if msg.lower() == "exit": break

c.close()
s.close()
```
## client.py
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = input("Enter message for server: ")
    s.send(msg.encode())
    data = s.recv(1024).decode()
    print("Server:", data)

    if msg.lower() == "exit":
        break

s.close()
```
## OUTPUT
<img width="675" height="228" alt="image" src="https://github.com/user-attachments/assets/f2a9eb58-9578-49ee-84ba-2c680f159f86" />

<img width="735" height="288" alt="image" src="https://github.com/user-attachments/assets/2602dbbe-0560-4555-a762-0bbd04ff842e" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
