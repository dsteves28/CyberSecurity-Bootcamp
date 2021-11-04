# Windows System Administration

### 1: Create a GPO: Disable Local Link Multicast Name Resolution (LLMNR)
- **Local Link Multicast Name Resolution (LLMNR)** is a vulnerability, so we will be disabling it on Windows 10. 
    - LLMNR is a protocol used as a backup (not an alternative) for DNS in Windows.
      - When Windows cannot find a local address (e.g. the location of a file server), it uses LLMNR to send out a broadcast across the network asking if any device knows the address.
    - LLMNR’s vulnerability is that it accepts any response as authentic, allowing attackers to poison or spoof LLMNR responses, forcing devices to authenticate to them.
      - An LLMNR-enabled Windows machine may automatically trust responses from anyone in the network.
    - Turning off LLMNR will prevent the Windows machine from trusting location responses from potential attackers.

![1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/1.PNG)

### 2: Create a GPO: Account Lockout
   - An account lockout disables access to an account for a set period of time after a specific number of failed login attempts. 
     - This policy defends against brute-force attacks, in which attackers can enter a million passwords in just a few minutes.

![2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/2.PNG)

### 3: Create a GPO: Enabling Verbose PowerShell Logging and Transcription
   - PowerShell is often used as a living off the land hacker tool. 
     - Once a hacker gains access to a Windows machine, they will leverage built-in tools, such as PowerShell and wmic, as much as possible to achieve their goals while trying to stay under the radar.

   - So why not just completely disable PowerShell?
     - Many security tools and system administration management operations, such as workstation provisioning, require heavy use of PowerShell to set up machines.

   - A PowerShell practice that is recommended regardless of whether PowerShell is enabled or disabled: **Enabling enhanced PowerShell logging and visibility through verbosity.**
     - This type of policy is important for tools like SIEM and for forensics operations, as it helps combat obfuscated PowerShell payloads.

![3.2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.2.PNG)

![3.3](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.3.PNG)

![3.4](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.4.PNG)

![3.5](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.5.PNG)

### 4: Create a Script: Enumerate Access Control Lists
   - A PowerShell script that will enumerate the Access Control List of each file or subdirectory within the current working directory.
        - In Windows, access to files and directories are managed by Access Control Lists (ACLs). These identify which entities (known as security principals), such as users and groups, can access which resources. ACLs use security identifers to manage which principals can access which resources.
![4](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/4.PNG)

### 5: Verify the PowerShell Logging GPO

![5.0](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/5.0.PNG)

![5.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/5.1.PNG)

![GPO_GC_Computers](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/GPO%20GC%20Computers.PNG)