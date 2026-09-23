<h1>phishing-to-exfiltration-investigation-simulated-security-incident</h1>
<h2>Description</h2>
simulated SOC investigation of a phishing-to-exfiltration incident using splunk for triage, timeline reconstruction, and 5W incident reporting.
<br/>

<h2>Overview</h2>
this project documents a simulated SOC investigation in which an initial phishing email led to a multi-stage compromise involving powershell execution and data exfiltration. <br/>

acting as a tier 1 SOC analyst, i triaged the alert, investigated the attack chain end-to-end, and documented findings and remediation recommendations following a standard incident response workflow. <br/>

<h2>Scenario Summary</h2>
an end user received a phishing email that, once interacted with, triggered a chain of malicious activity:

1. initial access - phishing email delivered to a user, containing a malicious link/attachment.
2. execution - attacker leveraged powershell on the compromised host for post-exploitation activity.
3. exfiltration - data was transferred out of the environment to an external destination.

<h2>Tools & Environment</h2>

- splunk - log search and correlation (SPL) across email, endpoint, and network data sources to reconstruct the attack timeline.
- virustotal - reputation checks on sender domains, URLs, attachments, and file hashes.
- case management workflow - documented investigation steps, IOCs, and final disposition in a simulated SOC ticket.

<h2>Investigation Methodology</h2>

1. Ticket Intake

- received the alert/ticket for review and began triage in the case management workflow.

2. Event Triage (Splunk)
for the flagged event, i pulled the following data points to establish context around the activity:

- affected host - the system where the activity occurred.
- associated use - the account tied to the host/session at the time.
- process id (PID) and parent processs id (PPID) - to identify what spawned the suspicious process.
- command executed - the full command line for the flagged process.
- execution location - where on the host/network the command ran.

3. Timeline Construction

- chained the individual events (initial email interaction > process execution > follow-on activity) into a single timeline using the host/user/pid-ppid relationships identified above.
- the timeline was used to establish whether the chain of events, taken together, indicated a genuine compromise versus benign/false-positive activity.

4. Reporting (5W Format)
documented findings in a structured report answering:

- Who - user/account and host involved.
- What - nature of the malicious activity (phishing > powershell execution > exfiltration).
- When - timestamps establishing he sequence of events.
- Where - host, process location, any nay external destinations involved.
- Why - likely intent/impact of the activity (ex. credential theft, data exfiltration)

5. Remediation & Actionable Recommendations

- isolate the affected host from the network.
- block the malicious domain/ip.
- force credential reset for the affected user.
- review for persistence mechanisms or further lateral movement.
- update detection content to catch similar powershell execution patterns in the future.

<h2>Skills Demonstrated</h2>

- ticket-based soc triage workflow.
- splunk process-tree analysis (host, user, pid/ppid, commandline, execution context).
- event timeline reconstruction to validate a suspected compromise.
- structured incident reporting (5w methodology).
- threat inteligence enrichment (virustotal).
- remediation planning and actionable recommendations.
