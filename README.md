# Sliver-Server-Fun
C&C Ubuntu Server

## Objective

This project focused on simulating the daily tasks and challenges SOC Analysts, emphasizing the importance of log analysis, alert triage, and incident response. The aim was to build a foundational skillset in cybersecurity operations, preparing for real-world SOC environments. I decided to have some fun and get adversarial by generating and triggering a C2 payload on a Windows VM. My goal was to detect and block the attack. Mission accomplished ;)

### Skills Showcased

-   **Understanding of Common Attack Vectors:** Deeper knowledge of prevalent attack techniques and their indicators.
-   **Familiarity with Security Frameworks:** Increased understanding of frameworks like MITRE ATT&CK.
-   **Continuous Learning:** Emphasized the importance of staying updated with the latest threats and technologies.
-   **Virtualization and Lab Setup:** Gained even more proficiency in setting up and configuring a virtualized lab environment, including installing and managing virtual machines.
-   **Security Tool Deployment:** Learned to deploy and configure security tools such as Security Onion and LimaCharlie.
-   **Log Ingestion and Analysis:** Developed skills in ingesting logs from various sources and analyzing them to identify potential security incidents.
-   **Endpoint Detection and Response (EDR):** Gained familiarity with EDR concepts and practical experience in monitoring endpoint activity and detecting threats.
-   **Basic Incident Response:** Developed foundational incident response skills by practicing the initial steps of incident handling, such as identifying, analyzing, and documenting security incidents.
-   **Familiarity with Common Security Concepts:** Gained a better understanding of security concepts like log management, network monitoring, and endpoint security.
-   **Linux Command-Line Proficiency:** Improved Linux command-line skills through various configurations and commands.
-   **Problem-Solving and Troubleshooting:** Enhanced problem-solving and troubleshooting skills by addressing technical challenges and errors encountered during lab setup and tool configuration.

### Tools Used

-   **VMware Workstation:** Used to create and manage the virtual lab environment.
-   **Security Onion:** A Linux distribution designed for network security monitoring, including tools like ELSA (for log management), Suricata (IDS/IPS), and Zeek (network security monitoring).
-   **LimaCharlie:** A cloud-based EDR platform for endpoint monitoring and threat detection.
-   **Acronis:** Another cloud-based EDR platform for endpoint monitoring and threat detection I decided to use. I like their UI better.
-   **Wireshark:** A network protocol analyzer for capturing and inspecting network traffic.
-   **tcpdump:** A command-line packet analyzer for capturing network traffic.
-   **Linux Command-Line Tools:** Used for system administration, log analysis, and network troubleshooting.

## Noteable Steps
Successful ssh from Windows host to Ubuntu VM where the C&C server is.

![Screenshot 2025-02-22 183646](https://github.com/user-attachments/assets/1d5944f1-3c6c-4dbc-b7da-eb0ff6aa51df)

Starting the Sliver HTTP listener to detect the executable.

![Screenshot 2025-02-22 184106](https://github.com/user-attachments/assets/0f7065cf-bc10-4625-999a-23e15b6246b3)

Verifying and dropping into the session within Sliver to get basic info about the session

![Screenshot 2025-02-22 184306](https://github.com/user-attachments/assets/439908c9-4e19-4862-8863-b7192384c500)

Identify running processes on the Windows victim with the "ps -T" command. My process in green and any detected countermeasures (defensive tools) in red.

![Screenshot 2025-02-22 184502](https://github.com/user-attachments/assets/98cb584a-393d-472b-a2f9-595d1875adf8)

Here I'm stealing credentials on the system by dumping the lsass.exe process from memory with the "procdump" command. This will dump the remote process from memory, and save it locally on my Sliver C2 server.

![Screenshot 2025-02-22 184618](https://github.com/user-attachments/assets/0a63c2bf-65bc-4e90-ac5e-4c7894be356c)

Since lsass.exe is a known sensitive process often targeted by credential dumping tools, the EDR generates events and automatically blocks this. Very cool.

![Screenshot 2025-02-20 122933](https://github.com/user-attachments/assets/d5a4f3b9-88c9-459a-ab2f-93d37fbcf2ce)




