# Lab 22: Attacking a Website Using XSS and Custom Payloads (DVWA)

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to exploit a Cross-Site Scripting (XSS) vulnerability using the Damn Vulnerable Web Application (DVWA). Custom payloads are used to trigger script execution in the browser to highlight the security risks of unsanitized user input.

## Tools Used  
- DVWA (Damn Vulnerable Web Application)  
- Kali Linux (or similar with LAMP stack and DVWA setup)  
- Web browser with developer tools  
- Custom JavaScript payloads

## Procedure  
- Start DVWA by launching Apache and MySQL services:
  ```bash
  sudo service apache2 start
  sudo service mysql start
- Navigate to DVWA in browser:
    http://localhost/dvwa/
- Log in with default credentials (admin / password)
- Set security level to Low under DVWA Security tab
- Navigate to XSS (Reflected) module
- In the input field, enter a basic XSS payload:
  ```html
  <script>alert('XSS')</script>
- Submit and confirm that an alert box appears
- Try more advanced payloads:
  ```html
  <svg onload=alert('SVG XSS')>
  <img src=x onerror=alert('XSS 2')>
  <iframe src="javascript:alert('XSS via iframe')"></iframe>
- Observe browser behavior and test browser defenses
- Use browser dev tools (F12) to inspect page source and confirm injection points
## Results
- DVWA successfully rendered user input without sanitization
- Alert boxes triggered as proof-of-concept for script execution
- Custom payloads bypassed basic filtering mechanisms
- DOM inspection confirmed that user input was embedded into the page’s HTML

## Lessons Learned
- XSS vulnerabilities allow attackers to execute arbitrary JavaScript in a victim's browser
- Reflected XSS is often found in search bars, error messages, and form submissions
- Input sanitization and output encoding are essential to prevent XSS
- Tools like DVWA provide a safe environment to test and understand real-world attack vectors
