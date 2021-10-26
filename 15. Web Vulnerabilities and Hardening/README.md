# Web Vulnerabilities and Hardening

## 1. Command Injection

![1.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/1.1.PNG)
![1.2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/1.2.PNG)

#### Mitigation
- Require Multi-Factor Authentication (strongly recommended for employees with administrative privileges).
- Monitoring employee account log-ins for unusual patterns is a key protection against employee password reuse risk.  Some of the dangers from cyber-attacks arise when unusual patterns of access occur — like repeated logins attempts.

## 2. BWAPP and Brute Force

![2.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/2.1.PNG)
![2.2.0](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/2.2.0.PNG)
![2.2.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/2.2.1.PNG)
![2.3](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/2.3.PNG)

#### Mitigation
Input validation is performed to ensure only properly formed data is entering the workflow in an information system, preventing malformed data from persisting in the database.

-  Input validation should be applied on both **Syntactical** and **Semantic** level.

   - **Syntactic validation** should enforce correct syntax of structured fields (e.g. SSN, date, currency symbol).

   - **Semantic validation** should enforce correctness of their values in the specific business context (e.g. start date is before end date, price is within expected range).

It is always recommended to prevent attacks as early as possible in the processing of the user's (attacker's) request. Input validation can be used to detect unauthorized input before it is processed by the application.

## 3. BeEF and Zombies

![3.1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/3.1.PNG)
![3.2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/3.2.PNG)
![3.3](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/3.3.PNG)

![pluto](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/15.%20Web%20Vulnerabilities%20and%20Hardening/So.%20.%20.%20%20-%20Imgur.gif)
