
## Use the tool NMAP [Command line only] to perform the below task. Run Wireshark in the background and capture only the necessary packets to showcase for the corresponding question.

### a) Explain the subnet and use the NMAP Command to scan the services for the whole subnet.

Subnetting allows network administrators to divide a large network into smaller subnetworks, which can be used to group devices that have similar functions or security requirements.
A subnet is a portion of a network that has been partitioned into smaller networks, each with its own unique IP address range and it is done to improve network performance, security, and manageability. 

Command to scan entire subnet - `nmap -sn <network address>/<subnet prefix/CIDR notation>`

Example - `nmap 192.168.1.0/24`

Victim Machine: In Victime Machine Apache Service is on 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/1b5ad1cf-8db6-42a0-ae13-262f009f8e17)

Attacker Machine: NMap Scan will do and check the network

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/cae403ad-a83b-4d9f-8a13-376400ecfe39)


### b) What is a firewall, and mention its types. Use the NMAP command to detect that a firewall protects the host.

Firewall
A firewall is a network security device that monitors and controls incoming and outgoing network traffic based on a set of predefined security rules. Its primary purpose is to protect networks and devices from unauthorized access, attacks, and malicious activity.
Firewalls can be implemented as software, hardware, or a combination of both. They work by examining the packets of network traffic and comparing them against the set of rules or policies defined by the administrator.
If a packet matches a rule, it is allowed to pass through the firewall. If it doesn't match any rule, it is either dropped or sent to a different location for further analysis
Types
- Packet filtering firewall
- Stateful inspection firewall
- Application-level gateway firewall
- Next-generation firewall
- Host-based firewall
nmap command to identify a firewall -
To identify a firewall we can use the Standard SYN Scan

>> Reason : The RST packet makes closed ports easy for Nmap to recognize. Filtering devices such as firewalls, on the other hand, tend to drop packets destined for disallowed ports. In some cases they send ICMP error messages (usually port unreachable) instead. Because dropped packets and ICMP errors are easily distinguishable > from RST packets, Nmap can reliably detect filtered TCP ports from open or closed ones, and it does so automatically.

Command - nmap -sS -p- <ip>

If a port is filtered by a firewall, Nmap will not be able to determine if it is open or closed, but will instead report it as "filtered"

where,

TCP SYN Scan (-sS)

TCP ACK Scan (-sA)

Victim Machine: Now setup a User friendly firewall in kali by `sudo apt install ufw`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d2d2aeb9-8eb5-4e4c-9c03-a409f9a89eef)

start ufw firewall with this command - `sudo ufw enable`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/75831b08-0b01-4f75-ae87-d7a4b9a92c1c)

Attacker Machine: If Firewall is enabled then port will mention as filtered port 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/11ae83ec-bb86-4d28-8736-cc4215d5b0bd)

if firewall is disabled then it will show as open port

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/c022f35f-5f2e-41ba-bc39-07b4a15a9c5b)

### c) Use the NMAP command to scan a network and determine which devices are running.

Command - `nmap -sn <ip>/<CIDR>` 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/10ebfdd6-9cab-4a79-88b6-fb7dd2d3ab4a)

### d) What are vertical and horizontal scanning?

- `Horizontal scanning or network scanning` sends requests to the same port on different hosts. Attackers use horizontal scanning to prepare for a mass attack.
- `Vertical scanning` sends requests to different ports on the same host. Attackers typically use vertical scanning to look for vulnerabilities in a preselected target.

### e) Use the NMAP command to scan multiple hosts. [HINT: Add hosts into a file and scan it].

Attacker: We have to add victim's IP Address into `/ect/hosts` file and have to scan using NMAP Command

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/3b55c060-151d-4d23-a5fd-b542b1ec5ee0)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d8192a6a-ce70-4259-af5f-ec9bff307e41)

### f) Use NMAP commands to export the output in XML format.

For this we use the `-oX` flag.

Command to save it is: `nmap -sV 10.0.2.9 -oX result.xml`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/091a4ef5-86bd-4fdb-99cb-992f00b698ff)

### g) Use the NMAP command to get OS information about a host.

`-O` : Enables OS detection, as discussed above. Alternatively, you can use -A to enable OS detection along with other things.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/ed147a5d-22b5-4ba5-a679-e06d77a3fedb)

### h) Explain ping sweeping and Perform ping sweeping using Nmap

Ping Sweep
Ping sweeping is a network reconnaissance technique used to determine which IP addresses are alive and responsive on a network. It involves sending a series of ICMP echo request messages, also known as pings, to a range of IP addresses, usually in a sequential order, to identify which ones are available and can be reached.

Ping sweeping is often used by network administrators to identify active hosts on a network and to map the network

Nmap command to perform ping sweep - nmap -sn <network address>/<CIDR>.

where, -sn - allows to perform a ping scan on the target:

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d08854f0-020c-412f-b669-b1ca55e98230)

## Try these below questions after completing the above commands. 

### 1. What is a web application firewall? How do you use Nmap to detect a WAF? Perform WAF fingerprint detection using NMAP.

A web application firewall (WAF) is a firewall that monitors, filters and blocks data packets as they travel to and from a website or web application.

A WAF can be either network-based, host-based or cloud-based and is often deployed through a reverse proxy and placed in front of one or more websites or applications.

Running as a network appliance, server plugin or cloud service, the WAF inspects each packet and uses a rule base to analyze Layer 7 web application logic and filter out potentially harmful traffic that can facilitate web exploits.

Command - `nmap --script http-waf-detect `

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/22a94cb3-93d4-4c54-94db-09d5b236b974)

### 2. What is EXIF data? Try to find EXIF data of images on a website using NMAP NSE

- It is a metadata that is embedded within image files, such as JPEGs, TIFFs, and RAW files. This data includes information about the camera settings used to take the picture, as well as information about the date, time, and location of the image
- Exif data can also include information about the camera's make and model, the lens used, and the exposure settings, such as shutter speed, aperture, and ISO.

Command - `nmap --script http-exif-spider flipkart.com`
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/9babb3d1-52f1-44a0-8ec0-2ef41b3500d3)

Appling command on our Victim Machine 
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/90377e48-b80d-4bf2-81ae-2f3c4108d400)

### 3. Use NMAP NSE to find all subdomains of the website.

All the nse scripts are loacated in `/usr/share/nmap/scripts/`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7bbd6cec-0d67-4d58-aba2-5b55259a5e48)

### 4. Perform a vulnerability scan on the target host using NMAP NSE.

To perform a vulnerability scan in NMAP NSE, We have command - `nmap -sV --script=vuln 10.0.2.9`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/bb81974e-859b-4f3f-8b69-ca0ce65c5f63)
