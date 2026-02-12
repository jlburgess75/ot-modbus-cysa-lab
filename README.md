# OT/ICS Modbus Attack Detection Lab

## Overview
This project simulates real-world OT/ICS cybersecurity scenarios involving Modbus read/write operations, unauthorized write activity, and packet-level traffic analysis.

The lab demonstrates:
- Detection of unauthorized Modbus write commands (Function Code 06 / 16)
- Wireshark packet analysis of industrial traffic
- Attack reconstruction using command logs and PCAP evidence
- OT-to-SOC incident documentation workflow
- MITRE ATT&CK mapping for ICS environments

Built for:
- SOC Analyst interview demonstrations
- CySA+ skill reinforcement
- OT security transition portfolio (Mechanical Tech → OT-aware SOC Analyst)

---

## Lab Environment
**Components**
- Raspberry Pi (Modbus client / telemetry forwarder)
- Modbus device or simulator (server/slave)
- Wireshark (packet capture)
- Splunk (optional): ingest telemetry and build detections

**Network Flow**
OT Device/Simulator → Raspberry Pi (Modbus) → Logs/PCAP → Detection/IR Documentation

---

## Attack Simulation Scenarios

### Scenario 1 — Unauthorized Write (Function Code 06)
Goal: simulate a malicious write to a holding register and document the evidence.

Evidence generated:
- Command execution logs (mbpoll output)
- Register before/after state
- PCAP showing Modbus write

### Scenario 2 — Network Sniffing & Reconstruction
Goal: capture Modbus traffic and identify write activity using Wireshark filters.

---

## MITRE ATT&CK (ICS) Mapping

| Technique | Description | Lab Demonstration |
|----------|-------------|------------------|
| T0855 | Unauthorized Command Message | Modbus Write Single Register (FC06) |
| T0831 | Manipulation of Control | Forced register value change |
| T0842 | Network Sniffing | Wireshark capture of Modbus traffic |
| T0807 | Command-Line Interface | mbpoll used for register modification |

---

## SOC Incident Report Example
See: `incident-report/incident_report_unauthorized_modbus_write.md`

---

## Visual Proof
Screenshots are stored in `/screenshots`:
- Wireshark Modbus write packet
- Register value before/after
- Command execution output
- Network diagram

---

## Why This Matters (Business Impact)
In real OT environments, unauthorized Modbus write commands can:
- Manipulate process variables
- Shut down production
- Damage equipment
- Create safety hazards

This lab demonstrates detection, analysis, and documentation of such activity from an **OT-aware SOC** perspective.

---

## OT → SOC Skill Bridge
This lab shows how industrial protocol analysis translates into:
- SIEM correlation
- Threat detection engineering
- Alert triage workflows
- ICS threat modeling
