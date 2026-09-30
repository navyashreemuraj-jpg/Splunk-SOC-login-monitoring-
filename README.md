# Splunk-SOC-login-monitoring-

Project Overview
This project demonstrates a basic Security Operations Center (SOC) workflow using Splunk to monitor and investigate authentication events.
The project focuses on identifying failed and successful login activity, reviewing source IP addresses and users, and creating a dashboard for security monitoring.

sample logs[splunk_soc_practice_logs.txt](https://github.com/user-attachments/files/32856918/s[splunk_soc_practice_logs.txt](https://github.com/user-attachments/files/32857042/splunk_soc_practice_logs.txt)
plunk_soc_practice_logs.txt)
Tools Used
* Splunk Enterprise
* Windows
* Sample authentication and security logs

Objectives
* Ingest security logs into Splunk
* Monitor authentication activity
* Identify failed and successful login attempts
* Review users and source IP addresses
* Investigate suspicious login patterns
* Create a SOC monitoring dashboard

Investigation
The log data contains authentication events with information such as:
* Username
* Login status
* Source IP address
* Action
* Event time
The events were reviewed in Splunk to identify unusual or repeated authentication activity.

SPL ANALYSIS
1. View All Login Events
index=main
Purpose:
Used to retrieve all sample login events from the main index.

2. Display Important Fields
index=main
| table _time user action status source_ip
Purpose:
Used to display important authentication fields in a structured table.
Note: The source_ip field was not available in the current sample data.

3. Count Total Login Events
index=main
| stats count
Purpose:
Counts the total number of login events in the sample dataset.
Result: 10 events.

4. Analyze Login Status
index=main
| stats count by status
Purpose:
Groups login events by their authentication status to compare successful and failed activity.

5. Analyze User Activity
index=main
| stats count by user
| sort - count
Purpose:
Counts login events for each user and sorts the users by activity.

6. Analyze Failed Login Activity
index=main
| search status="failed"
| stats count by user
| sort - count
Purpose:
Filters failed authentication events and groups them by username to identify users with repeated failed login activity.

Dashboard
A Splunk dashboard named SOC Login Monitoring was created using the analyzed login data.
The dashboard contains:
* Total Login Events
* Login Status
* User Activity
* Failed Logins by User

Skills Demonstrated

* Splunk search
* SPL fundamentals
* Authentication log analysis
* User activity analysis
* Failed login investigation
* Security monitoring
* Dashboard creation
[screenshots of soc monitoring.docx](https://github.com/user-attachments/files/32857990/screenshots.of.soc.monitoring.docx)

Disclaimer
This project uses sample data for educational and demonstration purposes.
