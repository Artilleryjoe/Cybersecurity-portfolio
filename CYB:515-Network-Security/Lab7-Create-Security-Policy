# Creating a Security Policy Using Windows Administrative Tools

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to use built-in Windows Administrative Tools to define and enforce a local security policy. Security policies control user rights, password enforcement, auditing, and other key behaviors that support a secure enterprise environment.

## Tools Used  
- Windows 10 (Pro or Enterprise)  
- Local Security Policy Editor (`secpol.msc`)  
- Group Policy Editor (`gpedit.msc`)  
- Event Viewer (for auditing verification)

## Procedure  

- Open the Local Security Policy Editor:
  - Press `Win + R`, type `secpol.msc`, and press Enter

- Configure key security policies:
  - Navigate to **Account Policies > Password Policy**
    - Enforce password history (e.g., 24 passwords remembered)
    - Maximum password age: 60 days
    - Minimum password length: 12
    - Password complexity requirements: Enabled

  - Navigate to **Local Policies > User Rights Assignment**
    - Deny logon locally: Add unauthorized or guest users
    - Allow log on locally: Restrict to required user groups only

  - Navigate to **Local Policies > Audit Policy**
    - Audit logon events: Success and Failure
    - Audit object access: Success and Failure

- Optionally, use `gpedit.msc` to make broader security changes under:
  - **Computer Configuration > Windows Settings > Security Settings**

- Apply changes and reboot if necessary

- Verify:
  - Attempt to create a weak password (should be denied)
  - Check `Event Viewer > Security` logs for audit entries

## Results  
- Password policy settings were successfully applied and enforced  
- Local logon rights were restricted to authorized groups  
- Audit logs showed successful and failed logon attempts  
- System behavior aligned with enterprise password and access standards

## Lessons Learned  
- Windows Administrative Tools provide fine-grained control over security configurations  
- Password complexity, rotation, and access restrictions are essential first-line defenses  
- Auditing policies support visibility into user actions and system access  
- These tools support both standalone hardening and domain-based enforcement in enterprise environments
