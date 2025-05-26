
 Threat Analysis Summary Report

Overview
This project analyzes malicious network activity from a packet capture file using Suricata IDS. The Suricata `eve.json` log was ingested into Splunk for correlation and detection. Events of interest include abnormal Kerberos activity, suspicious DNS queries, and untrusted TLS certificates.

Key Observations

 1. Suspicious Kerberos Activity
 Multiple `KRB_TGS_REQ` and `KRB_AS_REQ` messages involving unusual service principal names (e.g., `ldap/`, `host/`, `cifs/`).
 Several authentication requests lacked pre-authentication or used empty client names.
 MITRE ATT&CK Technique**: `T1558.003 - Kerberoasting`

2. DNS Requests to Suspicious Domains
Domains like `amajai-technologies.work` and multiple Microsoft telemetry domains (`*.microsoft.com`, `windowsupdate.com`) appeared.
The domain `amajai-technologies.work` resolved to `23.106.160.137` and was later accessed over HTTP.
MITRE ATT&CK Technique**: `T1071.004 - Application Layer Protocol: DNS`

3. Unusual HTTP Communication
Host: `amajai-technologies.work`
URI: `/IE9CompatViewList.xml`
User-Agent: Legacy Internet Explorer string (possibly impersonated)
MITRE ATT&CK Technique**: `T1071.001 - Application Layer Protocol: Web Traffic`

4. Suspicious TLS Connections
TLS connection to `45.63.107.192` (non-Microsoft IP) with self-signed or untrusted certificate:
Subject: `CN=zqyefcetkqg.biz`
Issuer: Same as subject (likely forged)
MITRE ATT&CK Technique**: `T1587.001 - Adversary Infrastructure: SSL/TLS Certificates`

5. DCERPC and SMB Traffic
Negotiations and IOCTL queries via SMB, targeting the Domain Controller at `10.12.7.7`.
Indicators of lateral movement preparation or enumeration.
MITRE ATT&CK Technique**: `T1021.002 - Remote Services: SMB/Windows Admin Shares`

Recommendations
 Investigate host `10.12.7.101` for signs of compromise.
 Block access to suspicious domain `amajai-technologies.work`.
 Flag and monitor connections to external IPs with self-signed certificates.
 Validate Kerberos tickets and enforce pre-authentication.

Skills Demonstrated
 Network threat detection with Suricata
 Log ingestion and search in Splunk
 Protocol analysis (DNS, SMB, TLS, Kerberos)
 MITRE ATT&CK-based detection mapping
