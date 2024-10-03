# File Integrity Monitoring with Wazuh - Windows and Ubuntu

## Description

This home lab project focuses on implementing File Integrity Monitoring (FIM) using Wazuh, an open-source security monitoring solution. The FIM will be implemented for Windows Server 2022 and Ubuntu 24.04. FIM is crucial for maintaining the security and integrity of files on systems by detecting unauthorized changes, which could indicate potential security breaches or system tampering


### Objectives

- Set up a Wazuh server to collect and analyze security data.
- Set up and configure agents on target systems (Windows and Ubuntu) to monitor specific files and directories for changes.
- Implement alerting mechanisms to notify administrators of any detected file changes.
- Generate reports to track changes over time and assess compliance with security policies.


### Tools and Technologies Used

- **VirtualBox**: Used for creating virtual machines for the lab environment.
- **Wazuh**: SIEM tool for log management and security monitoring;
- **Windows Server 2022**: Used as a monitored system;
- **Ubuntu Server 24.04 LTS**: Used as a monitored system.


### 3. **Lab Setup**
   - **Environment Diagram**: 
     - (Include a diagram showing the network layout of your lab setup with all VMs and their connections.)

   - **Components**:
     - **Wazuh Manager**: Centralized management console.
     - **Elasticsearch**: For data indexing and storage.
     - **Kibana**: For visualizing and analyzing data.
     - **Agent Nodes**: Installed on target systems (e.g., a Kali Linux VM) to collect logs.

### 4. **Installation Steps**
   - **Step 1: Setting Up Virtual Machines**
     - Create VMs using VirtualBox for Wazuh Manager, Elasticsearch, Kibana, and Kali Linux.
     - Allocate necessary resources (CPU, RAM, etc.) for each VM.

   - **Step 2: Installing Wazuh Manager**
     - Update the package manager:
       ```bash
       sudo apt-get update
       ```
     - Install Wazuh Manager:
       ```bash
       curl -s https://packages.wazuh.com/4.x/ubuntu/KEY.gpg | sudo apt-key add -
       echo "deb http://packages.wazuh.com/4.x/ubuntu/ focal main" | sudo tee /etc/apt/sources.list.d/wazuh.list
       sudo apt-get update
       sudo apt-get install wazuh-manager
       ```

   - **Step 3: Configuring Wazuh**
     - Modify the configuration file (`/var/ossec/etc/ossec.conf`) to set up agents and alerts.
     - Restart Wazuh Manager:
       ```bash
       sudo systemctl restart wazuh-manager
       ```

   - **Step 4: Installing Elasticsearch and Kibana**
     - Follow similar steps to install and configure Elasticsearch and Kibana.

### 5. **Generating Test Data**
   - **Kali Linux Testing**: 
     - Execute various tests to generate logs (e.g., using Metasploit, Nmap).
     - Sample command to generate logs:
       ```bash
       nmap -sS -p 1-65535 <target_ip>
       ```

### 6. **Results and Analysis**
   - **Data Visualization**: 
     - Showcase screenshots of dashboards in Kibana that display security events, logs, and alerts.
   - **Alerts Configuration**:
     - Explain how alerts were configured in Wazuh and provide examples of alerts generated during testing.

### 7. **Challenges and Solutions**
   - **Challenge**: Difficulty in integrating Wazuh with Elastic Stack.
     - **Solution**: Consulted official documentation and community forums, which helped resolve configuration issues.

### 8. **Lessons Learned**
   - Gained hands-on experience in setting up a complete SIEM solution.
   - Improved understanding of log analysis and incident response workflows.

### 9. **Future Improvements**
   - Plan to integrate additional data sources (e.g., firewalls, web servers).
   - Explore automated incident response mechanisms using Wazuh.

### 10. **Conclusion**
   - This project successfully demonstrated the deployment of Wazuh in a lab environment, providing valuable insights into security monitoring and log analysis.

### 11. **Links and References**
   - [GitHub Repository](https://github.com/username/wazuh-lab)
   - [Wazuh Official Documentation](https://wazuh.com/documentation/)
   - [Elastic Stack Documentation](https://www.elastic.co/guide/en/elastic-stack/current/index.html)

### 12. **Contact Information**
   - **Name**: Rogério Muhate
   - **Email**: rbmuhate@gmail.com
   - **LinkedIn**: [LinkedIn Profile](https://www.linkedin.com/in/rmuhate)

