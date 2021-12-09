# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology
![network map](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/2.%20Blue%20Team%20-%20Summary%20of%20Operations/Final%20Network%20Network%20Map.PNG)

### The following machines were identified on the network:

- Name of VM: Hyper-V Manager (ML-REFVM-684427)
  - **Operating System**: Windows 10
  - **Purpose**: Contains the Capstone, ELK, Kali and Target Machines
  - **IP Address**: 192.168.1.1

- Name of VM: Kali 
  - **Operating System**: Linux
  - **Purpose**: Attacking Machine used for penetration test 
  - **IP Address**: 192.168.1.90 
  - **Open Ports**: 22/tcp-ssh

- Name of VM: ELK Server
  - **Operating System**: Linux 
  - **Purpose**: Elastic Search Database: It holds the Kibana Dashboards
  - **IP Address**: 192.168.1.100
  - **Open Ports**: 22/tcp-ssh and 9200/tcp-http

- Name of VM: Capstone
  - **Operating System**: Linux
  - **Purpose**: Filebeat and Metricbeat are installed and will forward logs to the Elk Machine
  - **IP Address**: 192.168.1.105
  - **Open Ports**: 22/tcp-ssh, 80/tcp-http, 422, 329, 404

- Name of VM: Target 1
  - **Operating System**: Linux 3.2 - 4.9
  - **Purpose**: Exposes a vulnerable WordPress Server
  - **IP Address**: 192.168.1.110
  - **Open Ports**:
    * 22/tcp open ssh
    * 80/tcp open http
    * 111/tcp open rpcbind
    * 139/tcp open netbios-ssn Samba smbd 3/x - 4.X (workgroup: WORKGROUP)
    *445/tcp open netbios-ssn Samba smbd 4.2.14-Debian (workgroup: WORKGROUP)

### Description of Targets

The target of this attack was on Virtual Machine: **Target 1 IP Address 192.168.1.110**

**Target 1** is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

### Name of Alert 1: Excessive HTTP Errors

Alert 1 is implemented as follows:
  - **Metric**: Packetbeat ('http.response.status_code')
  - **Threshold**: WHEN count() GROUPED OVER top 5 'http.response.status_code' IS ABOVE 400 FOR THE LAST 5 minutes
  - **Vulnerability Mitigated**: Brute Force Attacks 
  - **Reliability**: This Alert is High Reliability because it will reduce the number of false positives and alert when a high number of HTTP Error's are present after 5 minutes

### Name of Alert 2: HTTP Response Size Monitor

Alert 2 is implemented as follows:
  - **Metric**: Packetbeat (http.request.bytes)
  - **Threshold**: WHEN sum() of http.request.bytes OVER all documents IS ABOVE 3500 FOR THE LAST 1 minute
  - **Vulnerability Mitigated**: Code Injection attacks (XSS or CRLF)
  - **Reliability**: This is Medium Reliability because some it may generate false positives. There is the possibility that a large, non-malicious HTTP request may trigger the alarm.

#### Name of Alert 3: CPU Usage Monitor

Alert 3 is implemented as follows:
  - **Metric**: Metricbeat (system.process.cpu.total.pct) 
  - **Threshold**: WHEN max() OF system.process.cpu.total.pct OVER all documents IS ABOVE 0.5 FOR THE LAST 5 minutes
  - **Vulnerability Mitigated**: Virus or Malware
  - **Reliability**: This is Low Reliability because this alert will generate a lot of false positives. CPU can spike for several different reasons. 

### Suggestions for Going Further (Optional)
 
- Each alert above pertains to a specific vulnerability/exploit. Recall that alerts only detect malicious behavior, but do not stop it. For each vulnerability/exploit identified by the alerts above, suggest a patch. E.g., implementing a blocklist is an effective tactic against brute-force attacks. It is not necessary to explain _how_ to implement each patch.

The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:

- **Vulnerability 1: Brute Force Attacks** 

  - **Patch: WordPress Hardening**

    * Update WordPress and other software: apt-get upgrade weekly
    * Popular WordPress Plugins: Loginizer, WP Limit Login Attempts, Brute Force Login Protection: These plugins help protect websites from malicious attacks
    * Implement a strong password policy: 12 characters/2 special characters and password reset every 60 days
    * create alerts when when a user has met the "failed login" threshold and lock out the user
    * Implement a Multi-Factor Authentication password reset policy
    * Establish rule to block all known VPN Traffic

  - **Why It Works**: 

    * Updating software weekly typically will automatically fix errors and update patches
    * Plugins help secure the website based on their intended purpose. 
    * Strong password policies help reduce BruteForce Attacks
    * Alerts help notify Cyber Professionals when there is unusual activity like a large amount of HTTP Requests
    * Multi-Factor Authentication is a useful tool to ensure attackers can not gain access to another user's account 
    * Blocking VPN Traffic is one way monitor and identify traffic

- **Vulnerability 2: Code Injection attacks (XSS or CRLF)**

  - **Patch: Code Injection/DDOS Hardening**

    * Update software: apt-get upgrade weekly
    * Restrict PHP and EXE 
    * Establish HTTP Request Limit Rules 
        - Max URL Length
        - Max length of a query string
        - Max size of a request
    
  - **Why It Works**: 

    * Updating software weekly typically will automatically fix errors and update patches
    * Restricting PHP and EXE helps reduce Injection Attacks on the front end
    * Establishing HTTP Request Limit Rules automatically drops traffic when threshold has been met

- **Vulnerability 3: Virus or Malware** 

  - **Patch**: Virus and Malware Hardening

    * Update software: apt-get upgrade weekly
    * Update and install industry standard Anti-Virus Software
    * Implement and Monitor Network using Intrusion Detection System (IDS) 
        - SNORT
        - Kibana
        - Wireshark
        - Nessus
    
  - **Why It Works**: 

     * Updating software weekly typically will automatically fix errors and update patches
     * Installing Anti-Virus Software is critical to any Network Security. Installing Anti-Virus Software is an Industry Standard Practice.
     * IDS is critical for network security because it enables you to detect and respond to malicious traffic