
![D1]()
![D2]()

1. Identify the offensive traffic.

  - Identify the traffic between your machine and the web machine: `source.ip: 192.168.1.90 AND destination.ip: 192.168.1.105`

    - When did the interaction occur? 
      - Nov 11, 2021 @ 00:00:00.000 → Nov 11, 2021 @ 03:00:00.0
    ![1]()
    - What responses did the victim send back? 
      - `401, 301, 207, 404` and `200`
    ![1.2]()
    ![1.2.1]()
    - What data is concerning from the Blue Team perspective? 
      - A spike in the `Connections over time [Packetbeat Flows] ECS`. This is due to `hydra`.
    ![1.3]()
    ![1.3.1]()


2. Find the request for the hidden directory.

- In your attack, you found a secret folder. Let's look at that interaction between these two machines. `source.ip: 192.168.1.90 AND destination.ip: 192.168.1.105 AND url.path: /company_folders/secret_folder/`

  - How many requests were made to this directory? At what time and from which IP address(es)? 
    - 15,225
  ![2.1]()
  - Which files were requested? What information did they contain? 
    - `192.168.1.105/company_folders/secret_folder/connect_to_corp_server`
  - What kind of alarm would you set to detect this behavior in the future? 
    - We could set an alert that goes off for any machine that attempts to access this directory or file.
  - Identify at least one way to harden the vulnerable machine that would mitigate this attack. 
    - This directory and file should be removed from the server all together.



3. Identify the brute force attack.

- After identifying the hidden directory, you used Hydra to brute-force the target server. Answer the following questions:

  - Can you identify packets specifically from Hydra? 
    - Under `user_agent.original Mozzilla/4.0 (Hydra)`
  - How many requests were made in the brute-force attack? How many requests had the attacker made before discovering the correct password in this one? 
    - 15,225
  - What kind of alarm would you set to detect this behavior in the future and at what threshold(s)? 
    - Base of the spikes seen in `Connections over time [Packetbeat Flows] ECS` and `Errors vs successful transactions [Packetbet] ECS`, we could set an alert if `401 Unauthorized` is returned from any server over a certain threshold that would weed out forgotten passwords. Start with 10 in one hour and refine from there.
    - We could also create an alert if the `user_agent.original` value includes `Hydra` in the name.
  ![1.3]()
  ![1.3.1]()
  - Identify at least one way to harden the vulnerable machine that would mitigate this attack.
    - After the limit of 10 `401 Unauthorized` codes have been returned from a server, that server can automatically drop traffic from the offending IP address for a period of 1 hour. We could also display a lockout message and lock the page from login for a temporary period of time from that user.



4. Find the WebDav connection.

- Use your dashboard to answer the following questions:

  - How many requests were made to this directory?
    - The `Top 10 HTTP requests [Packetbeat] ECS` panel shows that the webdav folder was directly connected and files inside were accessed.
  ![2.1]()
  - Which file(s) were requested? 
    - With the `Top 10 HTTP requests [Packetbeat] ECS` panel we can see the passwd.dav and shell.php file were requested.
  - What kind of alarm would you set to detect such access in the future? 
    - We can create an alert anytime this directory is accessed by a machine other than the machine that should have access.
  - Identify at least one way to harden the vulnerable machine that would mitigate this attack.
    - Connections to this shared folder should not be accessible from the web interface.
    - Connections to this shared folder could be restricted by machine with a firewall rule.



5. Identify the reverse shell and meterpreter traffic.

- To finish off the attack, you uploaded a PHP reverse shell and started a meterpreter shell session. Answer the following questions:

  - Can you identify traffic from the meterpreter session?
    -  `Port 4444` is the default port used for meterpreter and the port used in all of their documentation. Because of this, many attackers forget to change this port when conducting an attack.
    - `source.ip: 192.168.1.105 and destination.port: 4444`
  - What kinds of alarms would you set to detect this behavior in the future?
    - We can set an alert for any traffic moving over port 4444.
    - We can set an alert for any .php file that is uploaded to a server.
  - Identify at least one way to harden the vulnerable machine that would mitigate this attack.
    - Removing the ability to upload files to this directory over the web interface would take care of this issue.