# Conducting CSRF (Cross-Site Request Forgery) Attack

## Course  
CYB/550 – Technical Enterprise Security

## Objective  
This lab demonstrates how a Cross-Site Request Forgery (CSRF) attack works by exploiting the trust a web application places in a user's browser session. The goal is to simulate unauthorized actions taken without the user’s consent.

## Tools Used  
- Damn Vulnerable Web Application (DVWA)  
- Web browser  
- Burp Suite or raw HTML payload  
- Localhost environment or DVWA VM

## Procedure  
- Launch DVWA and set security level to “Low” under Security tab  
- Log into DVWA using default credentials (admin/password)  
- Navigate to the CSRF module in the menu  
- Note the form parameters used for a password change request  
- Create a malicious HTML form:
    ```html
    <form action="http://[DVWA-IP]/vulnerabilities/csrf/" method="POST">
      <input type="hidden" name="password_new" value="hackedpass123">
      <input type="hidden" name="password_conf" value="hackedpass123">
      <input type="submit" value="Click Me">
    </form>
- Host the form on a separate server or open it locally
- While logged into DVWA, open the attacker form in the same browser session
- Submit the form and verify that the password was changed without consent

## Results
- Password change executed successfully without any confirmation
- No CSRF token or session validation detected
- DVWA account was fully compromised via a single forged request

## Lessons Learned
- CSRF exploits trust established by a valid session token stored in the browser
- Mitigation techniques include:
  - CSRF tokens embedded in forms
  - SameSite cookie attributes
  - Referer header checks
- Developers must never rely solely on cookies for authentication of critical actions
