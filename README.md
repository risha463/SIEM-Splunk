📄 Incident Response Report — Task 2 (SIEM Analysis Using Splunk)

🔐 1. Overview

This project involves analyzing Windows security logs using Splunk SIEM to detect suspicious authentication activities, identify brute-force behavior, classify incidents, and recommend remediation actions.

📁 2. Log Source Details

Log File: windows_security_logs.txt

Log Type: Windows Security Authentication Logs

Sourcetype: log2metrics_keyvalue

Index Used: task2_index

🔗 Log File:
logs/windows_security_logs.txt

🎯 3. Objectives

Ingest log data into Splunk

Search & analyze login events

Identify failed & successful attempts

Detect brute-force attack pattern

Create visualizations

Draft SOC-style incident report

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

✔ EventID Breakdown (4625 / 4624)
index="task2_index"
| stats count by EventID


📸 Screenshots in folder:
/screenshots/query_results/

📊 5. Visualizations Created
✔ EventID Breakdown Pie Chart
✔ Failed Login Attempts Bar Chart
✔ Successful Login vs Failed Login Comparison
✔ Account Name Pie Chart
✔ Status Distribution Pie Chart

📸 Screenshots in folder:
/screenshots/visualizations/

🚨 6. Findings (Alert Analysis)
🔹 Summary:
EventID	Description	Count
4625	Failed Login	3
4624	Successful Login	1
🔹 Suspicious Behaviour Observed:

Multiple failed login attempts

Same IP address: 185.34.55.1

Target account: admin

Short time gap between events

Final successful login

👉 This matches a Brute Force Attack.

🛑 7. Incident Classification

Incident Type: Brute-Force Authentication Attack

MITRE ATT&CK: T1110

Severity: High

Reason:

Multiple rapid failed attempts

Successful login after failures

Admin account targeted

Same attacker IP

🛠️ 8. Recommended Actions
✔ Immediate

Block attacker IP

Reset admin credentials

Review login session details

Enable MFA

✔ System/Policy Fixes

Implement Account Lockout Policy

Monitor EventID 4625 spikes

Restrict admin login from external IP ranges

🧾 9. Screenshots

All screenshots stored in:

/screenshots/
   ├── query_results/
   └── visualizations/

📄 10. Full PDF Report

The full incident response report is available here:

👉 SOC_Incident_Response_Report.pdf

✅ 11. Conclusion

A brute-force attack was successfully identified through SIEM analysis.
Splunk provided visibility into authentication attempts, enabling detection, classification, and mitigation planning.
