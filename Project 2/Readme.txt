# 🛡️ Malicious Network Traffic Detection using Suricata & Splunk

📌 Project Overview
This project demonstrates how to detect malicious network traffic using Suricata IDS and visualize the results in Splunk. Infected PCAP files are analyzed and converted into structured JSON logs, then ingested into Splunk for threat detection and dashboarding.

 🎯 Objectives
- Detect malware communication and exploit attempts in PCAP traffic
- Use Suricata to generate JSON alerts from packet captures
- Ingest Suricata logs into Splunk
- Build detection dashboards using SPL queries

 🛠️ Tools & Technologies
- Suricata IDS
- Splunk (Free version)
- Python (optional log manipulation)
- Sample infected PCAPs from [malware-traffic-analysis.net](https://www.malware-traffic-analysis.net/)

 📁 Project Structure

├── 01_raw-pcaps/
├── 02_suricata-logs/
├── 03_splunk-setup/
├── 04_splunk-dashboards/
├── 05_analysis-reports/
├── scripts/
└── README.md
