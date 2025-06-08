# Monitoring and Logging a Deployed Application

## Course  
CYB/535 – Secure Programming

## Objective  
This lab demonstrates how to monitor and log activity within a deployed Python application using PyCharm. Logging is essential for traceability, debugging, and post-incident analysis, especially when handling sensitive operations such as password hashing.

## Tools Used  
- Python 3.x  
- PyCharm (IDE)  
- hashlib (standard Python module)  
- Logging module (`logging`)

## Procedure  
- Open PyCharm and create a new Python project  
- Write a function to hash a password with a salt using SHA-256:
      ```python
      import hashlib
      import logging

      logging.basicConfig(filename='app.log', level=logging.INFO)
    
      def gen_pass_hash(password, salt):
          try:
              string_to_hash = password + salt
              hash_object = hashlib.sha256(string_to_hash.encode())
              resulting_hash = hash_object.hexdigest()
              logging.info("Password hash generated successfully.")
              return True, resulting_hash
          except Exception as e:
              logging.error("Hashing failed: %s", str(e))
              return False, str(e)


- Create test input and call the function:
    ```python
    thePass = "SecurePass123!"
    theSalt = "@##f80rndmValx23"
    result, resultingHash = gen_pass_hash(thePass, theSalt)
    
    print("Hashing successful:", result)
    print("Hash:", resultingHash)
- Run the script in PyCharm and inspect the generated app.log file
- Confirm log entries include both success and error cases


## Results
The password hashing function successfully logged actions to app.log
On valid input, the log recorded a successful hash generation
Exception handling captured and logged failure scenarios cleanly
PyCharm provided full visibility into console output and log files

## Lessons Learned
- Logging is a critical part of secure software development
- Monitoring output during development helps catch runtime errors early
- Including meaningful log messages ensures effective post-incident analysis
- Logging sensitive values (e.g., passwords) should be avoided — only log metadata or results
