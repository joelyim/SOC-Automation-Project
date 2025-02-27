# SOC Automation Project 

## Objective

This project aims to build a SOC Automation Lab that integrates Wazuh, The Hive, and Shuffle to simulate a real-world Security Operations Center (SOC) environment. The goal is to provide hands-on experience with Extended Detection and Response (XDR), case management, and SOAR (Security Orchestration, Automation, and Response) capabilities.

### Skills Learned

- Understanding how Security Operations Centers (SOCs) function and implementing automation to streamline workflows.
- Configuring Wazuh to detect security threats and respond effectively.
- Using The Hive for organizing and tracking security incidents.
- Implementing Shuffle to automate security processes and improve efficiency.
- Monitoring network activity and analyzing logs to detect potential security threats.
  
### Tools Used

- VirtualBox: Virtualization platform for creating and managing virtual machines.
- Wazuh: Open-source SIEM and security monitoring platform for log analysis and intrusion detection.
- The Hive: Case management system for organizing and tracking security incidents.
- Shuffle: SOAR (Security Orchestration, Automation, and Response) tool for automating security workflows.
- Mimikatz: Tool used to generate security telemetry for testing detection capabilities.
  
## Steps

*Ref 1: Logical Diagram*

<img src="https://github.com/user-attachments/assets/8bea2ae1-99ef-47ce-a56d-aaf786b7118a" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 2: Install Windows and create Droplet*

<img src="https://github.com/user-attachments/assets/489723f8-f5a5-4f0d-844e-8d6f1eaca9b7" width="400"/> <img src="https://github.com/user-attachments/assets/ac474870-079b-45e1-8aae-b2632580d270" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 3: Create Wazuh and install TheHive*

<img src="https://github.com/user-attachments/assets/59e21052-4bf7-40a5-b345-c4baef93635f" width="400"/> <img src="https://github.com/user-attachments/assets/1ee75037-d01f-4f24-a64c-9a9c5e4e77d9" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 4: Added Dropet*

<img src="https://github.com/user-attachments/assets/6fb03c58-85d4-428f-a9ef-524f83df43b9" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 5: Apt-get on Wazuh Root*

<img src="https://github.com/user-attachments/assets/6c8bd523-0725-4ae3-b9a1-038f51ebcb54" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 6: Run the following commands below*

<img src="https://github.com/user-attachments/assets/e3432273-3669-40c4-89fc-89c791920413" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 7: Run IPv4 on Wazuh*

<img src="https://github.com/user-attachments/assets/33bbc418-91bc-402c-814d-2d03947f7333" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 8: Change Hostname to "TheHive"*

<img src="https://github.com/user-attachments/assets/5fd900c5-e111-40de-a725-620bee3a30db" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 9: Install all modules below*

<img src="https://github.com/user-attachments/assets/4940d68c-9057-44f1-8507-a8d1dcbab032" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 10: Commands for installation process*

<img src="https://github.com/user-attachments/assets/bd69eb37-d88b-42df-9c0a-3a1a37f501b8" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 11: Edit Cassandras Config File on TheHive*

<img src="https://github.com/user-attachments/assets/23494121-0ead-44c3-b41c-00186bed0e5b" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 12: Change Listening Address to TheHives public IP address*

<img src="https://github.com/user-attachments/assets/fdbd7acf-4177-4986-b0e0-0f772b9df1d3" width="400"/>

<br><br> <!-- Adds extra space between sections -->

*Ref 13: Change RPC address as well*

<img src="https://github.com/user-attachments/assets/d2d959f1-c5aa-42c4-b8b4-618df1f70021" width="400"/>

<br><br>

*Ref 14: Change Seed Provider*

<img src="https://github.com/user-attachments/assets/ad680eaf-34fe-4e4e-a6f5-b070fc564b33" width="400"/>

<br><br>

*Ref 15: Stop and Restart Cassandra (Important to restart each configuration after a change)*

<img src="https://github.com/user-attachments/assets/513049a9-ed90-4da1-8d8b-c6d8b6043ef6" width="400"/>

<br><br>

*Ref 16: Run Elastic Search to manage Indices*

