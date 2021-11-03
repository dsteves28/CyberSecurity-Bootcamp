# CyberSecurity-Bootcamp

## [01. CyberSecurity](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/01.%20CyberSecurity)

### Research on prominent reports, blogs, and research papers.
- Navigating four prominent security reports and answering questions in order to get a basic understanding of the market.

## [02. Governance, Risk, and Compliance](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/02.%20Governance%2C%20Risk%2C%20and%20Compliance)

### This section is about security culture and how to promote it within organizations. 
It’s important that all employees are aware of common security risks and treat security seriously. The majority of cyberattacks aim to exploit human weaknesses with methods like phishing.
For this reason, people are most often the weakest link in an organization’s security defenses.

Step 1. **Measure and Set Goals**

Step 2. **Involve the Right People**

Step 3. **Create a Training Plan** 

## [03. Terminal and Bash](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/03.%20Terminal%20and%20Bash)

### Using command-line skills to navigating, modifying, and analyzing data files.
- Taking the role of a security analyst for the Lucky Duck Casino to uncover the identities of a rogue casino player and dealer colluding to scam Lucky Duck out of thousands of dollars.
  - Analyzing a large database with data on wins and losses, player analysis, and dealer schedules.
  - Preparing several evidence files to assist the prosecution.
  - A summary of the findings for the casino.

## [04. Linux SysAdmin Fundamentals](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/04.%20Linux%20SysAdmin%20Fundamentals)

### Perform a Linux system administration role by covering the foundational knowledge of users, groups, permissions, and access controls.
1. **Ensure Permissions on Sensitive Files** - Inspecting the file permissions of each of the following files. `/etc/shadow` `/etc/gshadow` `/etc/group` `/etc/passwd`
2. **Create User Accounts** - Setting up various users in Linux.
3. **Create User Group and Collaborative Folder** - In Linux create a group, adding users to it, creating a shared group folder, setting the group folder owners for these shared folders.
4. **Lynis Auditing** - Using Lynis to run an audit against the system in order to harden it.
5. **Chrootkit** - Using Chrootkit to see what can be done to harden the system.

## [05. Archiving and Logging Data](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/05.%20Archiving%20and%20Logging%20Data)

### Perform the role of a security analyst in an effort to mitigate network attacks eveloped an efficient log management program that performs:
- Log size management using `logrotate`.
- Log auditing with `auditd` to track events, record the events, detect abuse or unauthorized activity, and create custom reports.      
  - These tools, in addition to archives, backups, scripting, and task automation, contribute to a fully comprehensive log management system.

**Step 1.** **Creating, Extracting, Compressing, and Managing tar Backup Archives** - Creating tar archives; along with extracting and excluding specific files and directories to help speed up your workflow.

**Step 2.** **Creating, Managing, and Automating Cron Jobs** - Creating an archiving and backup scheme to mitigate against malware.

**Step 3.** **Writing Basic Bash Scripts** - Set up multiple backup directories. Each directory will be dedicated to housing text files that you will create with different kinds of system information.

**Step 4.** **Managing Log File Sizes** - Implement log rotation in order to preserve log entries and keep log file sizes more manageable. Also compress logs during rotation to preserve disk space and lower costs.

#### Also Included:
- **Checking for Policy and File Violations** - Create an event monitoring system that specifically generates reports whenever new accounts are created or modified, and when any modifications are made to authorization logs.

- **Performing Various Log Filtering Techniques** - Filtering through log files to determine if a system breach occurred.

## [06. Bash Scripting and Programming](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/06.%20Bash%20Scripting%20and%20Programming)

### Gaining and maintaining access to the target machine by installing a backdoor. Then use the backdoor to crack sensitive passwords.

**Step 1.** Create a "secret" user named sysd. Anyone examining /etc/passwd will assume this is a service account.

**Step 2.** Allow SSH access via port 2222. SSH usually runs on port 22, but opening port 2222 will allow you to log in as your secret sysd user without connecting to the standard (and well-guarded) port 22.

**Step 3.** Test your solution by testing the new backdoor SSH port.

**Step 4.** Attempt to crack as many passwords as possible with John the Ripper.

## [07. Windows Administration and Hardening](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/07.%20Windows%20Administration%20and%20Hardening)

### Create domain-hardening **Group Policy Objectives (GPOs)** and revisit some PowerShell fundamentals.

1. **Create a GPO: Disable Local Link Multicast Name Resolution (LLMNR)**
   - **Local Link Multicast Name Resolution (LLMNR)** is a vulnerability, so we will be disabling it on Windows 10.
      - LLMNR is a protocol used as a backup (not an alternative) for DNS in Windows.
      - When Windows cannot find a local address (e.g. the location of a file server), it uses LLMNR to send out a broadcast across the network asking if any device knows the address.
      - LLMNR’s vulnerability is that it accepts any response as authentic, allowing attackers to poison or spoof LLMNR responses, forcing devices to authenticate to them.
      - An LLMNR-enabled Windows machine may automatically trust responses from anyone in the network.
      - Turning off LLMNR will prevent our Windows machine from trusting location responses from potential attackers.

2. **Create a GPO: Account Lockout**
   - An account lockout disables access to an account for a set period of time after a specific number of failed login attempts. 
     - This policy defends against brute-force attacks, in which attackers can enter a million passwords in just a few minutes.

3. **Create a GPO: Enabling Verbose PowerShell Logging and Transcription**
   - PowerShell is often used as a living off the land hacker tool. 
     - Once a hacker gains access to a Windows machine, they will leverage built-in tools, such as PowerShell and wmic, as much as possible to achieve their goals while trying to stay under the radar.

   - So why not just completely disable PowerShell?
     - Many security tools and system administration management operations, such as workstation provisioning, require heavy use of PowerShell to set up machines.

   - A PowerShell practice that is recommended regardless of whether PowerShell is enabled or disabled: **Enabling enhanced PowerShell logging and visibility through verbosity.**
     - This type of policy is important for tools like SIEM and for forensics operations, as it helps combat obfuscated PowerShell payloads.

4. **Create a Script: Enumerate Access Control Lists**
   - A PowerShell script that will enumerate the Access Control List of each file or subdirectory within the current working directory.
     - In Windows, access to files and directories are managed by Access Control Lists (ACLs). These identify which entities (known as security principals), such as users and groups, can access which resources. ACLs use security identifers to manage which principals can access which resources.

5. **Verifing the PowerShell Logging GPO**
   - A test to verify that the PowerShell logging GPO is working properly.

## [08. Networking Fundamentals](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/08.%20Networking%20Fundamentals)

###

## [09. Networking Fundamentals II](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/09.%20Networking%20Fundamentals%20II)

###

## [11. Network Security](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/11.%20Network%20Security)

###

## [12. Azure Server Map](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/12.%20Network%20Map)

###

## [13. ELK Stack Project](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/13.%20Elk%20Stack%20Project)

###

## [14. Web Development](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/14.%20Web%20Development)

###

## [15. Web Vulnerabilities and Hardening](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/15.%20Web%20Vulnerabilities%20and%20Hardening)

###

## [16. Penetration Testing](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/16.%20Penetration%20Testing)

###

## [17. Penetration Testing Part 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/17.%20Penetration%20Testing%202)

###

## [18. SIEMs](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/18.%20SIEMs)

###

## [19. SIEMs Part 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/tree/main/19.%20SIEMs%20Part%202)

### 