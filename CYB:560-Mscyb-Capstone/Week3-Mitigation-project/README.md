## Week 3: Summative Assessment – Mitigation Presentation

### Title  
**Runbooks for Incident Response**

### Objective  
This presentation outlines the role of structured runbooks in mitigating high-risk cybersecurity incidents. The three threats addressed are:  
- Credential Compromise  
- Website Code Injection  
- DDoS Attacks  

All runbooks are designed with board-level oversight in mind and align with NIST’s risk-based framework.

---

### Threat 1: Credential Compromise  
**Risks**  
- Unauthorized access  
- Potential data breaches  
- Financial loss  

**Runbook**  
- Identify compromised account via logs  
- Revoke access or reset credentials  
- Force logout from all sessions  
- Check for lateral movement  
- Notify impacted parties  
- Implement MFA and lockout rules  

---

### Threat 2: Website Code Injection  
**Risks**  
- Theft and manipulation of data  
- Application downtime and customer impact  

**Runbook**  
- Detect anomaly (via WAF/logs)  
- Quarantine vulnerable code  
- Roll back and patch affected components  
- Conduct a full code audit  
- Notify if PII was exposed  
- Retrain developers on secure coding  

---

### Threat 3: DDoS Attack  
**Risks**  
- Service disruptions  
- Damage to brand reputation  

**Runbook**  
- Detect attack with anomaly-based IDS (e.g., Snort)  
- Engage cloud-based DDoS mitigation tools  
- Block attacking IPs  
- Rate-limit non-critical services  
- Monitor for second-stage attacks  
- Communicate transparently with stakeholders  

---

### Tools and Systems Used  
| Threat                  | Tools/Systems                                      |
|-------------------------|----------------------------------------------------|
| Credential Compromise   | MFA, Okta, CrowdStrike, SIEMs                      |
| Website Code Injection  | Static analysis tools, WAFs, secure coding checklists |
| DDoS Attack             | AWS Shield, CDN services, load balancing           |

---

### Ethical Considerations  
- Limit data collection to incident-relevant information  
- Ensure legal oversight of runbooks and data usage  
- Train all responders in ethical hacking protocols  
- Maintain audit logs for transparency and accountability  

---

### Final Recommendations  
- Align runbooks with NIST Cybersecurity Framework  
- Automate repeatable responses when feasible  
- Conduct periodic red team exercises  
- Continually revise playbooks based on threat landscape  
- Train personnel to understand ethical and technical impact  

---

### References  
- Kovrr (n.d.). *Managing the Risk of Compromised Credentials*.  
- IEEE (2022). *Code Injection Mitigation Models*.  
- IJRASET. *A Study on DDoS Attacks and Their Prevention*.  
