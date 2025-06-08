
# Lab 17: Using Apktool to Decode and Analyze an APK File

## Course  
CYB/500: Advanced Cybersecurity Concepts

## Objective  
This lab demonstrates how to use Apktool to decode an Android application package (APK) file, making it possible to inspect its resources, manifest file, and underlying smali code for analysis or reverse engineering.

## Tools Used  
- Apktool  
- Android Debug Bridge (ADB) (optional)  
- Linux terminal  
- A test APK file (e.g., `example.apk`)

## Procedure  
- Change to the working directory:  
  ```bash
  cd ~/Documents
- Use Apktool to decode the APK file:
    ```bash
    apktool d example.apk
- List the contents of the output folder:
    ```bash
    ls example
- Review decompiled contents:
  - ```AndroidManifest.xml``` - app permissions, components
  - ```res/``` - UI resources (layouts, strings, images)
  - ```smali``` - low-level representaion of Dalvik bytecode
- Optionally inspect suspicious code or hardcoded values (e.g., API keys, URLs)
  
## Results
- APK successfully decompiled into a readable directory structure
- AndroidManifest.xml reviewed for permissions and exposed components
- Smali code identified and explored for possible security issues
- Decompiled resources matched original app structure

## Lessons Learned
- Apktool is a powerful utility for analyzing Android apps without source code
- Decompiled APKs reveal app structure, logic flow, and potential security flaws
- Reverse engineering is essential for understanding third-party or malicious apps
- Ethical use of tools like Apktool is important in security testing and research
