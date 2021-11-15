# Splunk Basics

## 1. Determine the impact that the DDOS attack had on download and upload speed. 

[Speed Test File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/server_speedtest.csv)

### Create a field using `eval` called `ratio` that shows the ratio between the upload and download speeds. Then create a report using the Splunk's table command to display the following fields in a statistics report: `_time, IP_ADDRESS, DOWNLOAD_MEGABITS, UPLOAD_MEGABITS, ratio`.  

#### Splunk Search 

`source="server_speedtest.csv" | eval ratio = 'DOWNLOAD_MEGABITS'  / 'UPLOAD_MEGABITS' | table _time IP_ADDRESS DOWNLOAD_MEGABITS UPLOAD_MEGABITS ratio`

![Speedtest search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Speedtest%20search.PNG)

#### Report Table
![Speedtest table](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Speedtest%20table.PNG)

**Results:**

Worst effects were at 2020-02-23 14:30:00 2020-02-23 till. 18:30:00 2020-02-23. Started to recover at 2020-02-23 20:30:00. Full recovery at 2020-02-23 23:30:00.

Worst effects lasted 4 hours. System started to recover after 6 hours. Full recovery after 9 hours.

## 2. Determine how many critical vulnerabilities exist on the customer data server. 

[Nessus Scan Results File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/nessus_logs.csv)

### Create a report that shows the count of critical vulnerabilities from the customer database server. Then build an alert that monitors every day to see if this server has any critical vulnerabilities.

#### Splunk Search

`source="nessus_logs.csv" severity=critical dest_ip="10.11.36.26"| top limit=20 severity`

![Nessus search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20search.PNG)

#### Report
![Nessus Logs Report](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Report.PNG)

#### Alert if any Critical Vunlnerabilites are detected.
![Nessus Logs Alert](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert.PNG)

#### Setting up alert.
![Nessus Logs Alert Edit 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert%20Edit%201.PNG)

![Nessus Logs Alert Edit 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Nessus%20Logs%20Alert%20Edit%202.PNG)

## 3. Analyze administrator logs that document a brute force attack.

[Admin Logins File](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator_logs.csv)

### Create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring.

#### Splunk Search

`source="Administrator_logs.csv" name="An account failed to log on"`

![Administrator Logs Search](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Search.PNG)

#### Alert for when "An account failed to log on" with a baseline of 30.
![Administrator Logs Alert](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert.PNG)

#### Setting up alert.
![Administrator Logs Alert Edit 1](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert%20Edit%201.PNG)

![Administrator Logs Alert Edit 2](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/Administrator%20Logs%20Alert%20Edit%202.PNG)

**Results:** 

Brute force started at 8 am on Friday, February 21, 2020. Lasted for 6 hours till 2 pm on Friday, February 21, 2020.

The End!

![thumbs_up](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/thumbs%20up%20computer.gif)

![spider](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/18.%20SIEMs/spider.gif)