<img src="https://github.com/user-attachments/assets/6abbde78-3efd-41fd-839b-15970c338537" width="400"/>

<br><br>

*Ref 17: Change Local Host IP address and remove a comment for the cluster to start Elastic*

<img src="https://github.com/user-attachments/assets/a88adcbf-08fa-4891-bf71-7540cb4748ef" width="400"/>

<br><br>

*Ref 18: Run ElasticSearch*

<img src="https://github.com/user-attachments/assets/2cd06833-350c-42fe-bfc8-95961ae08c58" width="400"/>

<br><br>

*Ref 19: Change Owner of Hive*

<img src="https://github.com/user-attachments/assets/04d659a4-5636-43bc-847d-8f9a64c5078f" width="400"/>

<br><br>

*Ref 20: Change Hostname of Hive*

<img src="https://github.com/user-attachments/assets/b7c1937b-0d68-4a45-af1f-e38dcef43fb3" width="400"/>

<br><br>

*Ref 21: Start and enable TheHive*

<img src="https://github.com/user-attachments/assets/11295ca9-9339-4f1b-8659-aba5b761dd73" width="400"/>

<br><br>

*Ref 22: Run TheHive through its public IP address followed by port 9000*

<img src="https://github.com/user-attachments/assets/90cad546-daf7-487d-a712-f11cb9a2c0a6" width="400"/>

<br><br>

*Ref 23: Install TAR and find passwords on Wazuh*

<img src="https://github.com/user-attachments/assets/7991a898-5073-4c3e-90e2-4256a0318c8d" width="400"/>

<br><br>

*Ref 24: Deploy New Agent on Wazuh and assign Wazuh's public IP address*

<img src="https://github.com/user-attachments/assets/50072b7e-5ec9-4bfc-bb8c-03677937c4a2" width="400"/>

<br><br>

*Ref 25: Run commands on Powershell to start Wazuh*

<img src="https://github.com/user-attachments/assets/0323c603-6b63-4079-9e00-fb14cd9f03b1" width="400"/>

<br><br>

*Ref 26: New Agent Deployed*

<img src="https://github.com/user-attachments/assets/7750f27e-aed2-4b04-bcb1-90289a8f78b7" width="400"/>

<br><br>

*Ref 27: Head over to the Security Module to query events*

<img src="https://github.com/user-attachments/assets/5d0a14db-21a3-45ae-820b-4c81c683cdd2" width="400"/>

<br><br>

*Ref 28: Change Ossec Agent File*

<img src="https://github.com/user-attachments/assets/fb6fd581-883d-42e0-aa69-734b23260e91" width="400"/>

<br><br>

*Ref 29: Add or Remove Exclusions and select Downloads Folder*

<img src="https://github.com/user-attachments/assets/069669fa-87da-4678-8391-cf29ee47e09f" width="400"/>

<br><br>

*Ref 30: Download MimiKats and Extract ALl*

<img src="https://github.com/user-attachments/assets/45a5a71a-f05a-4efb-ad99-8441817ef283" width="400"/>

<br><br>

*Ref 31: Change Directory to Extracted MimiKatz File and run command*

<img src="https://github.com/user-attachments/assets/5db7ad67-7213-4331-8a1a-a8787cb2f59c" width="400"/>

<br><br>

*Ref 32: You won't see MimiKat alerts so we'll have to change alert behavior on Wazuh*

<img src="https://github.com/user-attachments/assets/34a81932-7315-4b82-9905-5d1a37d9b05a" width="400"/>

<br><br>

*Ref 33: Create a copy in case we need to rollback*

<img src="https://github.com/user-attachments/assets/b431f7c1-dce6-4b6f-9e72-d7047902204c" width="400"/>

<br><br>

*Ref 34: Use Nano command to change log to ALL*

<img src="https://github.com/user-attachments/assets/5efadab4-7930-40bc-90e0-b6cba917a718" width="400"/>

<br><br>

*Ref 35: Check Wazuh for security events*

<img src="https://github.com/user-attachments/assets/65d7b043-9f91-434f-8d06-b4fcd37fb243" width="400"/>

<br><br>












