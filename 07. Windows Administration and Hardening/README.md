# Windows System Administration

### 1: Create a GPO: Disable Local Link Multicast Name Resolution (LLMNR)

![1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/1.PNG)

### 2: Create a GPO: Account Lockout

![2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/2.PNG)

### 3: Create a GPO: Enabling Verbose PowerShell Logging and Transcription
- **Local Link Multicast Name Resolution (LLMNR)** is a vulnerability, so we will be disabling it on Windows 10.
      
      - LLMNR is a protocol used as a backup (not an alternative) for DNS in Windows.
      - When Windows cannot find a local address (e.g. the location of a file server), it uses LLMNR to send out a broadcast across the network asking if any device knows the address.
      - LLMNR’s vulnerability is that it accepts any response as authentic, allowing attackers to poison or spoof LLMNR responses, forcing devices to authenticate to them.
      - An LLMNR-enabled Windows machine may automatically trust responses from anyone in the network.
      - Turning off LLMNR will prevent our Windows machine from trusting location responses from potential attackers.

![3.2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.2.PNG)

![3.3](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.3.PNG)

![3.4](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.4.PNG)

![3.5](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/3.5.PNG)

### 4: Create a Script: Enumerate Access Control Lists

![4](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/4.PNG)

### 5: Verify Your PowerShell Logging GPO

![5.0](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/5.0.PNG)

![5.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/5.1.PNG)

![GPO_GC_Computers](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/07.%20Windows%20Administration%20and%20Hardening/GPO%20GC%20Computers.PNG)