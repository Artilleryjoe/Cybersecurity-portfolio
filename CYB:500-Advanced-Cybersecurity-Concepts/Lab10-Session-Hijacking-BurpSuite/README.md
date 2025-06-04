# Performing Session Hijacking Using Burp Suite

## Course
CYB/500: Advanced Cybersecurity Concepts

## Objective 
This lab demonstrates how to perform a session hijacking using Burp Suite by intercepting and managing a session token to manipulate authenticated sessions.

## Tools Used
- Burp Suite
- Damn Vulnerable Web Application (DVWA)
- Firefox ESR

## Prodedure
- Launch Burp Suite (default settings).
-In Burp, navigate to the Proxy tab to enable HTTP traffic capture.
-Open Firefox ESR and navigate to:
    ```text
    http://localhost/dvwa
- In Firefox, configure the browser to route traffic through Burp's proxy:
- Manual Proxy Configuration
- HTTP Proxy: 127.0.0.1
- Port: 8080
- Check: “Use this proxy server for all protocols”
- Clear: No Proxy for box
- Log in to DVWA using known credentials.
- In Burp Suite, observe the raw HTTP request under the Raw tab.
- Username and password are visible in plain text during login.
- Save the intercepted raw request as:
    ```text
    /root/hijack.xml

## Results
- Successfully intercepted HTTP login request containing session credentials.
- Saved raw HTTP data to a file for potential reuse.
- Demonstrated how session hijacking can be initiated through intercepted credentials.
## Lessons Learned
- Burp Suite provides a powerful platform for intercepting and manipulating web session       traffic.
- Improper session handling and lack of HTTPS expose applications to session hijacking.
- Always use encrypted communication and secure cookies to protect user sessions.
