# Staging a Persisted XSS Attack on an Admin Function

## Course  
CYB/535 – Secure Programming

## Objective  
This lab demonstrates how a persisted (stored) cross-site scripting (XSS) attack functions and why it poses a serious risk, especially in administrative panels. The goal is to simulate injection of malicious JavaScript into a database-backed comment field, which executes when viewed by an admin.

## Tools Used  
- Python 3.x  
- Flask  
- SQLite  
- Browser (any modern browser with developer tools)  
- PyCharm  

## Procedure  
- Set up a simple Flask application with a basic comment form and admin viewer:
  ```python
  from flask import Flask, request, render_template_string
  import sqlite3

  app = Flask(__name__)

  conn = sqlite3.connect('comments.db', check_same_thread=False)
  conn.execute('CREATE TABLE IF NOT EXISTS comments (content TEXT)')
  conn.commit()

  @app.route('/', methods=['GET', 'POST'])
  def comment():
      if request.method == 'POST':
          comment = request.form.get('comment')
          conn.execute('INSERT INTO comments (content) VALUES (?)', (comment,))
          conn.commit()
      return '''
          <form method="post">
              <textarea name="comment"></textarea>
              <input type="submit" value="Submit">
          </form>
      '''

  @app.route('/admin')
  def admin_view():
      cursor = conn.execute('SELECT content FROM comments')
      comments = cursor.fetchall()
      display = ''.join(f'<p>{row[0]}</p>' for row in comments)
      return render_template_string(display)

  if __name__ == '__main__':
      app.run(debug=True)
- Run the application locally in PyCharm

- Submit the following malicious input in the comment form:
    ```html
    <script>alert('XSS by user');</script>
- Navigate to the /admin route to simulate an admin user reviewing submitted comments

- Observe the alert box firing in the browser, proving execution of stored script

## Results
- The application accepts and stores unsanitized user input
- Visiting the admin panel causes the stored script to execute in the browser
- The stored script demonstrates how a malicious user can inject persistent code that       executes in another user's context
- The application lacks output encoding, input validation, and content sanitization

## Lessons Learned
- Persistent XSS can compromise administrative sessions or inject permanent backdoors into web interfaces
- Storing user input without sanitization introduces critical vulnerabilities
- Preventing XSS requires encoding untrusted output and validating user input at all stages
- Admin panels are high-value targets and must be hardened against all injection-based attacks
