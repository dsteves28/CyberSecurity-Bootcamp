# Splunk Basics

## 1. Determine the impact that the DDOS attack had on download and upload speed. 

### Create a field called ratio that shows the ratio between the upload and download speeds. Then create a report using the Splunk's table command to display the following fields in a statistics report: `_time, IP_ADDRESS, DOWNLOAD_MEGABITS, UPLOAD_MEGABITS, ratio`

#### Splunk Search
![Speedtest search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Speedtest%20search.PNG)

#### Report Table
![Speedtest table](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Speedtest%20table.PNG)

Results: 

## 2. Determine how many critical vulnerabilities exist on the customer data server. 

### Create a report that shows the count of critical vulnerabilities from the customer database server. Then build an alert that monitors every day to see if this server has any critical vulnerabilities.

#### Splunk Search
![Nessus search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20search.PNG)

#### Report
![Nessus Logs Report](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Report.PNG)

#### Alert if any Critical Vunlnerabilites are detected.
![Nessus Logs Alert](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert.PNG)

#### Setting up alert.
![Nessus Logs Alert Edit 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert%20Edit%201.PNG)

![Nessus Logs Alert Edit 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert%20Edit%202.PNG)

## 3. Analyze administrator logs that document a brute force attack.

### Create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring.

#### Splunk Search
![Administrator Logs Search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Search.PNG)

#### Alert for when "An account failed to log on" with a baseline of 30.
![Administrator Logs Alert](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert.PNG)

#### Setting up alert.
![Administrator Logs Alert Edit 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert%20Edit%201.PNG)

![Administrator Logs Alert Edit 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert%20Edit%202.PNG)