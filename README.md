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
Server:
~~~
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
        st +=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
~~~
Client:
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
~~~

## OUPUT

server
<img width="936" height="201" alt="Screenshot 2026-02-20 105519" src="https://github.com/user-attachments/assets/444a92ff-6580-46d6-926b-caf08e364a90" />


Client
<img width="933" height="154" alt="Screenshot 2026-02-20 105626" src="https://github.com/user-attachments/assets/6b38cec9-93d4-4efd-b02b-65491ccdc768" />






## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
