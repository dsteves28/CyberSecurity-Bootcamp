# Penetration Testing 1

## 1. Google Dorking

- Karl Fitzgerald (Chief Executive Officer of Altoro Mutual)
   - Someone with possible admin privileges. Knowing their name can be used to determine a username and to look up other info about them.

## 2. DNS and Domain Discovery

1. NetRange: 65.61.137.64 - 65.61.137.127
2. Demo.testfire.net Location - Sunnyvale, CA, 94085
3. Infrastructure Location - Rackspace Backbone Engineering. 9725 Datapoint Drive, Suite 100, San Antonio, TX, 78229
4. 65.61.137.117

## 3. Shodan

- **Open Ports** of the DNS server for `demo.testfire.net` - 80 HTTP, 443 HTTPS, 8080 HTTP-Proxy 
- **Services:** Apache Tomcat/Coyote JSP Engine (version 1.1)

## 4. Recon-ng

![recon](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/recon.PNG)
![reconreport](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/16.%20Penetration%20Testing/reconreport.PNG)

Conclusion: Altoro Mutual is vulnerable to XSS.

## 5. Zenmap

