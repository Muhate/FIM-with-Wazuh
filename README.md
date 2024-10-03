# File Integrity Monitoring with Wazuh - Windows and Ubuntu

## Objectivo

O projeto de Segurança de Active Directory teve como objetivo estabelecer um ambiente controlado para simulação e detecção de ataques cibernéticos. O foco principal era ingerir e analisar logs dentro de um sistema de gerenciamento de eventos e informações de segurança (SIEM), gerando telemetria de teste para imitar cenários de ataque do mundo real. Esta experiência prática foi projectada para aprofundar a compreensão da segurança da rede, padrões de ataque e estratégias defensivas. Para a efectivação do laboratório serão usadas as ferramentas Splunk (SIEM), Sysmon, Kali Linux e Atomic Red Team. Nas estações finais serão instalados o Splunk Universal Forwarder e o Sysmon e serão configurados para enviar métricas para o servidor onde estará instalado o Splunk server.

### Habilidades aprendidas

- Compreensão avançada dos conceitos do SIEM e aplicação prática;
- Proficiência em análise e interpretação de logs de sistemas;
- Desenvolvimento de pensamento crítico e competências de resolução de problemas em cibersegurança.

### Ferramentas usadas
[Bullet Points - Remove this afterwards]

- Security Information and Event Management System (SIEM) - Splunk para ingestão e análise de logs;
- Kali Linux e Atomic Red Team para simular ataques do mundo real;
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*



## Project Title: **Building a Home Lab with Wazuh for Security Monitoring**

### 1. **Overview**
   - **Description**: This project involved setting up a home lab environment using Wazuh as a Security Information and Event Management (SIEM) tool. The goal was to monitor security events, analyze logs, and improve overall security posture.
   - **Objectives**:
     - To learn how to deploy and configure Wazuh.
     - To integrate Wazuh with the Elastic Stack for enhanced data visualization.
     - To set up alerts and notifications for security events.

### 2. **Tools and Technologies Used**
   - **Wazuh**: SIEM tool for log management and security monitoring.
   - **Elastic Stack**: Comprising Elasticsearch, Logstash, and Kibana for data storage and visualization.
   - **VirtualBox**: Used for creating virtual machines for the lab environment.
   - **Kali Linux**: Penetration testing distribution used to generate test logs.

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

