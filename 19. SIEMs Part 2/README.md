# SIEMs (Splunk): Protecting from Future Attacks

 I am assuming the role of an SOC analyst at a small company called Virtual Space Industries (VSI), which designs virtual reality programs for businesses. 

As SOC analysts, I am tasked with using Splunk to monitor against potential attacks on systems and applications.

The task here is to design mitigation strategies to protect VSI from future attacks.


## Part 1: Windows Server Attack

[Windows Server Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/windows_server_logs.csv)

[Windows Server Attack Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/windows_server_attack_logs.csv)

### Section 1
Several users were impacted during the attack on March 25th.

Based on the attack signatures, what mitigations would you recommend to protect each user account? 

- 

Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

- 

### Section 2
VSI has insider information that JobeCorp attempted to target users by sending `"Bad Logins"` to lock out every user.

What sort of mitigation could you use to protect against this?

- 


## Part 2: Apache Webserver Attack:

[Apache Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/apache_logs.txt)

[Apache Attack Logs File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/apache_attack_logs.txt)

### Section 1

Based on the geographic map, recommend a firewall rule that the networking team should implement.
Provide a "plain english" description of the rule.

- 

For example: "Block all incoming HTTP traffic where the source IP comes from the city of Los Angeles."

Provide a screen shot of the geographic map that justifies why you created this rule.

- 


### Section 2

VSI has insider information that attackers will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule I just created.


What other rules can you create to protect VSI from attacks against your webserver?

- 

Conceive of two more rules in "plain english".

- 

Hint: Look for other fields that indicate the attacker.





![neat](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/neat.gif)

![badgifs](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/your%20gifs%20are%20bad.gif)

![sad](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/19.%20SIEMs%20Part%202/I%20made%20myself%20sad.gif)