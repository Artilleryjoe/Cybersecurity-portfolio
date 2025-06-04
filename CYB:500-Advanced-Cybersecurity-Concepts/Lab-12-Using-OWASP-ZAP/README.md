# Using OWASP ZAP

## Course
CYB/500: Advanced Cybersecurity Concepts

## Objective
This lab demonstrates how to use OWASP ZAP to conduct web application vulnerability scanning and perform fuzzing-based brute-force attacks.

## Tools Used
- OWASP ZAP
- Damn Vulnerable Web Application (DVWA)

## Procedure
- Identify the IP address of the target machine:
  ```bash
  ifconfig -a eth0 | grep "inet"
- Navigate to DVWA in the browser using the retrived IP.
- In DVWA, set security to **Low**
- Go to **Brute Force** section.'
- In Firefox, configure the proxy settings:
  - HTTP Proxy: ```localhost``` 
  - Port: ```8080```
  - Use this proxy server for all protocols: **Enabled**
- Open OWASP ZAP and let it intercept browser traffic.
- In DVWA, perform a login attempt through **Brute Force**.
- In ZAP, navigate to
  ```Sites > http://<IP Address> > dvwa > vulnerablities```
- Locate:
  ```GET: brute?Login=&password=&username=```
- Right-click and select: ```Attack > Fuzz```
- In the fuzzing window:
  - Load payloads from file:
    ```/root/Documents/fuzz_crack.txt```
  - Add payload > OK
  - Start the Fuzzer
- Once complete, save Raw request:
  ```Save > Request > Header > Filename: ```cracked```
   
## Results
- OWASP ZAP was successfully used to intercept DVWA login requests.
- A fuzzing attack was executed using custom payloads to attempt brute-force login.
- HTTP requests and headers were saved for analysis, demonstrating vulnerability exploitation workflow.
## Lessons Learned
- OWASP ZAP can be effectively used for intercepting, analyzing, and fuzzing HTTP requests.
- Proxy-based traffic inspection allows testers to simulate and observe real-world attack scenarios.
- Fuzzing with payload lists reveals weak points in web authentication mechanisms.
