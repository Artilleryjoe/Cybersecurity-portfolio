# Configuring RAID 5

## Course  
CYB/510 – Enterprise Network Security

## Objective  
This lab demonstrates how to configure a RAID 5 array using multiple virtual disks on a Linux system. RAID 5 provides fault tolerance by distributing parity information across all disks, allowing data recovery in the event of a single drive failure.

## Tools Used  
- Linux OS (Ubuntu or Debian-based)  
- `mdadm` (multi-disk administration tool)  
- At least 3 attached virtual disks  
- Terminal access with `sudo` privileges

## Procedure  

- Install `mdadm` if not already available:
    ```bash
    sudo apt update
    sudo apt install mdadm

- Identify available disks using ```lsblk``` or ```fdisk -l```. Ensure you have at least 3 unused disks (e.g., ```/dev/sdb```, ```/dev/sdc```, ```/dev/sdd```).
- Create the RAID 5 array:
    ```bash
    sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
- Monitor the array's initialization:
    ```bash
    cat /proc/mdstat
- Create a filesystem on the new array:
  ```bash
  sudo mkfs.ext4 /dev/md0
- Mount the RAID Device:
    ```bash
    sudo mkdir -p /mnt/raid5
    sudo mount /dev/md0 /mnt/raid5
- Save the array configuration:
    ```bash
    sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
- Update initramfs to ensure the array is recognized on reboot:
    ```bash
    sudo update-initramfs -u

## Results
- RAID 5 array created with 3 virtual disks using mdadm
- Array initialized successfully and formatted with ext4 filesystem
- Mount point /mnt/raid5 confirmed accessible and persistent
- Redundancy tested by simulating single disk failure (optional) and observing array recovery

## Lessons Learned
- RAID 5 offers a strong balance of redundancy and storage efficiency for enterprise environments
- mdadm is a powerful utility for configuring and managing software-based RAID arrays
- Understanding disk layout, RAID levels, and recovery procedures is essential for secure infrastructure planning
- Proper configuration and testing of RAID arrays ensure data integrity and uptime in case of hardware failure
