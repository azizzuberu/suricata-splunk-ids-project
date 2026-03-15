# Suricata + Splunk Intrusion Detection System (IDS)

## Overview

This project demonstrates a **real-time network intrusion detection and monitoring system** built using **Suricata IDS** and **Splunk SIEM**.
The system monitors network traffic, detects malicious activity, and visualizes security events through a Splunk dashboard.

The goal of the project is to simulate a **Security Operations Center (SOC)** environment where network threats can be detected, analyzed, and monitored in real time.

---

## Architecture

Network Traffic → Suricata IDS → eve.json Logs → Splunk SIEM → Security Dashboard & Alerts

1. Suricata monitors network traffic.
2. Detected events and alerts are stored in `eve.json`.
3. Splunk ingests the logs and indexes them.
4. Dashboards and alerts visualize and analyze attack activity.

---

## Technologies Used

* Suricata – Network Intrusion Detection System
* Splunk – Security Information and Event Management (SIEM)
* Nmap – Attack simulation and network scanning
* Ubuntu Linux – Operating system environment
* GitHub – Project version control and hosting

---

## Features

* Real-time network intrusion detection
* Integration of Suricata logs with Splunk
* Security event monitoring dashboard
* Attack visualization (top attackers, attack types, targeted ports)
* Alert generation for suspicious activities
* Log analysis using Splunk Search Processing Language (SPL)

---

## Project Structure

```
suricata-splunk-ids-project
│
├── configs/
│   └── suricata-config.yaml
│
├── dashboards/
│   └── splunk-dashboard.json
│
├── scripts/
│   └── attack-simulation.sh
│
├── screenshots/
│   └── dashboard-preview.png
│
└── README.md
```

---

## Installation Guide

### 1. Install Suricata

```
sudo apt update
sudo apt install suricata -y
```

Verify installation:

```
suricata --version
```

---

### 2. Install Splunk

Download Splunk Enterprise and install:

```
tar -xvzf splunk.tgz
cd splunk/bin
sudo ./splunk start --accept-license
```

Access Splunk Web:

```
http://localhost:8000
```

---

### 3. Configure Splunk to Ingest Suricata Logs

Suricata logs are stored at:

```
/var/log/suricata/eve.json
```

Add this file as a **data input** in Splunk to monitor IDS events in real time.

---

## Example Splunk Queries

### View IDS Alerts

```
index=suricata event_type=alert
```

### Top Attack Types

```
index=suricata event_type=alert
| stats count by alert.signature
| sort -count
```

### Top Attacking IP Addresses

```
index=suricata event_type=alert
| stats count by src_ip
| sort -count
```

### Attack Timeline

```
index=suricata event_type=alert
| timechart count
```



## Attack Simulation

Network attacks can be simulated using Nmap:

```
nmap -sS <target-ip>
```

This generates alerts in Suricata which will appear in the Splunk dashboard.



## Dashboard Visualization

The Splunk dashboard includes:

* Total intrusion alerts
* Top attack signatures
* Top attacking IP addresses
* Targeted ports
* Attack timeline

These visualizations help security analysts quickly identify threats and patterns.



## Learning Outcomes

This project demonstrates the following cybersecurity skills:

* Intrusion Detection System deployment
* SIEM integration
* Security log analysis
* Threat monitoring
* SOC-style dashboard creation
* Network attack detection



## Future Improvements

* Integrate machine learning for anomaly detection
* Add Zeek network monitoring
* Automate IP blocking using firewall rules
* Deploy the system in a cloud environment



## Author

Zuberu Abdul Aziz

Cybersecurity and Information Security enthusiast

## License

This project is for educational and research purposes.
