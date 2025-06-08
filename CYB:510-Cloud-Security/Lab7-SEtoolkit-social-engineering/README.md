# Using SEToolkit to Plan a Social Engineering Attack

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use the Social-Engineer Toolkit (SEToolkit) to simulate and plan a social engineering attack in a controlled lab environment. The goal is to understand the capabilities of SET and how attackers exploit human trust to gain unauthorized access.

**Disclaimer:** This lab was conducted in a virtual lab environment for educational purposes only. No unauthorized access or real-world targeting occurred.

## Tools Used  
- SEToolkit (Social-Engineer Toolkit)  
- Kali Linux (or Parrot OS)  
- Target browser on a virtual machine  
- Apache web server (optional for custom hosting)

## Procedure  

- Launch SEToolkit on Kali Linux:
  ```bash
  sudo setoolkit
- Accept the disclaimer, then choose:
  - Option 1: Social-Engineering Attacks
  - Option 2: Website Attack Vectors
  - Option 3: Credential Harvester Attack Method
  - Option 2: Site Cloner
- Enter the IP address of the attacking machine (e.g., ```192.168.1.100```)
- Enter the URL to clone (e.g., ```https://login.facebook.com``` or a benign test site)
- SET will clone the site and host it locally. Send the IP to the target in a phishing-style scenario.
- On the target machine (in a controlled lab), open a browser and visit the attacker's IP:
    ```bash
    http://192.168.1.100
- Enter dummy credentials to observe how SET captures them in real time.
- Review captured data in the terminal or under:
    ```bash
    /var/www/html/post.php

## Results
- SET successfully cloned the specified login page
- Target entering credentials triggered credential capture in terminal output
- Demonstrated how a legitimate-looking site can be used to phish information
- Reinforced the need for user awareness and secure communication practices

## Lessons Learned
- SEToolkit is a powerful demonstration tool for ethical hacking and training
- Social engineering remains one of the most effective attack vectors due to human vulnerability
- Organizations must train users to verify links, URLs, and SSL certificates before submitting sensitive data
- Multi-factor authentication and browser security tools reduce the impact of credential theft
