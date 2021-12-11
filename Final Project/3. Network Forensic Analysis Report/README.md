# Network Analysis
## Time Thieves
At least two users on the network have been wasting time on YouTube. Usually, IT wouldn't pay much mind to this behavior, but it seems these people have created their own web server on the corporate network. So far, Security knows the following about these time thieves:
- They have set up an Active Directory network.
- They are constantly watching videos on YouTube.
- Their IP addresses are somewhere in the range 10.6.12.0/24.
You must inspect your traffic capture to answer the following questions:

1. What is the domain name of the users' custom site? 
 **frank-n-ted.com**
 
2. What is the IP address of the Domain Controller (DC) of the AD network?
**12.6.12.12**
 ![custom](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/customdomain.PNG)

3. What is the name of the malware downloaded to the 10.6.12.203 machine? 
**June11.dll**
![Getdll](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/GetDll.PNG)


Upload the file to VirusTotal.com. What kind of malware is this classified as?
 **Trojan**
![virustotal](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/virustotal.PNG)
 
## Vulnerable Windows Machines
The Security team received reports of an infected Windows host on the network. They know the following:
Machines in the network live in the range 172.16.4.0/24.
- The domain mind-hammer.net is associated with the infected computer.
- The DC for this network lives at 172.16.4.4 and is named Mind-Hammer-DC.
- The network has standard gateway and broadcast addresses.


Inspect your traffic to answer the following questions:

Find the following information about the infected Windows machine:
- Host name: **Rptterdam-PC.mind-hammer.net**
- IP address: **172.16.4.205**
- MAC address: **00:59:07bo:63:a4**
![infected](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/infectedpc.PNG)

What is the username of the Windows user whose computer is infected?
**matthijs.devries**
 
![username](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/Username.PNG)

What are the IP addresses used in the actual infection traffic?
 
As a bonus, retrieve the desktop background of the Windows host.
Illegal Downloads
IT was informed that some users are torrenting on the network. The Security team does not forbid the use of torrents for legitimate purposes, such as downloading operating systems. However, they have a strict policy against copyright infringement.
- IT shared the following about the torrent activity:
- The machines using torrents live in the range 10.0.0.0/24 and are clients of an AD domain.
- The DC of this domain lives at 10.0.0.2 and is named DogOfTheYear-DC.
- The DC is associated with the domain dogoftheyear.net.

Your task is to isolate torrent traffic and answer the following questions:

Find the following information about the machine with IP address 10.0.0.201:
- MAC address: **00:16:17:18:66:c8**
- Windows username: **elmer.blanco**
- OS version **Windows 10**

![blanco](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/blancousername.PNG)

![os](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/os.PNG)

Which torrent file did the user download?
**Betty_Boop_Rythm_on_the_Reservation.avil**

![download](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/3.%20Network%20Forensic%20Analysis%20Report/Download.PNG)