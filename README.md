# Network-Analysis-and-Web-Shell-Investigation

## Introduction

In cybersecurity, internal threats can be as dangerous as external ones, and understanding how to analyze network traffic is a critical skill. This lab simulates a real-world scenario where an alert is triggered for unusual internal activity, and the task is to investigate whether the behavior is malicious. The focus of this analysis is to examine network traffic using Wireshark, identify patterns, and determine the intent behind the observed activities.

## Scenario

The SOC received an alert in their SIEM for 'Local to Local Port Scanning' where an internal private IP began scanning another internal system. Your task is to investigate the provided PCAP file using any tools available to determine if this activity is malicious or authorized.

### Skills Learned

- Network Traffic Analysis
    - Investigating PCAP files for anomalies such as port scans, unauthorized access attempts, and lateral movement.
    - Leveraging Wireshark’s features, including protocol hierarchies and TCP stream reconstruction, to identify key activities in network traffic.

- Incident Response Techniques
    - Identifying the use of common attacker tools like Gobuster and SQLmap.
    - Recognizing patterns of malicious behavior, such as web shell uploads and unauthorized command execution.

- Report Writing
    - Documenting findings to create actionable intelligence for Security Operations Centers (SOCs).

### Tools Used

- Wireshark
- URL Decoder

## Steps

#### Step 1: Investigating PCAP File Properties

1. Opened the PCAP file in Wireshark and accessed the file properties via the Statistics menu.
2. Verified the capture date and duration: February 7, 2021, over a 15-minute span.
3. Confirmed that the provided PCAP matched the alert timeline, ensuring accurate analysis.

![Ref 2  time frame](https://github.com/user-attachments/assets/485203e2-4419-4fbf-b6c0-6cc5764c3a17)
Ref 1. Investigating PCAP File Properties.


#### Step 2: Analyzing Protocol Hierarchies
1. Identified active protocols:
    - SSH
    - DNS
    - HTTP
    - SMB
2. These protocols indicated potential lateral movement opportunities within the network.

![Ref 3  Protocol Hierarchy](https://github.com/user-attachments/assets/9737a1a9-8d09-4dcf-9926-03f60924043c)
Ref 2. Analyzing Protocol Hierarchies.


#### Step 3: Detecting Port Scanning Activity
1. Examined conversation details under the IPv4 and TCP tabs.
2. Noted that source IP 10.251.96.4 consistently targeted multiple ports on 10.251.96.5, with the same source port (41675) being used repeatedly.
    - This consistent behavior strongly indicated port scanning activity.

![Detecting Port Scanning Activity](https://github.com/user-attachments/assets/88084fba-6521-437b-8f31-3e0563a2795d)
Ref 3. Detecting Port Scanning Activity.


#### Step 4: HTTP Stream Analysis
1. Investigated an HTTP POST request from packet 38.
2. Reconstructed the HTTP stream and discovered a login attempt with credentials:
    - Username: admin
    - Password: Admin@1234
3. Decoded special characters (e.g., %40 → @) to interpret the full password.
4. Observed that the login occurred over HTTP instead of HTTPS, indicating insecure communication.

![Ref 4  Explore post request](https://github.com/user-attachments/assets/04fdd3a4-8485-4557-8e49-6ee4c9d6c294)
Ref 4. Investigated an HTTP POST request.


#### Step 5: Identifying Attack Tools
1. Recognized the use of Gobuster v3.0.1, a directory brute-forcing tool, from the user agent string.
2. Detected SQLmap v1.4.7, an automated SQL injection tool, used for unauthorized database access attempts.
![Ref 6  Exploring a GET request on a packet we notice the user agent as gobuster](https://github.com/user-attachments/assets/ce8aff31-5470-4e2e-8ebc-b3de869f1b03)
Ref 5. Recognized the use of Gobuster v3.0.1

![Ref 8  Noticed another user agent sqlmap](https://github.com/user-attachments/assets/4ded5263-eedb-4171-963f-d4777fd83110)
Ref 6. Detected SQLmap v1.4.7

![Ref 9  An SQL attack following](https://github.com/user-attachments/assets/83ad6804-cbce-4537-8911-24cadead71aa)
Ref 7. An SQL Attack detected

#### Step 6: Web Shell Analysis
1. Analyzed a callback from 10.251.96.5 to 10.251.96.4 on port 4422, which occurred during the attack.
2. Reconstructed the TCP stream to identify the upload of a malicious web shell (db_functions.php).
3. Observed attacker commands executed on the compromised server:
    - whoami, cd, ls: Discovery commands.
    - python: Used to establish a reverse shell.
    - rm db: Attempted file removal.

![Ref 10  successful webshell](https://github.com/user-attachments/assets/c931497d-2e18-46df-8af1-fd02e14ceed2)
Ref 8. Web Shell Analysis

## Practical Applications and Organizational Benefits

#### 1. Threat Detection and Incident Response
SOC teams can use similar techniques to identify malicious activities like port scanning, unauthorized logins, and web shell uploads in their environments.

#### 2. Malicious Tool Recognition
Understanding tools like Gobuster and SQLmap enhances the ability to detect and mitigate automated attacks.

#### 3. Post-Attack Forensics
Reconstructing attacker activity enables organizations to identify vulnerabilities and strengthen defenses.

#### 4. Skill Development
Hands-on analysis of PCAP files provides real-world experience with network monitoring tools and techniques.


## Conclusion 
Through this project, I analyzed malicious network activity, identified attack patterns, and gained valuable experience with incident response. This exercise reinforced the importance of traffic analysis and the ability to detect, investigate, and respond to cybersecurity threats effectively.
