# SecureBank SOC Lab Architecture

## 1. Overview

The SecureBank SOC Lab simulates a banking security monitoring environment. The architecture consists of an attacker machine, a banking application server, and a SOC monitoring server responsible for collecting logs, detecting threats, and generating security alerts.

## 2. Architecture Components

### 2.1 Attacker Machine (Kali Linux)

Purpose:
- Simulate cyber attacks against the banking system
- Generate security events for detection

Tools:
- Nmap
- Burp Suite
- SQLMap
- Hydra
- Metasploit

---

### 2.2 SecureBank Application Server

Purpose:
- Host the simulated banking application
- Generate application and security logs

Responsibilities:
- User authentication
- Banking transactions
- Web service operation
- Application logging

---

### 2.3 SOC Server (Ubuntu Server)

Purpose:
- Central security monitoring platform

Responsibilities:
- Collect logs
- Analyze security events
- Generate alerts
- Support incident investigation

Main Tool:
- Wazuh SIEM

---

## 3. Network Architecture

All virtual machines communicate through an isolated VMware virtual network.
             Kali Linux
             Attacker
                |
                |
      VMware Internal Network
          192.168.100.0/24
                |
    --------------------------
    |                        |
    |                        |
    SecureBank Server SOC Server
192.168.100.10 192.168.100.20
|
Wazuh SIEM
|
SOC Analyst Dashboard


## 4. Data Flow

1. Attacker performs malicious activity.
2. SecureBank server generates logs.
3. Logs are collected by SOC Server.
4. Wazuh analyzes events.
5. Security alerts are generated.
6. SOC analyst investigates the incident.

## 5. Security Monitoring Scope

The SOC monitors:

- Failed login attempts
- Brute-force attacks
- Web application attacks
- Suspicious user activities
- Unauthorized access attempts
- System changes

## 6. Expected Outcome

The final architecture demonstrates a complete SOC workflow:

Attack → Log Generation → Detection → Alert → Investigation → Response