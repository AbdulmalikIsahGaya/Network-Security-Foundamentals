# Lab Report: OPNsense Policy Logging and Firewall Rule Analysis

## 1. Introduction
This report documents the configuration, testing, and analysis of firewall policy logging in OPNsense. The primary objective of this laboratory exercise was to understand how firewall rules generate log entries, how traffic is classified as allowed or denied, and how log data can be used for network security monitoring and troubleshooting.

Policy logging is an essential feature in modern firewall systems because it provides visibility into traffic flows, helps verify rule effectiveness, and supports incident response activities. In OPNsense, logging can be enabled on individual firewall rules to capture information such as source and destination addresses, protocol type, rule action, and timestamps.

---

## 2. Objectives
The objectives of this lab were to:
- Configure firewall rules with logging enabled in OPNsense.
- Generate both allowed and blocked traffic to verify rule behavior.
- Inspect firewall logs to confirm the action taken by the firewall.
- Analyze how policy logging supports network monitoring and security review.
- Demonstrate the importance of rule ordering, least-privilege policy design, and log review.

---

## 3. Lab Environment
The laboratory environment consisted of:
- OPNsense firewall appliance
- One internal network segment (LAN)
- One external network segment or test interface (WAN)
- Client systems generating test traffic
- A target host or service for connectivity validation
- Firewall rules configured for monitoring and filtering

The testing environment was designed to simulate a typical small office or campus network where firewall policy enforcement and logging are necessary for both service accessibility and security.

---

## 4. Methodology
The following procedure was implemented during the laboratory exercise:

1. Accessed the OPNsense web interface.
2. Navigated to the firewall rule configuration section.
3. Reviewed the current rule set and identified relevant access rules.
4. Enabled logging for selected allow and block rules.
5. Generated controlled network traffic to test rule behavior.
6. Reviewed the firewall logs in the OPNsense dashboard.
7. Examined key log fields such as:
   - Timestamp
   - Rule number
   - Action taken
   - Source IP
   - Destination IP
   - Protocol
   - Interface
   - Result status
8. Compared expected behavior with observed log entries.
9. Documented findings and recommendations.

---

## 5. Configuration Details
The firewall policy logging configuration included enabling logging on selected rules to capture both permitted and denied traffic. Rules were configured to allow only required services while blocking unnecessary or suspicious traffic.

The logging feature in OPNsense helps administrators monitor:
- Which rule processed the traffic
- Whether the traffic was allowed or blocked
- Whether the packet matched an existing stateful firewall session
- Whether a rule was triggered by a malicious or unauthorized source

This setup is valuable for both operational monitoring and forensic analysis.

---

## 6. Test Scenarios and Results
The following test scenarios were conducted to validate firewall behavior:

| Test Scenario | Traffic Type | Expected Result | Observed Result | Notes |
|---|---|---|---|---|
| Internal to Internet access | HTTP/HTTPS | Allowed | Logged as permitted | Confirmed rule matched |
| Internal to blocked destination | Restricted port/service | Denied | Logged as blocked | Verified rule enforcement |
| Port scanning or unauthorized connection attempt | Suspicious inbound/outbound traffic | Blocked | Logged as rejected | Useful for security observation |
| Established connection tracking | Stateful traffic | Allowed | Logged as session established | Demonstrated firewall state behavior |

The logs confirmed that firewall rules processed traffic according to the configured policy. Allowed connections were recorded as successful transactions, while blocked traffic was recorded as denied or rejected based on the configured rules.

---

## 7. Analysis of Firewall Logs
The firewall log entries provided important insight into how the security policy was functioning.

Key observations included:
- Log entries recorded the precise time each packet or flow was processed.
- Source and destination IP addresses helped identify whether traffic was internal or external.
- The action field showed whether the traffic was allowed, rejected, or blocked.
- The rule number enabled administrators to correlate traffic with a specific policy entry.
- Protocol and port information aided in determining whether application-layer services were being accessed correctly.
- Review of logs allowed for quick identification of unauthorized or abnormal behaviors.

These log fields are crucial for both day-to-day network administration and cybersecurity operations. Without logging, firewall policy enforcement would be difficult to validate and troubleshoot.

---

## 8. Findings
The laboratory exercise revealed several important findings:

1. Firewall policy logging is essential for verifying whether a rule works as intended.
2. Logging improves visibility into network connections and access attempts.
3. Rule ordering plays a critical role in determining how traffic is handled.
4. Deny rules must be carefully designed to prevent legitimate services from being unintentionally blocked.
5. Monitoring firewall logs supports incident response by identifying suspicious behavior patterns.
6. Policy logs provide evidence for operational troubleshooting and security audits.

The exercise also demonstrated that OPNsense can provide a precise view of network activity when logging is configured correctly.

---

## 9. Discussion
This lab emphasized the importance of structured firewall policy management. In modern network security, access control must be both effective and observable. OPNsense’s policy logging capability enables administrators to validate the intent of each firewall rule and confirm that traffic is being processed according to the network’s security requirements.

The ability to inspect logs in real time is particularly useful for identifying misconfigurations, detecting policy violations, and monitoring unauthorized access attempts. By correlating log entries with firewall rules, administrators can improve both security posture and operational efficiency.

---

## 10. Conclusion
The OPNsense policy logging lab was successfully completed, and the results demonstrated that firewall logging is a critical component of secure network management. The lab confirmed that logging provides visibility into traffic decisions and supports both performance troubleshooting and security monitoring.

By enabling logging on firewall rules and analyzing the resulting data, network administrators can improve policy validation, detect suspicious activity, and ensure that the firewall is enforcing the organization’s intended access control policy. This lab highlights the value of proper rule design, continuous monitoring, and effective log review in maintaining a secure network environment.

---

## 11. Recommendations
To enhance the security and operational value of OPNsense firewall logging, the following recommendations are suggested:
- Enable logging on all critical allow and deny rules.
- Review logs regularly to detect unusual connection patterns.
- Use specific rules rather than overly broad permit policies.
- Maintain an organized rule set with clear documentation.
- Avoid excessive logging on low-priority traffic to reduce noise.
- Integrate firewall logs with centralized SIEM or logging systems for long-term analysis.
- Test firewall policies periodically to confirm they still meet organizational requirements.

---

## 12. References
- OPNsense Documentation: Firewall and Rule Logging
- OPNsense User Guide
- Network Security Fundamentals Course Materials

---

## 13. Appendix (Optional)
Add screenshots of:
- Firewall rule configuration
- Logging enabled on selected rules
- Firewall log dashboard
- Example blocked/allowed traffic log entries

These visual records can strengthen the final report and provide supporting evidence for the analysis.
