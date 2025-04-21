# What to learn for Linux 
 - Boot Process
 - File System
 - Permisssions
 - Systemd
 - Package Managers
 - Debugging Skills
 - Finding / Reading Logs
 - Networking Fundamentals 
 - Bash Scripting 

 Learn linux to the point where you can install Arch Linux and exactly what you are doing.

 # Certifications 
 -LPIC-1

 # What is Linux?
 - Linux is an open-source operarting system that powers a wide range of devices, from smartphones to servers

 # Key Features of Linux
 * Stabiity
 * Security
 * Customizability
 * Compatibitly 
 * Performance



# What is Terminal?
* Terminal - is a program or envriroment that provides a graphical or textual interface for interacting with computer.

Purpose :  * Acts as the interface between the user and the shell.
           * Accepts inputs (Commands) and dispalys output ( Result of commands). 

Analogy - The screen displaying instructions.

# What is Shell?
* Shell - is a command-line interpreter that processes commands enetered by user and passes them to operating system for execution. It is a software layer that sits between the user and the kernel of the operating system.

Purpose :  * Exceutes commands and scripts 
           * Provide features like command history, variable management, and scripting capabilities. 
           
Analogy - The brain interpreting instructions.

- The default shell for UBUNTU is bash (Bourne Again SHell).

- You can confirm the shell for your user by running:
                                                    * echo $SHELL

* Zsh (Z shell) is is a powerful and feature-rich command-line shell for UNIX-like operating systems. It is an alternative to other popular shells like bash or fish and is known for its advanced features, flexibility, and user-friendly design.




# Understanding Linux Boot Processes 

* BIOS (Legacy) = Basic Input Output System: 
 - Is the firmware that initializes hardware when you turn on your computer and starts the boot process. It’s the first thing that runs before the operating system (like Linux) .


* UEFI (Modern) = Unified Extensible Firmware Interface is a modern firmware interface that serves as a bridge between a computer’s hardware and its operating system. It is the successor to the older BIOS (Basic Input/Output System) and provides more advanced capabilities for booting and managing system firmware.

ANALOGY = BIOS like a conductor of an orchestra. Before a concert starts, the conductor ensures all instruments (hardware) are in place and working. Then, they give the green light to start the music (booting into Linux).

* How BIOS Works in Linux Boot Process:
 1. Power On – You press the power button, and BIOS wakes up.

 2. POST (Power-On Self-Test) – BIOS checks if essential hardware (CPU, RAM, keyboard, etc.) is working.

 3. Boot Order Check – BIOS looks for a bootable device (like a hard drive, SSD, or USB).

 4. Loads Bootloader - BIOS finds the Master Boot Record (MBR) or EFI System Partition (ESP) on the bootable device.
It loads the first 512 bytes of the boot sector, which contains:
	•	A small piece of code to start the bootloader (GRUB, Syslinux, systemd-boot).
	•	Partition table (MBR systems only).
If the system uses MBR (Legacy BIOS Boot):
	•	BIOS loads the bootloader from the first sector (MBR) of the disk (e.g., /dev/sda).
If the system uses UEFI (Modern Boot Method):
	•	The BIOS firmware (UEFI) loads the EFI bootloader from the EFI System Partition (ESP) (e.g., /boot/efi/EFI/ubuntu/grubx64.efi).

5. Bootloader Loads Linux Kernel- 	Once the bootloader is loaded into memory, BIOS passes control to it.
	•	The bootloader (e.g., GRUB) takes over to:
	•	Display boot menu options.
	•	Load the Linux kernel.
	•	Initialize the RAM disk (initrd/initramfs).
	•	Proceed to system startup.


## Linux Boot Process Flowchart (With Comments)

```plaintext
+--------------------+
| Power On          |  <-- System is powered on
+--------------------+
        |
        v
+--------------------+
| BIOS / UEFI       |  <-- Firmware initializes hardware
| - POST check      |  <-- Runs Power-On Self-Test (POST)
| - Initialize HW   |  <-- Detects CPU, RAM, Storage, etc.
| - Detect boot dev |  <-- Finds bootable device (HDD/SSD)
+--------------------+
        |
        v
+----------------------+
| Bootloader (GRUB)   |  <-- Loads the boot menu
| - Loads Kernel      |  <-- Selects and loads Linux kernel
| - Loads initramfs   |  <-- Loads initial RAM disk (initrd/initramfs)
+----------------------+
        |
        v
+----------------------+
| Kernel Initialization |  <-- Linux kernel takes control
| - Detects Hardware   |  <-- Loads device drivers
| - Mounts root fs     |  <-- Root filesystem is mounted
| - Starts init system |  <-- systemd (or init) is executed
+----------------------+
        |
        v
+----------------------+
| Init System (systemd)|  <-- Manages startup processes
| - Starts services    |  <-- Activates necessary daemons
| - Manages targets    |  <-- Defines runlevels (multi-user, GUI, etc.)
| - User login ready   |  <-- Prepares system for user interaction
+----------------------+
        |
        v
+----------------------+
| User Space Active   |  <-- System is fully operational
| - CLI or GUI        |  <-- User logs in (terminal or desktop)
| - Applications Load |  <-- System is ready for use
+----------------------+
```
 

 # systemd Notes

