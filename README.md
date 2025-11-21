📄 Incident Response Report — Task 2 (SIEM Analysis Using Splunk)

🔐 1. Overview

This project analyzes Windows Security Logs using Splunk SIEM to detect suspicious authentication attempts, identify brute-force behavior, classify incidents, and provide remediation steps.

📁 2. Log Source Details

Log File: windows_security_logs.txt

Log Type: Windows Security Authentication Logs

Sourcetype: log2metrics_keyvalue

Index Used: task2_index

📸 Screenshot — Log Upload:
/screenshots/upload.png

🎯 3. Objectives

Ingest logs into Splunk

Monitor authentication events

Detect failed & successful logins

Identify brute-force login patterns

Build visualizations

Prepare SOC-style incident report

🔍 4. Splunk Queries Used
✔ View All Events
index="task2_index"

✔ Failed Login Attempts
index="task2_index" "Failed Login"

✔ Successful Login Attempt
index="task2_index" "Successful Login"

✔ Count of Failed Logins
index="task2_index" "Failed Login"
| stats count

✔ Failed Logins by IP Address
index="task2_index" "Failed Login"
| stats count by IpAddress

✔ EventID Breakdown (4624 / 4625)
index="task2_index"
| stats count by EventID


📸 Query Result Screenshots:

/screenshots/search_all_events.png

/screenshots/failed_logins.png

/screenshots/successful_login.png

/screenshots/event_timeline1.png

/screenshots/event_timeline2.png

📊 5. Visualizations Created
✔ EventID Breakdown Pie Chart
✔ Failed Login Attempts Bar Chart
✔ Successful vs Failed Logins
✔ Status Pie Chart
✔ Account Name Pie Chart

📸 Visualization Screenshots:

/screenshots/eventid_breakdown.png

/screenshots/bar_chart_failed_logins.png

/screenshots/pie_chart_successful_login.png

/screenshots/pie_chart_account_name.png

/screenshots/pie_chart_Status.png

/screenshots/visualizations.png

🚨 6. Findings (Alert Analysis)
🔹 Summary of Events:
EventID	Meaning	Count
4625	Failed Login	3
4624	Successful Login	1
🔹 Suspicious Indicators:

Same attacker IP: 185.34.55.1

Target account: admin

3 failed attempts within seconds

Followed by 1 successful login

👉 This is a confirmed brute-force attack pattern.

🛑 7. Incident Classification

Incident Type: Brute-Force Authentication Attack

MITRE ATT&CK: T1110

Severity: High

Reason: Rapid failed attempts + final successful compromise.

🛠️ 8. Recommended Actions
✔ Immediate:

Block IP 185.34.55.1

Force password reset of admin

Review session after compromise

Enable MFA

✔ Policy Fixes:

Enable Account Lockout Policies

Monitor EventID 4625 spikes

Restrict admin login from external IPs

🧾 9. Screenshots Included

All screenshots stored here:

/screenshots/


Includes:

upload.png

search_all_events.png

failed_logins.png

successful_login.png

event_timeline1.png

event_timeline2.png

eventid_breakdown.png

bar_chart_failed_logins.png

pie_chart_successful_login.png

pie_chart_account_name.png

pie_chart_Status.png

visualizations.png

📄 10. Full PDF Report

👉 SOC_Incident_Response_Report.pdf

✅ 11. Conclusion

Splunk SIEM successfully detected a brute-force login attack involving multiple failed attempts followed by a successful authentication.
This event is classified as High Severity, requiring immediate remediation and future monitoring.
