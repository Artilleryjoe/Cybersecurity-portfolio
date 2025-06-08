# Creating a Virtual Machine and Installing Ubuntu Using Hyper-V Manager

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to create a new virtual machine (VM) and install Ubuntu Linux using Hyper-V Manager. This forms the foundation for building secure, isolated virtual environments for enterprise network testing and simulation.

## Tools Used  
- Hyper-V Manager (Windows 10/11)  
- Ubuntu ISO (e.g., Ubuntu 22.04 LTS)  
- Host machine with virtualization enabled

## Procedure  

- Enable Hyper-V if not already active:
  - Open "Turn Windows features on or off"
  - Check "Hyper-V" and restart the system if prompted

- Open Hyper-V Manager and create a new virtual machine:
  - Click **New > Virtual Machine**
  - Name the VM (e.g., `Ubuntu-Test-VM`)
  - Assign memory (recommend 2048–4096 MB)
  - Select virtual switch (default or external for internet access)
  - Create a virtual hard disk (20 GB or more)
  - Attach the Ubuntu ISO as a boot device

- Start the VM to begin Ubuntu installation:
  - Choose language and keyboard layout
  - Select normal installation
  - Create a user, password, and computer name
  - Allow Ubuntu to handle disk partitioning
  - Complete the installation and reboot when prompted

- Post-installation:
  - Log in and run updates:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
  - Optionally install `openssh-server` for remote access:
    ```bash
    sudo apt install openssh-server
    ```

## Results  
- Virtual machine created successfully with allocated resources  
- Ubuntu installed and running within Hyper-V  
- Network connectivity confirmed via browser and ping  
- System updated and ready for secure lab use

## Lessons Learned  
- Hyper-V provides a reliable environment for Linux VM hosting directly within Windows  
- Combining VM creation and OS installation streamlines lab setup  
- Regular updates and snapshotting of VMs help ensure consistency across experiments  
- Virtualization is an essential part of enterprise network design, testing, and security
