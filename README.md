# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software : 
Command Prompt And Network Protocol Analyzer
## Procedure:
To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## Program
client.py
~~~
import socket
s = socket.socket()
s.connect(('localhost', 8000)) 
while True:
    ip = input("Enter the website you want to ping: ")
    s.send(ip.encode())
    print(s.recv(1024).decode())
~~~
server.py
~~~
import socket
import subprocess
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server waiting...")
c, addr = s.accept()
while True:
    hostname = c.recv(1024).decode()
    try:
        result = subprocess.check_output(
            ["ping", hostname],
            text=True
        )
        c.send(result.encode())
    except Exception as e:
        c.send(f"Error: {e}".encode())
~~~
## Output

<img width="1626" height="945" alt="Screenshot 2026-05-26 102752" src="https://github.com/user-attachments/assets/c27f26b3-3c9a-499e-b288-7f4b118d7ae3" />

## Result
Thus Execution of Network commands Performed 
