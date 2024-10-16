# File Integrity Monitoring with Wazuh - Windows and Ubuntu

### 1. Description

This home lab project focuses on implementing File Integrity Monitoring (FIM) using Wazuh, an open-source security monitoring solution. The FIM will be implemented for Windows Server 2022 and Ubuntu 24.04. FIM is crucial for maintaining the security and integrity of files on systems by detecting unauthorized changes, which could indicate potential security breaches or system tampering


### 2. Objectives

- Set up a Wazuh server to collect and analyze security data.
- Set up and configure agents on target systems (Windows and Ubuntu) to monitor specific files and directories for changes.
- Implement alerting mechanisms to notify administrators of any detected file changes.
- Generate reports to track changes over time and assess compliance with security policies.


### 3. Tools and Technologies Used

- **VirtualBox**: Used for creating virtual machines for the lab environment.
- **Wazuh**: SIEM tool for log management and security monitoring;
- **Windows Server 2022**: Used as a monitored system;
- **Ubuntu Server 24.04 LTS**: Used as a monitored system.


### 4. Lab Setup
   - **Network Diagram**:
   
The diagram below illustrates how the components will be interconnected all together, along with their description and IP addresses details.

<p align="center">
<img width="300" alt="Network Diagram" src="https://github.com/user-attachments/assets/d4e4da42-b979-432c-a39f-8d0aa15bf3a8">
</p>

   - **Components**:
     - **Wazuh Manager**: Centralized management console.
     - **Agent Nodes**: Installed on target systems (Windows and Ubuntu Servers) to collect logs.

### 5. Installation Steps
   - **5.1. Setting Up VirtualBox**

For setting up VirtualBox, refer to <a href="https://github.com/Muhate/Setting-Up-VirtualBox">this guide</a>
<br>
<br>
   
   - **5.2: Setting Up Windows 2022 on VirtualBox**

For setting up Windows 2022 on VirtualBox, refer to <a href="https://github.com/Muhate/Install-Windows-on-VirtualBox">this guide</a>
<br>
<br>

   - **5.3: Setting Up Ubuntu Server 24.04.LTS on VirtualBox**

For setting up Ubuntu Server on VirtualBox, refer to <a href="https://github.com/Muhate/Install-Ubuntu-on-VirtualBox">this guide</a>
<br>
<br>

   - **5.4: Setting Up Wazuh Manager on Ubuntu Server 24.04 LTS**

     - After logging into the server, update the package manager:
       ```
       sudo apt update && sudo apt upgrade -y && sudo reboot
       ```
     - Install Wazuh Manager and all other components:
       ```
       curl -sO https://packages.wazuh.com/4.9/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
       ```
       
   - **5.5: Deploy agent on Windows Server 2022**
     
     - After logging into the wazuh dashboard, deploy the agent following the steps indicated in the image below and then hit the button **Deploy new agent**:

<p align="center">
<img width="643" alt="Agent deployment" src="https://github.com/user-attachments/assets/075b542a-1a3e-400e-95ce-61b0e59aed0f">
</p>

After clicking the **Deploy new agent** button, choose the operating system and fill all the details asked in the following screen as shown in the images below:

<p align="center">
<img width="643" alt="details filled" src="https://github.com/user-attachments/assets/25feca57-5086-4d69-93db-4a9a0d366562">
</p>

After running all the given commands on your windows machine, click the **Close** button and check for the connectivity between the manager and the agent, the screen should look like the image below.

<p align="center">
<img width="643" alt="Agent showing in the manager" src="https://github.com/user-attachments/assets/f0bde5d7-4bd3-45d4-b328-493762fbce9b">
</p>

If not showing as **active** wait for some minutes and refresh the page.

   - **5.6: Configure the agent to monitor the files or folders you intend to moniotr**
Now that we already deployed the agent, let configure it. The configurations will be made on the file **ossec.conf** located at **C:\Program Files (x86)\ossec-agent**. Before we change any configuration on it, it is a best practice to make a backup of the file, so copy and rename the file so that anything going wrong we can be able to revert to our functional version. For this demonstration we will be monitoring the folder **C:\Users\Public**, but you are free to choose another directory. So locate the section with **File integrity monitoring** and add the content below inside of that:

       ```
       <directories check_all="yes" whodata="yes" report_changes="yes">C:\Users\Public</directories>
       ```

After editing the configuration file, save it and restart the agent. Go to **seacrh bar**, type **services** and hit **ENTER**. Locate the service called **wazuh**, right click on it and choose **restart**, or on powerShell run the below commands:

       ```
       NET STOP WazuhSvc
       NET START WazuhSvc
       ```
After that, check if is there any event on the manager, following the steps shown in the image below, then go to **Events**.

<p align="center">
<img width="643" alt="Check events" src="https://github.com/user-attachments/assets/ef71fc09-fa99-4f2e-a1b7-8472940853da">
</p>

If you followed everything from the beginning, you will notice that there is no event triggered, that because we didn't make any modification yet. Let us create a file inside the folder **C:\Users\Public** and check if we will have any event.
Inside, we created one folder and one file, called **Test Folder** and **Test file**, as shown below. Go and see again the **Events** under **File Integrity Monitoring**.

<p align="center">
<img width="421" alt="File and Folder created" src="https://github.com/user-attachments/assets/f254378e-caea-4189-80fa-17047581cc8b">
</p>


Now you can see the changes, see how we can see the file created.

<p align="center">
<img width="643" alt="File created" src="https://github.com/user-attachments/assets/9a5e0f83-be38-43a1-8c5c-db4b3d3b8dc9">
</p>


   - **Step 3: Configuring Wazuh**
     - Modify the configuration file (`/var/ossec/etc/ossec.conf`) to set up agents and alerts.
     - Restart Wazuh Manager:
       ```bash
       sudo systemctl restart wazuh-manager
       ```

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

