# macOS-Authentication-Failure-Detection-Lab
Performed authentication failure analysis on macOS using system log filtering. Detected and documented repeated invalid credential attempts resembling brute-force activity.


# 🛡️ Security Incident Report  
## macOS Authentication Failure Detection Lab

**Analyst:** Sai Nikhith Atmakuri  
**Date:** March 2, 2026  
**Project Type:** Security Monitoring & Log Analysis Lab  

---

## 📌 1. Executive Summary

On March 2, 2026, multiple authentication failures were detected on a macOS system during a controlled security lab exercise. Log analysis confirmed repeated invalid credential attempts recorded by the macOS authentication service (`opendirectoryd`).

The rapid sequence of failed authentication events within short time intervals resembles a brute-force credential attempt pattern. This report documents the detection process, log evidence, analysis, and security recommendations.

---

## 🖥️ 2. Environment Details

- **Operating System:** macOS  
- **Log Source:** macOS Unified Logging System  
- **Relevant Process:** `opendirectoryd`  
- **Log Query Method:** `log show` command with predicate filtering  
- **Test Type:** Simulated failed login attempts  

---

## 🔍 3. Attack Simulation

To simulate unauthorized access attempts, multiple incorrect password entries were intentionally performed on the system.

After generating the failed login attempts, the following command was used to query authentication failures:

```bash
log show --predicate '(eventMessage CONTAINS "Authentication failed")' --style syslog --last 1h
