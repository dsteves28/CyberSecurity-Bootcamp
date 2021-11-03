
# GoodSecurity Penetration Test Report 

## DonaldStephens@GoodSecurity.com

### 10/25/2021
#


    1.0 High-Level Summary

GoodSecurity was tasked with performing an internal penetration test on GoodCorp’s CEO, Hans Gruber. An internal penetration test is a dedicated attack against internally connected systems. The focus of this test is to perform attacks, similar to those of a hacker and attempt to infiltrate Hans’ computer and determine if it is at risk. GoodSecurity’s overall objective was to exploit any vulnerable software and find the secret recipe file on Hans’ computer, while reporting the findings back to GoodCorp.
When performing the internal penetration test, there were several alarming vulnerabilities that were
identified on Hans’ desktop. When performing the attacks, GoodSecurity was able to gain access to his machine and find the secret recipe file by exploit two programs that had major vulnerabilities. The details of the attack can be found in the ‘Findings’ category.

    2.0 Findings

**Machine IP:** 192.168.0.20

**Hostname:** Icecast streaming media services

**Vulnerability Exploited:** Icecast Header Overwrite

**Vulnerability Explanation:** This module exploits a buffer overflow in the header parsing of Icecast versions 2.0.1 and earlier, discovered by Luigi Auriemma. Sending 32 HTTP headers will cause a write one past the end of a pointer array. On win32 this happens to overwrite the saved instruction pointer, and on linux (depending on compiler, etc) this seems to generally overwrite nothing crucial (read not exploitable). This exploit uses ExitThread, this will leave Icecast thinking the thread is still in use, and the thread counter won’t be decremented. This means for each time your payload exits, the counter will be left incremented, and eventually the threadpool limit will be maxed. So you can multihit, but only till you fill the threadpool. 

    Severity Factor

|**Very Severe**| |
|-----------|--|
|Confidentiality Impact|Partial (There is considerable informational disclosure.)|
|Integrity Impact|Partial (Modification of some system files or information is possible, but the attacker does not have control over what can be modified, or the scope of what the attacker can affect is limited.)|
|Availability Impact|Partial (There is reduced performance or interruptions in resource availability.)|
|Access Complexity|Low (Specialized access conditions or extenuating circumstances do not exist. Very little knowledge or skill is required to exploit. )|

## Proof of Concept:

#### Using Metasploit to use the Icecast Header Overwite exploit to gain access to the target machine.
![meta](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/17.%20Penetration%20Testing%202/Metasploit.PNG)

#### After gaining access, you can now search and download files on the target machine.
![meterpreter](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/17.%20Penetration%20Testing%202/meterpreter.PNG)

#### Creating a shell in the target machine and looking at its system information.
![shell](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/17.%20Penetration%20Testing%202/shell.PNG)


    3.0 Recommendations

What recommendations would you give to GoodCorp?

- Update to Icecast 2.0.2 or later. Update all other software. 
  - Set automatic updates for all software, with the option to rollback in case the most recent update is insecere. 
- Encrypt all files/folders that you want to keep a secret
- Set up firewalls with rules to only explicitly allow traffic on needed ports.






.

       Memes


![beautiful](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/17.%20Penetration%20Testing%202/beautiful.gif)

And just because...

![sugerpeas](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/17.%20Penetration%20Testing%202/sugerpeas.gif)