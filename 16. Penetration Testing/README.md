# Penetration Testing 1

## 1. Google Dorking

- Karl Fitzgerald (Chief Executive Officer of Altoro Mutual)
   - Someone with possible admin privileges. Knowing their name can be used to determine a username and to look up other info about them.

## 2. DNS and Domain Discovery

1. NetRange: 65.61.137.64 - 65.61.137.127
2. Demo.testfire.net Location - Sunnyvale, CA, 94085
3. Infrastructure Location - Rackspace Backbone Engineering. 9725 Datapoint Drive, Suite 100, San Antonio, TX, 78229
4. DNS server IP Address: 65.61.137.117

## 3. Shodan

- **Open Ports** of the DNS server for `demo.testfire.net` - 80 HTTP, 443 HTTPS, 8080 HTTP-Proxy 
- **Services:** Apache Tomcat/Coyote JSP Engine (version 1.1)

## 4. Recon-ng

#### Using Recon-ng to search for and use module xssed. Then exporting results to html.
![recon](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/recon.PNG)

#### The Report from Recon-ng module xssed (html format).
![reconreport](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/reconreport.PNG)

Conclusion: Altoro Mutual is vulnerable to XSS.

## 5. Zenmap

#### Zenmap Scan Results (nmap -sV 192.168.0.10)
![zen1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/zen1.PNG)

#### Zenmap Output (nmap -sV -oN zenmapscan.txt 192.168.0.10)
![zen2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/zen2.PNG)

#### Zenmap vulnerability script command (nmap --script smb-enum-shares 192.168.0.10)
![]()

- The vulnerability is SMB 3 (Samba)
  - This vulnerability may allow an attacker to upload a shared library, then have the server load and execute it. Completely impacts the CIA triad (system files being shared, loss of system protection, and total shutdown of affected source).

- A **mitigation** solution would be updating the sever and require authentication of all users.

 

 
![yay](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/giphy.gif)