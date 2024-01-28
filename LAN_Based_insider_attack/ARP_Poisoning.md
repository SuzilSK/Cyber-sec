# LAN BASED INSIDER ATTACK

=> A Local Area Network (LAN)-based insider attack refers to malicious activities conducted by individuals with authorized access to the network, systems, or data within an organization's internal network. These attacks are perpetrated by individuals who have legitimate access to the network infrastructure and may exploit their privileges for malicious purposes. Insider attacks pose a significant threat as insiders often have a deep understanding of the organization's systems, making it challenging to detect and prevent such activities.

Types of LAN-based insider attacks that can be implemented on a system:

1. **Data Theft or Unauthorized Access:**
   - An insider may access sensitive information, databases, or files without proper authorization.
   - This could involve stealing customer data, intellectual property, financial records, or any other confidential information.

2. **Sabotage or Data Destruction:**
   - Insiders with malicious intent might intentionally delete or corrupt data, disrupting business operations.
   - This can result in financial loss, data loss, and damage to the organization's reputation.

3. **Eavesdropping or Wiretapping:**
   - Insiders may use network monitoring tools to capture and analyze network traffic.
   - This allows them to eavesdrop on communications, potentially obtaining sensitive information.

4. **Privilege Abuse:**
   - Insiders may abuse their legitimate access rights to gain unauthorized privileges.
   - This could involve elevating their permissions to access restricted data or perform actions beyond their role.

5. **Insider Trading:**
   - In financial organizations, insiders may use confidential information for personal financial gain through illegal stock trading activities.

6. **Malware Deployment:**
   - Insiders may introduce malware into the network to compromise systems, steal information, or disrupt operations.
   - This could be done through USB devices, email attachments, or other means.

7. **Social Engineering Attacks:**
   - Insiders may use social engineering techniques to manipulate colleagues into divulging sensitive information or performing actions that compromise security.

8. **Password Cracking:**
   - Insiders may attempt to crack passwords to gain unauthorized access to systems or accounts.
   - This could involve using password-cracking tools or techniques to exploit weak password policies.

9. **Data Exfiltration:**
   - Insiders might transfer sensitive data outside the organization's network without detection.
   - This could involve using covert channels or exploiting vulnerabilities to exfiltrate information.

10. **Denial of Service (DoS) Attacks:**
    - Insiders may intentionally flood the network or systems with traffic to overwhelm and disrupt normal operations.

11. **Compromising System Integrity:**
    - Insiders may intentionally compromise the integrity of systems by modifying or replacing critical files or configurations.

Preventing LAN-based insider attacks requires a combination of technical controls, user training, and monitoring. Implementing principles of least privilege, continuous monitoring, access controls, and employee awareness programs are essential components of a comprehensive security strategy to mitigate the risks associated with insider threats.


---------------------------------------------------------------------------------------------------------------------

# ARP Spoofing is used in this attack

ARP (Address Resolution Protocol) poisoning, also known as ARP spoofing, is a network attack in which an attacker sends fake or malicious ARP messages to associate their MAC address with the IP address of a legitimate device on the local network. This manipulation of ARP tables allows the attacker to intercept, modify, or redirect network traffic between two communicating parties.

Here's how ARP poisoning works:

1. **Address Resolution Protocol (ARP):**
   - ARP is used in local area networks to map IP addresses to MAC addresses. Each device on the network maintains an ARP table that maps IP addresses to corresponding MAC addresses.

2. **Normal ARP Operation:**
   - When a device wants to communicate with another device on the same local network, it checks its ARP table. If the MAC address for the target IP address is not found, it sends an ARP request broadcast to the network, asking, "Who has this IP address?"

3. **ARP Poisoning Process:**
   - The attacker, having gained access to the local network, sends fake ARP replies to other devices on the network.
   - In these ARP replies, the attacker falsely claims to be the legitimate owner of a specific IP address, associating their own MAC address with the target IP address.

4. **Consequences of ARP Poisoning:**
   - Once the ARP tables of other devices are poisoned, they start sending their network traffic to the attacker, thinking it is the legitimate device with the claimed IP address.
   - The attacker can intercept, modify, or forward the traffic as desired.

5. **Potential Attacks:**
   - Man-in-the-Middle (MitM) Attack: ARP poisoning is often used to conduct man-in-the-middle attacks, allowing the attacker to eavesdrop on or alter communications between two parties.
   - Session Hijacking: The attacker can hijack sessions by intercepting login credentials or session tokens, gaining unauthorized access to sensitive information.
   - Network Sniffing: ARP poisoning facilitates the capturing and analysis of network traffic, potentially revealing sensitive data.

6. **Detection and Prevention:**
   - ARP poisoning can be detected through network monitoring tools that analyze abnormal ARP traffic patterns.
   - Prevention measures include using static ARP entries, implementing ARP spoofing detection tools, and employing security mechanisms like VLANs and network segmentation.

7. **Countermeasures:**
   - Static ARP Entries: Manually configure static ARP entries on critical devices to prevent dynamic ARP poisoning.
   - ARP Spoofing Detection Tools: Use tools that detect and alert administrators to suspicious ARP activity.
   - Network Segmentation: Segmenting the network into smaller subnets can limit the scope of ARP poisoning attacks.

ARP poisoning is a serious security threat, and organizations should implement measures to detect and mitigate such attacks. Regular network monitoring and security awareness training for users can also help in preventing and responding to ARP poisoning incidents.

## Step:1 

open Kali linux and open the software called ETTERCAP

What is ETTERCAP:
=> Ettercap is a comprehensive suite for man in the middle attacks. It features sniffing of live connections, content filtering on the fly and many other interesting tricks. It supports active and passive dissection of many protocols and includes many features for network and host analysis.

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/f2889659-dad3-4f6f-be22-b9f8bd7f2274)

## Step:2

Turn on the Ettercap and start
![Screenshot_2024-01-28_05_35_01](https://github.com/SuzilSK/Cyber-sec/assets/129137449/b547ac71-efa9-4fd1-aad7-632fbfc4c3bc)

## Step:3 

Check or the no of Host available on the Network in which the adversary is connected
![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/e71ef87f-c3e5-4495-9c36-a0ea12307703)

## Step:4 

Add two Host by clicking ADD to Target 1 and Add to Target 2
Target 1:- Default Gateway
Target 2:- destinated system in which attacker need to implement attact

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/63c982c9-348e-4513-8d0a-b35a14eed520)

## Step:5 

After the Targets system are select implemt ARP Poisoning Attact 
![Screenshot_2024-01-28_06_03_18](https://github.com/SuzilSK/Cyber-sec/assets/129137449/f74b7b33-8db4-4a40-9142-17fd3a554ae1)

## Step:6 

Open a HTTP Web page and give the username and login to the website and observe the login to the web page

## Step:7 

after logging to the website open Ettercap and check for the username and password that the attacked system used to log in to the webpage will be displayed by the MITM attacker or ONpath Attack.
![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/3572c6ce-bed4-4588-bc56-02f94eacf4cf)
