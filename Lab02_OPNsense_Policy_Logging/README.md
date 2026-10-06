# Lab 02: OPNsense Policy Logging and Firewall Rule Analysis

## Overview
This laboratory exercise focuses on the configuration, testing, and analysis of firewall policy logging in OPNsense. The main goal is to understand how firewall rules generate logs, how those logs can be interpreted, and how policy logging supports network visibility, security monitoring, and incident response.

The lab demonstrates how firewall rules can be configured to allow or deny traffic while capturing detailed information about connection attempts, rule matches, and potential security events. By examining firewall logs, administrators can verify whether a rule is functioning as intended and identify suspicious or unauthorized network activity.

---

## Objectives
The objectives of this lab are to:
- Configure firewall rules in OPNsense with logging enabled.
- Generate both allowed and blocked network traffic.
- Inspect firewall logs to confirm rule behavior.
- Analyze how policy logging supports operational monitoring and security review.
- Evaluate the role of rule ordering, least-privilege access control, and log auditing.
- Document findings and provide recommendations for effective firewall management.

---

## Lab Environment
The lab environment includes:
- OPNsense firewall appliance
- Internal network segment (LAN)
- External network segment or test interface (WAN)
- Client systems used to generate traffic
- Target host or service for connectivity validation
- Firewall rules configured for monitoring and filtering

This setup simulates a typical small office or campus network where security policy enforcement and traffic visibility are critical.

---

## Tools and Requirements
To complete this laboratory exercise, the following are required:
- OPNsense web interface
- Firewall rule configuration panel
- Logging and monitoring features
- Network client systems or test devices
- Traffic generation tools such as browser access, ping, or service requests
- Access to firewall log dashboard

---

## Methodology
The procedure used in this lab was as follows:
1. Accessed the OPNsense management interface.
2. Navigated to the firewall rule configuration section.
3. Reviewed the active rule set and identified the relevant access policies.
4. Enabled logging for selected allow and deny rules.
5. Generated controlled traffic to test both permitted and blocked behavior.
6. Reviewed the OPNsense firewall logs.
7. Examined key fields such as:
   - Timestamp
   - Rule number
   - Action taken
   - Source IP address
   - Destination IP address
   - Protocol
   - Interface
   - Result status
8. Compared the expected outcomes with the observed log entries.
9. Documented findings and recommendations.

---

## Firewall Configuration
The firewall policy logging configuration involved enabling logging on selected rules to capture both allowed and denied traffic. Rules were designed to permit only required services while rejecting unauthorized or suspicious activity.

By enabling logging, the firewall records:
- Which rule processed the traffic
- Whether the traffic was allowed or blocked
- Whether the connection matched an existing stateful session
- Whether the packet originated from an unauthorized or malicious source
- The timestamps and flow details needed for investigation

This level of visibility is essential for both troubleshooting and proactive security monitoring.

---

## Test Scenarios
The following scenarios were used to validate firewall behavior:

- Internal-to-Internet access
  - Expected: Allowed
  - Observed: Logged as permitted traffic
  - Purpose: Confirm that valid traffic matches the correct rule

- Internal-to-blocked destination
  - Expected: Denied
  - Observed: Logged as blocked
  - Purpose: Verify that access control rules are enforced

- Unauthorized or suspicious connection attempt
  - Expected: Rejected
  - Observed: Logged as denied or rejected
  - Purpose: Demonstrate security monitoring and threat visibility

- Stateful connection tracking
  - Expected: Allowed as part of an established session
  - Observed: Logged as session-established traffic
  - Purpose: Confirm proper firewall state handling

---

## Results and Interpretation
The firewall logs confirmed that policy enforcement was functioning as expected. Allowed connections were recorded as successful transactions, while blocked or rejected traffic was captured as denied events. The log data provided clear visibility into who attempted to communicate, which rule processed the traffic, and whether the request was permitted or denied.

Key observations from the logs included:
- Source and destination IP addresses helped determine whether traffic was internal or external.
- Rule numbers allowed administrators to correlate traffic with the appropriate firewall policy.
- Protocol and port information showed which services were accessed or attempted.
- Time stamps enabled event correlation and troubleshooting.
- Denied connections provided evidence of attempted unauthorized access or policy violations.

---

## Findings
The laboratory exercise revealed several important findings:
- Firewall policy logging is essential for validating rule behavior.
- Logging increases visibility into network connections and access attempts.
- Rule ordering significantly affects how traffic is handled.
- Deny rules must be carefully designed to avoid unintentionally blocking legitimate services.
- Monitoring firewall logs supports incident response and proactive threat detection.
- Policy logging provides evidence for audits, troubleshooting, and security reviews.

These findings highlight the importance of maintaining a well-documented and correctly ordered firewall rule set.

---

## Discussion
This lab emphasized that effective network security depends not only on access control, but also on the ability to observe and validate policy enforcement. In modern networks, firewall policies must be both secure and transparent. OPNsense’s logging capabilities provide this transparency by capturing actionable details about traffic flows and rule matches.

The ability to review logs in real time is especially important for detecting MEC misconfigurations, investigating suspicious behavior, and confirming whether the firewall is enforcing the desired control policy. By correlating firewall logs with network activity, administrators can improve both operational efficiency and security posture.

---

## Importance of Policy Logging
Policy logging is a critical feature in firewall administration because it:
- Confirms whether traffic is being allowed or denied as expected
- Helps identify misconfigured rules or policy conflicts
- Improves visibility into attempted unauthorized access
- Assists in incident investigation and forensic analysis
- Supports compliance, auditing, and security monitoring requirements

Without logging, firewall control would be difficult to validate and troubleshoot.

---

## Conclusion
The OPNsense policy logging lab was successfully completed, and the results clearly demonstrate the value of firewall logging in secure network management. The exercise confirmed that enabling logging on firewall rules provides administrators with critical insight into traffic behavior, policy enforcement, and potential security incidents.

By reviewing firewall logs and correlating them with configured policies, network administrators can improve rule validation, detect suspicious activity, and ensure their firewall is enforcing the intended security model.

---

## Recommendations
To strengthen firewall monitoring and operational effectiveness, the following recommendations are advised:
- Enable logging on all critical allow and deny rules.
- Review logs regularly for abnormal traffic patterns.
- Use specific and well-documented firewall rules.
- Maintain a clear rule ordering strategy.
- Minimize unnecessary logging noise on low-priority traffic.
- Integrate firewall logs with centralized SIEM or log management systems.
- Periodically test rule behavior to confirm that policies still meet operational requirements.

---

## References
- OPNsense Documentation: Firewall and Rule Logging
- OPNsense User Guide
- Network Security Fundamentals Course Materials

---

## Appendix
Optional supporting evidence may include:
- Screenshot of firewall rule configuration
- Screenshot of logging enabled on selected rules
- Screenshot of the firewall logs dashboard
- Example of an allowed traffic log entry
- Example of a denied or rejected traffic log entry

These visual records can strengthen the final report and provide clear evidence of the lab’s results.
