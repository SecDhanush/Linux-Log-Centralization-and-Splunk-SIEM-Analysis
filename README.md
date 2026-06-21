# Centralized Endpoint Linux Log Monitoring & SIEM Analysis

## Project Overview
This deployment establishes an enterprise-grade centralized log collection and security monitoring framework. By configuring the **Splunk Universal Forwarder** on an **Ubuntu Server** node, critical operating system logs, authentication events, and containerized web application traffic are securely forwarded in real time to a centralized **Splunk Enterprise** indexer for proactive threat hunting and continuous visibility.

---

## Technical Architecture & Flow
1. **Endpoint Node:** Ubuntu Server generating internal system logs (`/var/log/syslog`) and authentication trails (`/var/log/auth.log`).
2. **Container Security:** Hosted **DVWA (Damn Vulnerable Web Application)** via Docker, tracking live web attack vectors directly from containerized JSON logs.
3. **Log Shipper:** Splunk Universal Forwarder parsing localized directory rules via tailored `inputs.conf` profiles.
4. **SIEM Pipeline:** Encrypted real-time data ingestion and event correlation managed via downstream Splunk indexers.
5. **Analyst Workspace:** Formulated Search Processing Language (SPL) threat hunting matrices to isolate indicators of compromise (IoCs).

---

## Configuration Blueprints Included

* **`inputs.conf`**: Defines target data inputs, configuring dedicated stanzas to actively track system authentication and capture real-time live application logs from Docker containers.
* **`splunk_threat_hunting_queries.spl`**: A curated library of production-ready SPL search queries designed to isolate malicious patterns, web application attacks, and anomalous infrastructure events.

---

## Key Use Cases Monitored

### 1. Web Application Attack Detection (DVWA)
Monitors containerized web logs for signature indicators of common OWASP Top 10 vulnerabilities, such as **SQL Injection (SQLi)** strings (e.g., `UNION SELECT`) and potential **Brute Force** access attempts directed at application portals.

### 2. Brute Force & Unauthorized Linux Access
Tracks repetitive SSH validation errors, mapping credential stuffing attempts or dictionary attacks targeting internal server infrastructure.

### 3. Privilege Escalation & Abuse Tracking
Monitors the use of execution privileges (`sudo` commands), ensuring complete traceability of root-level activities and identifying unauthorized system changes.
