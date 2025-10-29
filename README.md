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
**CLIENT**
```python
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
**SERVER**
```python
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT
![383512081-98cfc98f-204c-4250-ab10-3549264a8387](https://github.com/user-attachments/assets/4869615e-9d71-41dc-ae50-0f2927d282f1)
![383512150-47ec8f04-e7d4-4cc7-86e2-8c22b6b9b0c9](https://github.com/user-attachments/assets/0f43a318-c270-403e-8963-7ad504a45103)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
