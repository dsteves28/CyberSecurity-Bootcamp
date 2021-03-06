# SIEMs (Splunk): Protecting from Future Attacks

 I am assuming the role of an SOC analyst at a small company called Virtual Space Industries (VSI), which designs virtual reality programs for businesses. 

As SOC analysts, I am tasked with using Splunk to monitor against potential attacks on systems and applications.

The task here is to design mitigation strategies to protect VSI from future attacks.


## Part 1: Windows Server Attack

[Windows Server Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/windows_server_logs.csv)

[Windows Server Attack Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/windows_server_attack_logs.csv)

### Section 1

![timechart](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/timechart.PNG)

Splunk Search - `source="windows_server_attack_logs.csv"| timechart count`

Several users were impacted during the attack on March 25th.

![signatures](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/top%20signatures.PNG)

Splunk Search - `source="windows_server_attack_logs.csv"| top limit=20 signature`

Based on the attack signatures, what mitigations would you recommend to protect each user account? 

- Set account lockout policies after a certain number of failed login attempts to prevent credentials from being guessed. Implement CAPTCHA, if lockout is not a viable option.

Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

- Use multi-factor authentication. Where possible, also enable multi-factor authentication on externally facing services.

### Section 2
VSI has insider information that JobeCorp attempted to target users by sending `"Bad Logins"` to lock out every user.

What sort of mitigation could you use to protect against this?

- If failed attempts from a given IP address exceed a threshold, that address can be locked out.
    - Would fail if attacker is using a botnet.

- Use multi-factor authentication.

## Part 2: Apache Webserver Attack:

[Apache Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/apache_logs.txt)

[Apache Attack Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/apache_attack_logs.txt)

### Section 1

Splunk Search - `source="apache_attack_logs.txt" | iplocation clientip | geostats count by uri_path`

![Map](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/Apache%20Attack%20Geo%20Map.PNG)

Based on the geographic map, recommend a firewall rule that the networking team should implement.
Provide a "plain english" description of the rule.

- Block all incoming HTTP traffic where the source IP comes from the country of Ukraine.

![Close_up_map](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/Map%20close%20up.PNG)


### Section 2

VSI has insider information that attackers will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule I just created.


What other rules can you create to protect VSI from attacks against your webserver?

- Set a threshold on the number of tries an IP can get before it is lockout for a time.

- Use multi-factor authentication.

- Block all HTTP POSTS where the byte size is 65748, it is a DDoS attack / botnet.

.

![neat](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/neat.gif)

![badgifs](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/your%20gifs%20are%20bad.gif)

![sad](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/I%20made%20myself%20sad.gif)