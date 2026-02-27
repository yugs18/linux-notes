# Linux Directory Structure

## /
The root directory.

All files and directories in Linux are located under the root `/`.  
Absolute paths always start from `/`.

---

## /bin – Essential User Binaries
Contains essential command binaries required for basic system operation.

Examples:
- ls
- cp
- mv
- cat

---

## /dev – Device Files
Contains special device files.

These are virtual files representing hardware devices (e.g., disks, terminals).  
They are not physically stored data files.

---

## /etc – Configuration Files
Contains system-wide configuration files.

Used mainly by:
- System administrators
- Services
- Core system components

---

## /usr – User Programs & Data
Contains user-space programs and read-only data.

Most files here are read-only for normal users.

Subdirectories:

- `/usr/bin` → User commands
- `/usr/sbin` → Administrative commands
- `/usr/lib` → Libraries
- `/usr/share` → Shared data (docs, icons, etc.)

---

## /home – User Home Directories
Contains personal directories for each user.

Example:
- `/home/username`

---

## /lib – Shared Libraries
Contains shared libraries required by binaries in `/bin` and `/sbin`.

---

## /sbin – System Binaries
Contains essential system binaries.

Typically used by:
- Root
- System administrators

---

## /tmp – Temporary Files
Stores temporary files.

Usually cleared on reboot.

---

## /var – Variable Data
Contains files that change frequently.

Examples:
- Logs (`/var/log`)
- Cache
- Mail
- Spool files

---

## /boot – Boot Files
Contains:
- Kernel files
- Bootloader files (GRUB)
- Initial RAM disk images

---

## /proc – Process & Kernel Information
A virtual filesystem.

Contains information about:
- Running processes
- Kernel parameters
- System hardware

---

## /opt – Optional Software
Used for installing third-party software not managed by the default package manager.

---

## /root – Root User Home
Home directory of the root user.

---

## /media – Removable Media
Mount point for removable devices like USB drives.

---

## /mnt – Temporary Mount Point
Used by administrators to manually mount filesystems.

---

## /srv – Service Data
Contains data served by system services.
Example:
- Web server files

## /sys – System & Hardware Information

A virtual filesystem that provides structured information about:

- Hardware devices
- Drivers
- Kernel subsystems

It is created dynamically by the kernel at runtime.

Unlike regular files, these are interfaces to kernel data.

Examples:
- /sys/class → Device classes
- /sys/devices → Hardware devices
- /sys/kernel → Kernel information