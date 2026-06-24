# SOC Incident Report

## Incident Title

User Unable to Access Internet Due to DNS Misconfiguration

## Incident ID

SOC-INC-2026-001


## Date

24-Jun-2026


## Analyst

Harshitha BR


## Severity

Medium


## Affected Asset

Hostname: WIN10-CLIENT01

Operating System: Windows 10

User: John Doe


## Incident Description

The user reported that internet websites could not be accessed from the workstation.

Initial investigation confirmed that local network connectivity was available while DNS resolution was failing.


## Evidence

* hostname.png
* ipconfig_all.png
* ping_gateway.png
* ping_8.8.8.8.png
* nslookup_failed.png
* browser_error.png
* event_viewer.png


## Investigation Summary

The workstation received a valid IP address.

The default gateway responded successfully.

External internet connectivity was available.

DNS resolution failed.

Further investigation identified an incorrect manually configured DNS server.


## Root Cause

Invalid DNS server configuration.


## Containment

Verified that the issue was not caused by malware or firewall rules.

Confirmed DNS configuration as the source of the incident.


## Recovery

Changed DNS configuration to obtain DNS automatically.

Executed:

* ipconfig /flushdns
* ipconfig /renew


## Verification

* ping google.com successful
* nslookup google.com successful
* Browser successfully opened websites


## Business Impact

One workstation affected.

Temporary loss of internet access.

No data loss observed.

## Recommendations

* Prevent manual DNS changes.
* Perform regular network configuration audits.
* Use DHCP for DNS management.
* Maintain troubleshooting documentation.


## Status

Resolved

The workstation was restored to normal operation after correcting the DNS configuration.
