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

## Practical Applications and Organizational Benefits

#### 1. Risk-Free Testing Environment:
A well-structured virtual lab provides a safe environment for analyzing malware, understanding its behavior, and studying indicators of compromise without risking real-world systems. 

#### 2. Network Security Protocols and Configurations:
In a professional setting, these skills translate to efficient management of firewalls, secure network designs, and troubleshooting network issues to prevent unauthorized access.

#### 3. Cybersecurity Training and Skill Development:
The ability to simulate real-world attacks, practice defensive strategies, and refine response tactics benefits organizations by ensuring their security teams are well-prepared for emerging threats.

#### 4. Cost-Effective Solution for Cybersecurity Skills Development:
Virtual labs are highly cost-effective, requiring minimal physical hardware and infrastructure. By adopting similar lab setups, organizations can train their teams in the latest cybersecurity tools and techniques while minimizing costs.

#### 5. Practical Experience with Cybersecurity Tools and Techniques:
From IP address management to traffic monitoring and network configurations, this project has provided hands-on experience with essential cybersecurity tools and practices.

## Conclusion 
By implementing a home lab environment, I have developed a robust foundation in cybersecurity principles, network management, and virtual environment configurations, which are crucial for protecting modern organizations against cyber threats.