## 📌 1. What is `systemd`?
`Systemd` is the **init system** used in most modern Linux distributions to manage services, processes, and system startup. It replaces older init systems like **SysVinit** and **Upstart** and provides better performance, parallelization, and service dependency management.

---

## 📌 2. Key Concepts in `systemd`

- **Units**: `systemd` manages everything as a **unit**. The most common unit types are:
  - **Service units (`.service`)** → Manages daemons (e.g., `nginx.service`)
  - **Target units (`.target`)** → Groups of services (like runlevels)
  - **Timer units (`.timer`)** → Schedule tasks like `cron`
  - **Mount units (`.mount`)** → Manages file system mounts
  - **Device units (`.device`)** → Tracks hardware devices

---

## 📌 3. Managing Services with `systemd`

```sh
systemctl status nginx       # Check service status
systemctl start nginx        # Start a service
systemctl stop nginx         # Stop a service
systemctl restart nginx      # Restart a service
systemctl reload nginx       # Reload configuration (without restart)
systemctl enable nginx       # Enable service at boot
systemctl disable nginx      # Disable service at boot


## 📌 8. Summary of Commands

| Command                          | Description                                |
|----------------------------------|--------------------------------------------|
| `systemctl status <service>`     | Check the status of a service             |
| `systemctl start <service>`      | Start a service                           |
| `systemctl stop <service>`       | Stop a service                            |
| `systemctl restart <service>`    | Restart a service                         |
| `systemctl reload <service>`     | Reload service configuration              |
| `systemctl enable <service>`     | Enable service to start on boot           |
| `systemctl disable <service>`    | Disable service from starting on boot     |
| `journalctl -u <service>`        | View logs for a specific service          |
| `journalctl -f -u <service>`     | Follow live logs                          |
| `systemctl list-units --type=target` | Check system boot status               |
| `systemctl set-default <target>` | Change default runlevel (target)          |
| `systemctl daemon-reload`        | Reload systemd configurations             |
| `systemctl daemon-reexec`        | Restart systemd daemon                    |
| `systemd-analyze blame`          | Debug slow startup issues                 |


# 🎵 Analogy for `systemd`: The Orchestra Conductor

Imagine a **symphony orchestra** preparing for a performance.

- The **conductor (`systemd`)** is responsible for **starting, stopping, and managing** all the **musicians (`services`)**.
- Each **musician (service unit)** plays a specific role, like:
  - `nginx.service` → Web server
  - `mysql.service` → Database
  - `ssh.service` → Remote access
- The **conductor ensures** that musicians **start in the correct order** (dependencies) and **keep playing correctly** (monitoring).

---

## 🎼 How It Works

- When the **conductor arrives (system boots up)**, they **signal musicians to start playing (services start)**.
- If a musician is **late (fails to start)**, the conductor **tries to restart them**.
- Some musicians **must start before others** (dependency management).
- If a musician needs to **adjust their tempo (reload config)**, the conductor gives them a **new instruction**:

```sh
systemctl reload nginx


 # File System


## 1. Linux File System Basics
- **Everything is a file** (devices, directories, configs).
- **Hierarchical structure** with `/` (root) at the top.
- **Important directories**:
  - `/etc/` → System configurations
  - `/var/` → Logs
  - `/tmp/` → Temporary files
  - `/dev/` → Device files
  - `/mnt/ & /media/` → Mount points

---

## 2. Common Linux File Systems

| File System | Description | Use Case |
|-------------|------------|----------|
| **ext4** | Default, stable, supports large files | General Linux |
| **XFS** | High performance, journaling | Databases |
| **Btrfs** | Snapshots, checksums | Experimental storage |
| **ZFS** | Built-in RAID, scalable | Cloud & storage |
| **tmpfs** | RAM-based, fast | Temporary storage |
| **FAT32/exFAT** | Cross-platform | USB drives |
| **NTFS** | Windows FS (Linux supports via `ntfs-3g`) | Dual-boot |

---

## 3. Mounting and Managing File Systems

Mounting is the process of attaching a storage device (e.g., hard drive, USB, SSD) to a directory so the operating system can access its files.

Analogy = Mounting in Linux is like checking into a hotel with a suitcase (storage device). The hotel room (mount point) is where you unpack and access your belongings (files). Unmounting is like checking out, where you pack up and leave, ensuring nothing is left behind. If you reserve the same room every visit (fstab entry), your suitcase will always be placed there automatically.

# Linux Mounting Commands Summary

| Command                          | Description                               |
|----------------------------------|-------------------------------------------|
| `df -h`                          | Shows mounted file systems.              |
| `lsblk -f`                       | Displays file systems of disks.          |
| `blkid`                          | Lists UUID and file system type.         |
| `mkdir /mnt/mydisk`              | Creates a mount point.                   |
| `mount /dev/sdb1 /mnt/mydisk`    | Mounts `/dev/sdb1` to `/mnt/mydisk`.     |
| `umount /mnt/mydisk`             | Unmounts `/mnt/mydisk`.                  |
| `umount -l /mnt/mydisk`          | Forces unmount if the disk is busy.      |
| `fuser -m /mnt/mydisk`           | Shows processes using the mounted disk.  |
| `nano /etc/fstab`                | Edits the auto-mount configuration.      |
| `mount -a`                       | Applies all `/etc/fstab` mounts.         |




