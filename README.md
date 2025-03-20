# SOC Automation Project

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Architecture Overview](#architecture-overview)
- [Setup Environment](#setup-environment)
- [Wazuh Installation](#wazuh-installation)
- [TheHive Installation](#thehive-installation)
- [Cassandra Configuration](#cassandra-configuration)
- [ElasticSearch Configuration](#elasticsearch-configuration)
- [Agent Deployment](#agent-deployment)
- [Security Testing](#security-testing)
- [Troubleshooting](#troubleshooting)
- [Next Steps](#next-steps)

## Introduction
This project builds a comprehensive SOC Automation Lab integrating Wazuh, TheHive, and Shuffle to create a practical Security Operations Center (SOC) environment. It provides hands-on experience with XDR, case management, and SOAR capabilities.

## Prerequisites
- **Hardware Requirements**: 
  - Minimum 8GB RAM recommended
  - 50GB free disk space
  - Processor with virtualization support
- **Software Requirements**:
  - VirtualBox 6.1 or newer
  - Internet connection for downloading components
  - SSH client

## Architecture Overview
![Architecture Diagram](https://github.com/user-attachments/assets/8bea2ae1-99ef-47ce-a56d-aaf786b7118a)

This architecture consists of:
- Wazuh server for security monitoring and detection
- TheHive for case management
- Shuffle for workflow automation
- Windows endpoint for testing and telemetry generation

## Setup Environment

### Step 1: Create Windows VM
1. Open VirtualBox and click "New"
2. Configure the VM with:
   - Name: Windows-Endpoint
   - Type: Microsoft Windows
   - Version: Windows 10 (64-bit)
   - Memory: 4096MB
   - Create a virtual hard disk (VDI, dynamically allocated, 50GB)
3. Mount Windows ISO and install the operating system

![Windows VM Setup](https://github.com/user-attachments/assets/489723f8-f5a5-4f0d-844e-8d6f1eaca9b7)

### Step 2: Create Digital Ocean Droplet
1. Log in to Digital Ocean
2. Click "Create" and select "Droplets"
3. Choose Ubuntu 20.04 LTS
4. Select plan (minimum 4GB RAM / 2 CPUs)
5. Choose a datacenter region
6. Add SSH key
7. Click "Create Droplet"

![Create Droplet](https://github.com/user-attachments/assets/ac474870-079b-45e1-8aae-b2632580d270)

**Verification**: Ensure you can SSH into your droplet using:
```bash
ssh root@your_droplet_ip
```

## Wazuh Installation

### Step 1: Install Wazuh Server
1. SSH into your droplet
2. Update your system:
```bash
apt-get update && apt-get upgrade -y
```

3. Install dependencies:
```bash
apt-get install curl apt-transport-https unzip wget -y
```

4. Download and run Wazuh installation script:
```bash
curl -s https://packages.wazuh.com/4.3/wazuh-install.sh | bash
```

![Wazuh Installation](https://github.com/user-attachments/assets/59e21052-4bf7-40a5-b345-c4baef93635f)

5. Verify installation by accessing the Wazuh dashboard:
   - Open a browser and navigate to `https://your_droplet_ip`
   - Use the credentials from:
   ```bash
   cat /root/wazuh-passwords.txt
   ```

### Step 2: Configure Firewall
1. Allow necessary ports:
```bash
ufw allow 22/tcp
ufw allow 443/tcp
ufw allow 1514/tcp
ufw allow 1515/tcp
ufw allow 55000/tcp
ufw allow 9000/tcp
ufw enable
```

**Verification**: Check Wazuh is running:
```bash
systemctl status wazuh-manager
```

## TheHive Installation

### Step 1: Change Hostname
1. Edit hostname file:
```bash
nano /etc/hostname
```
2. Change to "TheHive"
3. Update hosts file:
```bash
nano /etc/hosts
```
4. Add entry: `your_droplet_ip TheHive`

![Change Hostname](https://github.com/user-attachments/assets/5fd900c5-e111-40de-a725-620bee3a30db)

### Step 2: Install Dependencies
```bash
apt-get install openjdk-11-jre-headless
echo 'deb https://artifacts.elastic.co/packages/7.x/apt stable main' | tee /etc/apt/sources.list.d/elastic-7.x.list
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
apt-get update
apt-get install elasticsearch
```

![Install Dependencies](https://github.com/user-attachments/assets/4940d68c-9057-44f1-8507-a8d1dcbab032)

### Step 3: Install Cassandra
```bash
echo 'deb http://downloads.apache.org/cassandra/debian 311x main' | tee /etc/apt/sources.list.d/cassandra.sources.list
wget -qO - https://downloads.apache.org/cassandra/KEYS | apt-key add -
apt-get update
apt-get install cassandra
```

## Cassandra Configuration

### Step 1: Edit Cassandra Configuration
1. Open configuration file:
```bash
nano /etc/cassandra/cassandra.yaml
```

2. Modify the following settings:
   - Change `listen_address` to your droplet's public IP
   - Change `rpc_address` to your droplet's public IP
   - Update `seeds` provider to include your IP

![Edit Cassandra Config](https://github.com/user-attachments/assets/fdbd7acf-4177-4986-b0e0-0f772b9df1d3)

3. Restart Cassandra:
```bash
systemctl stop cassandra
systemctl start cassandra
```

**Verification**: Check Cassandra status:
```bash
systemctl status cassandra
nodetool status
```

## ElasticSearch Configuration

### Step 1: Configure ElasticSearch
1. Edit configuration:
```bash
nano /etc/elasticsearch/elasticsearch.yml
```

2. Update the following:
```yaml
cluster.name: thehive
node.name: thehive-1
network.host: [your_droplet_ip]
http.port: 9200
cluster.initial_master_nodes: ["thehive-1"]
```

![Configure ElasticSearch](https://github.com/user-attachments/assets/a88adcbf-08fa-4891-bf71-7540cb4748ef)

3. Start ElasticSearch:
```bash
systemctl start elasticsearch
systemctl enable elasticsearch
```

**Verification**: Check ElasticSearch is running:
```bash
curl -X GET http://localhost:9200
```

...

## Security Testing

### Step 1: Download Mimikatz
1. Download Mimikatz on your Windows VM:
```powershell
# Use browser to download or use wget in PowerShell
```

2. Extract the archive
3. Run Mimikatz as administrator:
```cmd
cd c:\path\to\mimikatz
mimikatz.exe
```

![Run Mimikatz](https://github.com/user-attachments/assets/5db7ad67-7213-4331-8a1a-a8787cb2f59c)

### Step 2: Verify Detections
1. In Wazuh dashboard, navigate to Security Events
2. You should see alerts related to Mimikatz execution

![Security Events](https://github.com/user-attachments/assets/65d7b043-9f91-434f-8d06-b4fcd37fb243)

## Troubleshooting

### Common Issues

#### Wazuh Agent Not Connecting
1. Check firewall settings on both server and client
2. Verify agent keys were properly added
3. Restart the Wazuh agent service

#### TheHive Not Starting
1. Check Cassandra is running: `systemctl status cassandra`
2. Check ElasticSearch is running: `systemctl status elasticsearch`
3. Check TheHive logs: `journalctl -u thehive`

## Next Steps
- Integrate Shuffle for automation workflows
- Create custom detection rules in Wazuh
- Set up automated case creation in TheHive
- Implement playbooks for common security incidents
