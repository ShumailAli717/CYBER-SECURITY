# Dynamic Malware Analysis and Sandboxing

## Project Overview

This project documents the dynamic analysis of a suspicious file using the **Hybrid Analysis** online malware sandbox.

The objective was to examine the sample's behavior in a controlled sandbox environment, review its network activity, identify suspicious system interactions, and investigate malicious indicators.

## Sample Information

| Property | Details |
|---|---|
| Sample Name | `BankPaymAdviceVend.Report` |
| SHA256 | `2e1408013503cbc13466e2041bd3e045833ce65f5c91b7226e28e27d43d6eaf9` |
| Analysis Platform | Hybrid Analysis |
| Analysis Type | Dynamic Analysis |
| Verdict | Malicious |
| Threat Score | 100/100 |
| Detection | Trojan.Generic |

**Analysis Report:** [View on Hybrid Analysis](https://hybrid-analysis.com/sample/2e1408013503cbc13466e2041bd3e045833ce65f5c91b7226e28e27d43d6eaf9)

## Analysis Methodology

1. Selected the suspicious sample for investigation.
2. Submitted the sample to the Hybrid Analysis sandbox.
3. Reviewed the sandbox verdict and threat score.
4. Examined threat-hunting results and behavioral indicators.
5. Investigated informative, suspicious, and malicious indicators.
6. Reviewed network activity, file operations, and registry interactions.
7. Documented the findings and supporting evidence.

## Key Analysis Findings

### 1. Network Activity

The sandbox reported:

- Communication with external servers and domains.
- HTTP and HTTPS requests, including GET and POST activity.
- Retrieval of files from web servers.
- DNS queries.
- Communication with a domain identified as malicious.
- HTTPS connections using an insecure TLS/SSL version.
- HTTP traffic without expected HTTP headers.
- Multiple unique user-agent strings.

### 2. File System Activity

Observed indicators included:

- Dropping files in temporary directories.
- Writing files in the AppData directory.
- Creating and modifying Windows shortcut (LNK) files.
- Renaming files.
- Writing log files.
- Dropping files containing system information.

### 3. Registry Activity

The sandbox identified:

- Registry key creation and modification.
- Opening and querying registry keys.
- Queries involving service-related registry keys.

### 4. System and User Discovery

The sample showed indicators associated with:

- Gathering system and hardware information.
- Retrieving user account information through SID-related APIs.
- Querying security-token membership.
- Listing processes on a Remote Desktop Session Host.
- Accessing Windows LDAP client functionality.

### 5. Obfuscation and Other Indicators

Additional findings included:

- High file entropy, potentially indicating encrypted or compressed content.
- Indicators of obfuscation and decoding capabilities.
- Runtime module loading.
- Cryptographic class usage.
- A matched compiler/packer signature reported by Detect It Easy (DIE).

### 6. Potential Credential and Data-Theft Behavior

Hybrid Analysis reported attempts to invoke APIs commonly associated with credential theft and data exfiltration functionality.

This is a behavioral indicator and does not independently establish that credentials were successfully stolen or data was exfiltrated.

## Evidence and Screenshots

### Threat Hunting

Screenshots showing the threat-hunting findings and suspicious behavioral activity.

![Threat Hunting](Screenshots/Threat-Hunting/threat-hunting.png)

### Informative Incidents and Reports

Screenshots documenting the informative incident indicators and sandbox analysis results.

![Incident Reports](Screenshots/Incident-Reports/incident-reports.png)

### Malicious Indicators

Screenshots showing the malicious indicators identified by Hybrid Analysis.

![Malicious Indicators](Screenshots/Malicious-Indicators/malicious-indicators.png)

## Security Recommendations

- Treat the analyzed sample as malicious based on the sandbox verdict.
- Avoid executing suspicious files on personal or production systems.
- Investigate identified malicious domains and network indicators.
- Monitor suspicious file-system and registry modifications.
- Review authentication and endpoint activity for unusual behavior.
- Use isolated environments for malware investigation.

## Tools and Technologies

- Hybrid Analysis
- Malware Sandbox
- Dynamic Malware Analysis
- Threat Hunting
- Indicators of Compromise (IOCs)

## Disclaimer

This project was conducted for educational and cybersecurity learning purposes. The analysis reflects the behavior and indicators reported by Hybrid Analysis during sandbox execution. Sandbox findings should be interpreted in their execution context and do not necessarily prove that every reported capability was successfully used.

**Never execute suspicious malware samples on a personal or production system.**
