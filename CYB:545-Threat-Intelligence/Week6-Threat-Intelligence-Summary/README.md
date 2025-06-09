# Week 6 – Intelligence-Sharing Report: Equifax Case Study

## Course

CYB/545 – Threat Intelligence

## Objective

This report outlines intelligence findings and mitigation strategies related to the 2017 Equifax breach. It uses structured intelligence-sharing protocols to classify, prioritize, and recommend remediations in alignment with the NIST Cybersecurity Framework.

---

## Threat Intelligence Summary

**Event:** Equifax Data Breach (2017)
**Attack Vector:** Exploitation of Apache Struts vulnerability (CVE-2017-5638)
**Threat Actor Motivation:** Financial gain via data exfiltration
**Data Compromised:** Personally Identifiable Information (PII) of \~148 million Americans

---

## Evidence and Observations

* Attackers exploited a known vulnerability (CVE-2017-5638) left unpatched for two months.
* The vulnerability allowed remote code execution via crafted HTTP requests.
* Web traffic logs revealed malicious requests exploiting the input validation flaw.
* The attackers used encrypted channels to exfiltrate data over several weeks.

**Forensic Observations:**

* Logs showed suspicious payload injections with "Content-Type" headers.
* IDS and SIEM flagged unusual outbound traffic but lacked escalation.
* Absence of SSL/TLS inspection tools allowed encrypted exfiltration undetected.

---

## Threat Level Assignment (TLP Framework)

| Threat                              | Severity | Likelihood | TLP Classification | Priority |
| ----------------------------------- | -------- | ---------- | ------------------ | -------- |
| RCE Exploit (Apache Struts)         | High     | High       | TLP\:RED           | Critical |
| Unencrypted Internal Communications | High     | Medium     | TLP\:AMBER         | High     |
| Data Exfiltration (SSL)             | High     | Medium     | TLP\:AMBER         | High     |
| Failure to Patch                    | High     | High       | TLP\:RED           | Critical |
| Weak Access Controls                | Medium   | Medium     | TLP\:GREEN         | Medium   |

---

## Staffing Recommendations

* Increase security operations center (SOC) staffing for 24/7 coverage
* Train personnel to respond to TLP-coded alerts with urgency
* Implement continuous training in vulnerability lifecycle management
* Designate patch management roles with cross-functional authority

---

## Framework Alignment – NIST CSF

**Identify:**

* Asset inventory lacked ownership mapping
* Risk register did not prioritize known CVEs

**Protect:**

* No zero trust model; perimeter-centric strategy failed
* Patch management process lacked verification

**Detect:**

* SIEM lacked correlation rules for CVE-2017-5638
* IDS logs not tied into escalation workflows

**Respond:**

* No pre-established incident playbook for web application vulnerabilities
* Communication gaps delayed internal escalation

**Recover:**

* Public trust severely damaged; response lacked transparency
* Delay in notifying affected consumers increased regulatory penalties

---

## Mitigation Strategies

* Apply critical security patches within 72 hours of release
* Enforce multi-factor authentication (MFA) for all privileged accounts
* Monitor and decrypt outbound SSL traffic where legally permissible
* Update and test incident response plans quarterly
* Enhance logging and alert correlation through machine learning integrations

---

## Conclusion

Equifax’s 2017 breach illustrates how a failure in basic patch management can escalate into a national security-level event. Structured intelligence-sharing, cross-team accountability, and threat-informed defense are essential to prevent similar breaches.

This analysis provides a comprehensive view of how a single missed patch became a critical vulnerability, and how intelligence protocols—when properly implemented—could have accelerated detection and response.
