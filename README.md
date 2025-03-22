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
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
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


```
## OUPUT
![2nd server idle](https://github.com/user-attachments/assets/4079ed48-3511-444e-9d29-b256e02e4bd0)
![2nd cmd server](https://github.com/user-attachments/assets/e1f1dc15-c32e-4b36-8ed7-f5f30c7c24b7)
![2nd cmd client](https://github.com/user-attachments/assets/83f32ed2-9487-47db-af4a-e69751ddf3da)
![2nd client idle](https://github.com/user-attachments/assets/64dc325d-262f-44b0-ba7e-0a901b4e5a5a)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
