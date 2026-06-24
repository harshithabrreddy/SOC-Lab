# SOC-001 Investigation Notes

## Investigation Information

**Incident ID:** SOC-INC-2026-001

**Investigation Date:** 24-Jun-2026

**Analyst:** Harshitha

**System:** Windows 10 VM

**Issue:** User unable to access internet websites.


# Step 1 - Received Incident

## User Complaint

The user reported that internet websites were not opening.

Time Received:

09:30 AM

Priority:

Medium


# Step 2 - Collected Basic System Information

## Command

cmd
hostname

### Purpose

Identify the affected computer.

### Output

WIN10-CLIENT01


### Observation

The affected system hostname is WIN10-CLIENT01.

Evidence

hostname.png


## Command

cmd
whoami

### Purpose

Identify the logged-in user.

### Output

desktop\john

### Observation

The logged-in user is desktop\john.


# Step 3 - Checked Network Configuration

## Command

cmd
ipconfig /all

### Purpose

Collect IP configuration.

### Information Collected

* IPv4 Address
* Subnet Mask
* Default Gateway
* DNS Server
* DHCP Status

### Observation

The workstation has a valid IPv4 address.

The default gateway is reachable.

DNS Server configured:

192.168.200.200

Evidence

ipconfig_all.png


# Step 4 - Tested Gateway Connectivity

## Command

cmd
ping 192.168.1.1

### Purpose

Verify local network connectivity.

### Result

Reply received.

Packets Lost:

0%

### Observation

The workstation successfully communicates with the default gateway.

Evidence

ping_gateway.png


# Step 5 - Tested Internet Connectivity

## Command

cmd
ping 8.8.8.8

### Purpose

Verify external internet connectivity.

### Result

Reply received.

Packets Lost:

0%

### Observation

Internet routing is functioning correctly.

Evidence

ping_8.8.8.8.png


# Step 6 - Tested DNS Resolution

## Command

cmd
nslookup google.com

### Purpose

Verify DNS functionality.

### Result

DNS request timed out.

Server failed.

### Observation

The workstation cannot resolve domain names.

Evidence

nslookup_failed.png


# Step 7 - Browser Test

Opened

https://www.google.com

### Observation

Browser displayed:

"This site can't be reached."

Evidence

browser_error.png


# Step 8 - Checked Event Viewer

Location

Windows Logs

↓

System

### Observation

No DHCP failures.

No network adapter failures.

No malware-related events detected.

Evidence

event_viewer.png


# Investigation Summary

## Findings

✓ IP Address Assigned

✓ Gateway Reachable

✓ Internet Reachable

✗ DNS Resolution Failed

✗ Websites Could Not Open


# Root Cause Analysis

The DNS server was manually configured with an invalid IP address.

Because DNS resolution failed, domain names such as google.com could not be translated into IP addresses.


# Corrective Action

Changed DNS configuration back to automatic.

Executed:

cmd
ipconfig /flushdns

ipconfig /renew


# Verification

Executed:

cmd
ping google.com

nslookup google.com

Both commands completed successfully.

The browser successfully opened Google.


# Final Conclusion

The issue was caused by an incorrect DNS server configuration.

After restoring the DNS settings, internet access was successfully restored.

Investigation completed successfully.
