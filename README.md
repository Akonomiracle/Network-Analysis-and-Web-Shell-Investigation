# Network-Analysis-and-Web-Shell-Investigation

## Introduction

A cybersecurity home lab is a controlled environment used to simulate real-world network and security scenarios, allowing for hands-on practice in a safe setting. VirtualBox, an open-source software, enables users to run multiple virtual machines (VMs) on a single host machine, with each VM operating as a separate computer. This setup facilitates safe experimentation with security tools, malware analysis, and network configurations without impacting the host system.

## Objective

The primary objective of this home lab is to create a secure environment for testing cybersecurity concepts and performing activities like malware analysis, threat hunting, and vulnerability assessments. Once configured, the lab can also be used to study network traffic, evaluate security tools, and refine cybersecurity skills through real-world simulations.

### Skills Learned

- Virtualization Management
    - Installing and configuring VirtualBox and managing multiple virtual machines (VMs) independently.
    - Familiarity with different virtualization settings and understanding their impact on VM performance and security.

- Network Configuration
    - Setting up various network modes (NAT, Bridge, Internal Network, Host-Only) in VirtualBox to control connectivity and isolate environments as needed.
    - Practical knowledge of network isolation, essential for malware analysis and secure testing.

- IP Addressing and Network Troubleshooting
    - Assigning static IP addresses to VMs and verifying connectivity using tools like ipconfig and ifconfig.
    - Basic troubleshooting skills to resolve connectivity issues between virtual machines, an important skill for network diagnostics.

- Security Awareness and Isolation Techniques
    - Implementing secure practices, such as using isolated internal networks to prevent potential malware from impacting the host.
    - Understanding how to safely analyze suspicious software in a contained environment, minimizing risk.

### Tools Used

- VirtualBox
- ISO Images for Operating Systems
- Network Utilities

## Steps

#### Step 1: Installing VirtualBox & Virtual Machines

1. Begin by downloading and installing VirtualBox on your host computer, along with virtual machine (VM) ISO image files for your desired operating systems (e.g., Windows, Kali Linux).
    - Ensure that the ISO files are compatible with VirtualBox to prevent installation issues.
2. Load the ISO images into VirtualBox to initialize the VMs.

![Ref 1  installing kali](https://github.com/user-attachments/assets/56ab970a-d8a0-40f8-b229-c6c9381f545b)
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
