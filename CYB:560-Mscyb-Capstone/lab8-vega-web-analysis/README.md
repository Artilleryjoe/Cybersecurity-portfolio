# Using Vega for Web Application Security Analysis

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to use **Vega**, a GUI-based vulnerability scanner, to analyze web applications for common security issues such as XSS, SQL Injection, and sensitive data exposure. The goal is to identify weak points in a live or test web app to support secure development and remediation.

## Tools Used  
- Vega Vulnerability Scanner (GUI-based)  
- Target Web Application (e.g., DVWA, Mutillidae, or live test site)  
- Kali Linux or Windows machine with Java installed  
- Web browser for manual follow-up

## Procedure  
- Install Vega (Java-based package from official source or Kali repo)  
- Launch the application:
    ```bash
    ./Vega
- Create a new scan:
- Input target URL
- Select modules: XSS, SQL Injection, Shellshock, Directory Traversal, etc.
- Run automated scan
- Observe results in the Alert tab:
- Review severity, affected URLs, and description of each finding
- Explore the request/response pairs for manual verification
- Optionally, launch Vega’s proxy to intercept and analyze browser traffic in real-time
- Document findings and recommended mitigation for each confirmed vulnerability

## Results
- Identified multiple potential XSS and parameter injection points
- Observed lack of input validation on search and login forms
- Detected session tokens transmitted without secure flag
- Manual verification confirmed some false positives, which were dismissed after context review

## Lessons Learned
- Vega is effective for initial reconnaissance and discovery but requires human follow-up
- GUI tools provide quick wins, but deeper analysis benefits from combined use with manual testing or Burp Suite
- Automated tools can generate false positives — understanding context is key
- Even simple web apps often contain exploitable vulnerabilities if not securely developed
