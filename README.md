# Splunk-Firewall-Dashboard
📊 Splunk dashboard project for visualizing simulated firewall log data. Includes data ingestion setup, SPL queries, dashboard panels, and alerting – built for cybersecurity monitoring and blue team practice.
# Firewall Log Visualization in Splunk

## Overview

This project demonstrates how to build a **Splunk dashboard** for analyzing **firewall traffic logs**. The goal is to visualize key security metrics such as blocked vs allowed connections, top source IPs, protocols, and traffic volume trends.

---

## Architecture

```
[Firewall Simulator] → [Syslog Output] → [Splunk Indexer] → [Dashboards / Alerts]
```

- Logs generated using a **firewall simulator** mimicking traffic from commercial firewalls (e.g., Cisco ASA, pfSense).
- Traffic sent to **Splunk** using **syslog (UDP)** input.
- Indexed and visualized through Splunk's **Search & Reporting App**.

---

##  Prerequisites

- Splunk Enterprise or Cloud Instance (v9.x recommended)
- Basic familiarity with SPL queries
- Syslog input configured in Splunk
- Optional: Dashboard Studio for enhanced visual layouts

---

##  Data Source

> This project uses **simulated firewall traffic** generated in a controlled lab environment.
>
> The log data mimics real-world firewall logs and was sent to Splunk via syslog to replicate the ingestion pipeline. This approach ensures no sensitive or production data is exposed, while still allowing full functionality for dashboard development and security analysis.

---

##  Example SPL Queries

```spl
sourcetype=firewall_logs action=* | stats count by action
sourcetype=firewall_logs | top src_ip limit=10
sourcetype=firewall_logs | timechart count by action span=1h
```

Customize `sourcetype` and field names according to your firewall log format.

---

## 📊 Dashboard Panels

- **Panel 1:** Action Breakdown (Allowed vs Blocked) – Pie Chart
- **Panel 2:** Top Source IPs – Table
- **Panel 3:** Protocol Distribution – Bar Chart
- **Panel 4:** Traffic Trend Over Time – Timechart

Exported dashboard JSON is available in the `dashboards/` folder for easy import into Splunk.

---

## ⏰ Alerts (Optional)

You can convert queries into alerts:

- Example: Trigger an alert if `blocked` events exceed 1000/hour.

```spl
sourcetype=firewall_logs action=blocked | stats count > 1000
```

Use **Save As > Alert** in Splunk to set thresholds, frequency, and notification actions (e.g., email, webhook).

---

## 📂 Project Structure

```
├── README.md
├── dashboards/
│   └── firewall_dashboard.json
├── queries/
│   └── sample_searches.txt
├── sample_logs/
│   └── firewall_simulated.log
└── docs/
    └── architecture.png
```
---

## 🖼️ Screenshots

Below are some sample screenshots from the Splunk dashboard created in this project.

### 🔹 Dashboard Overview

<img width="2552" height="772" alt="Image" src="https://github.com/user-attachments/assets/dee739ea-0d67-4ead-8df3-8e34c5910dee" />

<img width="2554" height="771" alt="Image" src="https://github.com/user-attachments/assets/62ec509d-3ff7-4142-b5ba-e27603c6b569" />

### 🔹 Traffic Trend Panel

<img width="2357" height="800" alt="Image" src="https://github.com/user-attachments/assets/cd8315a3-c68f-4bb1-8044-7fced66b4376" />

<img width="2548" height="762" alt="Image" src="https://github.com/user-attachments/assets/90268436-6641-4833-a427-179e45f8dd51" />

### 🔹 Top Source IPs Panel

<img width="2521" height="741" alt="Image" src="https://github.com/user-attachments/assets/bec6bb1b-9b65-4ade-be8c-70baf83d1aa5" />

<img width="2541" height="734" alt="Image" src="https://github.com/user-attachments/assets/b75b343e-2b0d-4ade-a759-4bbbbd759d18" />



---

## 🚀 Getting Started

1. Clone this repository.
2. Set up Splunk and configure syslog ingestion.
3. Import the dashboard JSON from `/dashboards`.
4. Test with `/sample_logs/firewall_simulated.log` or your own lab data.
5. Adjust queries and panels based on your log structure.

---

## 📚 References

- [Splunk Dashboard Guide](https://docs.splunk.com/Documentation/Splunk/latest/Viz/Aboutdashboards)
- [Firewall Data Onboarding - Splunk Lantern](https://lantern.splunk.com/Data_Descriptors/Network_firewall_data)
- [Tutorial Video](https://youtu.be/tkSZws7vBEo?si=lhOHZyOGsBu_Weep)

---

## 👨‍💻 Author

**Manav Sadyora**\
Cybersecurity Enthusiast | SOC & Blue Teaming\
[TryHackMe](https://tryhackme.com/p/Manav.Sadyora) • [LinkedIn](http://www.linkedin.com/in/manav-sadyora) • [GitHub](https://github.com/mnv1851)

