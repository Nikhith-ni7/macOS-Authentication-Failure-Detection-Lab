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






## 📄 4. Log Evidence

The following indicators were observed in system logs:

Process: opendirectoryd

Message: Authentication failed

Error Code: ODErrorCredentialsInvalid

Multiple failures occurring within seconds of each other

Precise timestamps indicating rapid repetition

Example Log Entry
2026-03-02 20:17:48.096114-0500  
localhost opendirectoryd[363]:  
Authentication failed for <private>: ODErrorCredentialsInvalid

The error code ODErrorCredentialsInvalid confirms invalid credential attempts (incorrect password).

## 🧠 5. Analysis

Log timestamps indicate numerous authentication failures occurring between approximately 20:17:27 and 20:18:26, with several attempts occurring within the same second.

Key Observations

Repeated authentication failures in rapid succession

Consistent error code indicating invalid credentials

Central authentication service (opendirectoryd) handling validation

The behavior pattern aligns with brute-force or repeated credential-guessing activity. In this lab environment, the activity was intentionally generated for testing purposes.

## ⚠️ 6. Risk Assessment

Risk Level: 🟡 Medium (Lab Environment)

In a corporate environment, similar log patterns could indicate:

Unauthorized access attempts

Credential stuffing or brute-force attacks

Malware attempting privilege escalation

Compromised local or remote authentication attempts

Rapid repeated authentication failures should always be investigated.

## 🛠️ 7. Recommendations

Implement account lockout policies after a defined number of failed attempts

Enable Multi-Factor Authentication (MFA) wherever possible

Monitor authentication logs using a centralized SIEM solution

Configure alerting for excessive authentication failures within short time intervals

Investigate recurring authentication failures for potential malicious activity

## ✅ 8. Conclusion

This lab successfully demonstrated the detection and analysis of authentication failures using macOS Unified Logs. By filtering and interpreting system log data, repeated invalid credential attempts were identified and analyzed.

The exercise highlights the importance of log monitoring and authentication event analysis in early detection of unauthorized access attempts.
