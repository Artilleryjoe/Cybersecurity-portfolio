# Handling Authentication and Authorization Defects

## Course  
CYB/535 – Secure Programming

## Objective  
This lab demonstrates how to identify and remediate common authentication and authorization defects in a simple Python-based web application. These issues can lead to privilege escalation, broken access control, and exposure of sensitive resources.

## Tools Used  
- Python 3.x  
- Flask (minimal web app framework)  
- PyCharm  
- Browser or curl/Postman for manual testing  

## Procedure  
- Create a basic Flask application to simulate login and role-based access:
  ```python
  from flask import Flask, request, redirect, url_for

  app = Flask(__name__)

  users = {
      "admin": {"password": "adminpass", "role": "admin"},
      "user": {"password": "userpass", "role": "user"}
  }

  @app.route('/login', methods=['POST'])
  def login():
      username = request.form.get('username')
      password = request.form.get('password')
      if username in users and users[username]['password'] == password:
          return f"Logged in as {username}"
      return "Invalid credentials", 401

  @app.route('/admin')
  def admin_area():
      # Simulated flaw: No actual session or auth check
      return "Welcome to the admin panel."

  if __name__ == '__main__':
      app.run(debug=True)
- Test the login route using Postman or curl:
    - POST valid and invalid credentials to /login
- Access /admin directly without logging in
- Identify the lack of:
  - Session handling
  - Role validation
  - Input sanitization
- Remediate by adding basic authentication and access control:
    ```python
    from flask import session, redirect

    app.secret_key = 'replace_this'
    
    @app.route('/login', methods=['POST'])
    def login():
        username = request.form.get('username')
        password = request.form.get('password')
        if username in users and users[username]['password'] == password:
            session['username'] = username
            session['role'] = users[username]['role']
            return f"Logged in as {username}"
        return "Invalid credentials", 401

    @app.route('/admin')
    def admin_area():
        if session.get('role') != 'admin':
            return redirect(url_for('login'))
        return "Welcome to the admin panel."
    
## Results
- Initially, anyone could access protected routes without authentication
- Lack of session and role checks revealed classic access control vulnerabilities
- After remediation, access to /admin was properly restricted based on session role
- Confirmed that unauthenticated or unauthorized users were redirected appropriately

## Lessons Learned
- Authentication and authorization are distinct but equally critical components
- Role checks must be enforced on the server side — client-side logic can be bypassed
- Sessions or tokens should be used to track login state securely
- Failing to validate access rights opens the door to privilege escalation and data leaks

