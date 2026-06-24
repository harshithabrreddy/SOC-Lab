# Lessons Learned

## Project

SOC-001 User Cannot Access Internet


## New Commands Learned

hostname

whoami

ipconfig

ipconfig /all

ping

nslookup

ipconfig /flushdns

ipconfig /renew


## What I Learned

* How to investigate a network connectivity issue.
* How to collect evidence before making changes.
* The difference between IP connectivity and DNS resolution.
* How to identify an incorrect DNS configuration.
* How to restore DNS settings.
* How to verify that the issue has been resolved.
* How to document an investigation like a SOC analyst.


## Mistakes I Made

* Initially assumed the internet was completely down.
* Learned that pinging an IP address and resolving a domain name test different parts of the network.


## Important Concepts

Internet connectivity and DNS resolution are different.

If ping 8.8.8.8 works but nslookup google.com fails, the likely issue is DNS.

Always gather evidence before making configuration changes.

Never assume the root cause without testing.


## Skills Practiced

* Windows networking
* DNS troubleshooting
* Evidence collection
* Investigation documentation
* Root cause analysis
* Incident reporting


## Interview Questions I Can Now Answer

1. What is DNS?
2. What is the difference between ping and nslookup?
3. Why do we use ipconfig /all?
4. How do you identify a DNS issue?
5. What is root cause analysis?
6. How do you verify that an incident is resolved?


## Improvements for Next Lab

* Use Wireshark to capture DNS packets.
* Include more Event Viewer screenshots.
* Practice documenting investigation timelines.
