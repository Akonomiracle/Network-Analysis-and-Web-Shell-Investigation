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
Ref 1. VirtualBox and VM installation.



#### Step 2: Configuring Virtual Machines (VMs)

1. Set Up Networking: Configure each VM's network settings to manage connectivity, essential for tasks such as malware analysis or network scanning, ensuring these operations do not impact the host machine.
    - Key Network Options in VirtualBox:
        - NAT: Grants VM internet access via the host's network.
        - Bridge Adapter: Connects VMs to the same network as the host, where each VM acts as an independent device.
        - Internal Network: Connects VMs only to each other, isolating them from the host and the internet. Ideal for malware testing and secure communication between VMs.
        - Host-Only Network: Creates a private network between VMs and the host, with no internet access.
        - NAT Network: Similar to NAT, but allows multiple VMs on the same network with internet access.
        - Cloud Network: Connects VMs to the cloud.
        - Not Attached: Disconnects VMs from any network.
2. Preferred Network Configuration: Using the Internal Network is recommended to isolate the VMs from the host and internet, allowing safe internal communication for testing purposes.

![Ref 2  Network list](https://github.com/user-attachments/assets/2e4c13f2-802a-4bd3-b554-6826c4bf0ae7)
Ref 2. Network configurations.


#### Step 3: Assigning IP Addresses to the VMs

1. Windows VM: Assign a static IP address to ensure consistent connectivity during testing.
    - Verify the IP assignment using ipconfig in Command Prompt to confirm accurate network settings.
2. Kali Linux VM: Similarly, assign and check the IP address using ifconfig.
    - Document the IP configurations to maintain consistency and avoid conflicts.
![Ref 3  Assigning windows IP Address](https://github.com/user-attachments/assets/d107fa5c-b112-4690-8beb-13d7021f4e28)
Ref 3. IP assignment for Windows.

![Ref 4  Assigning Kali IP Address](https://github.com/user-attachments/assets/50f84fa5-5568-4a64-a5a1-8bd8fe599125)
Ref 4. IP assignment for Kali Linux.


#### Step 4: Testing Connectivity

1. To test connectivity, I performed a ping test from the Windows VM to the Kali VM, generating network traffic between the two systems. This confirmed that the machines were communicating within the isolated network, ensuring a functional setup for further testing and simulations.

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
