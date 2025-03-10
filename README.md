# APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM
# EXP: 10
# DATE:10-05-2023
# AIM:
To write a python program for creating Chat using TCP Sockets Links.

# ALGORITHM:
# Client:
Import the necessary modules in python
Create a socket connection to using the socket module.
Send message to the client and receive the message from the client using the Socket module in server
Send and receive the message using the send function in socket.
# PROGRAM:

## Developed : ISHAQ HUSSAIN A
## Reg no : 212221040059

# CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
  print('receiving data...')
  data = s.recv(1024)
  print('data=%s', (data))
  if not data:
    break
  f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
# SERVER:
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'myfile.txt'  # Replace 'path/to' with the actual path to the file
    try:
        with open(filename, 'rb') as f:
            l = f.read(1024)
            while l:
                conn.send(l)
                print('Sent', repr(l))
                l = f.read(1024)
        print('Done sending')
    except FileNotFoundError:
        print(f'File {filename} not found.')
    
    conn.send('Thank you for connecting'.encode())
    conn.close()
 ```
# CLIENT OUTPUT :
![image](https://github.com/DhanushPalani/EX-NO-10/assets/121594640/52a13d80-2a16-47c4-aab0-9234f15937e9)

# SERVER OUTPUT :
![image](https://github.com/DhanushPalani/EX-NO-10/assets/121594640/0d9ede5f-9d68-4cf9-9514-cb98a880f10c)

# RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
