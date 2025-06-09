# Resetting the Root Password on a Linux System

## Course  
CYB/560 – MS Cybersecurity Capstone

## Objective  
This lab demonstrates how to securely reset the root password on a Linux system using GRUB bootloader recovery mode. This is an essential recovery procedure for administrators locked out of privileged access or responding to credential loss.

## Tools Used  
- Linux virtual or physical machine  
- GRUB bootloader access  
- Terminal with root shell access (post-reset)

## Procedure  
- Reboot the system and interrupt GRUB during startup  
- Highlight the default boot entry and press `e` to edit  
- Navigate to the line starting with `linux` and append:
      ```bash
      init=/bin/bash
- Press Ctrl+X or F10 to boot into single-user mode
- Remount the root filesystem with write permissions:
      ```bash
      mount -o remount,rw /
 Reset the root password:
      ```bash
      passwd
- Enter and confirm the new root password
Remount the filesystem as read-only (optional but recommended):
      ```bash
      mount -o remount,ro /
Reboot the system:
      ```bash
      exec /sbin/init

## Results
Gained access to a root shell through GRUB bootloader
Successfully changed the root password without prior credentials
Verified ability to log in as root post-boot
Maintained system integrity during the process

## Lessons Learned
Boot-level access is critical for password recovery, highlighting the need for physical security
Resetting root credentials is powerful and should be audited or disabled in production systems
Consider encrypting disks and restricting GRUB editing to prevent unauthorized resets
Always document and communicate password changes in managed environments
