🐧 Linux File System

The Linux File System defines how data and files are organized and accessed in a Linux operating system.
Unlike Windows (which uses drives like C:\ or D:\), Linux uses a single tree structure that starts from the root directory /.

كل حاجة في لينكس تعتبر ملف — سواء كانت فولدر، أمر، أو حتى قطعة هاردوير.
وده جزء من فلسفة لينكس: “Everything is a file”.



🌳 File System Hierarchy (Tree Structure)
<pre>
/
├── bin        → Essential system commands (ls, cp, mv, cat)
├── boot       → Boot files and Linux kernel
├── dev        → Device files (e.g. hard drives, USBs)
├── etc        → System and application configuration files
├── home       → Users’ home directories
│   ├── amr
│   └── guest
├── lib        → Shared libraries for programs in /bin and /sbin
├── media      → Mount points for removable media (USB/CD)
├── mnt        → Temporary mount point for manual mounting
├── opt        → Optional or third-party software
├── proc       → Virtual directory containing process and system info
├── root       → Home directory for the root (admin) user
├── run        → Runtime data for system services
├── sbin       → System binaries (used by root user)
├── srv        → Data for services like FTP or web servers
├── tmp        → Temporary files
├── usr        → User programs, documentation, libraries
│   ├── bin
│   ├── lib
│   └── share
└── var        → Variable data such as logs, mail, cache
    ├── log
    ├── mail
    └── tmp
</pre>



📘 Directory Descriptions
| Directory         | Description                                                            |
| ----------------- | ---------------------------------------------------------------------- |
| `/`               | The root of the entire file system. Every file and folder starts here. |
| `/home`           | Contains personal directories for each user (e.g., `/home/amr`).       |
| `/root`           | The administrator’s (root user) home directory.                        |
| `/bin`            | Essential Linux commands available to all users.                       |
| `/sbin`           | System commands for administration (e.g., `shutdown`, `reboot`).       |
| `/etc`            | Configuration files for the system and software.                       |
| `/var`            | Variable files such as logs, cache, and mail.                          |
| `/tmp`            | Temporary files used by programs (cleared on reboot).                  |
| `/usr`            | User-installed software, libraries, and documentation.                 |
| `/lib`            | Shared libraries needed by binaries in `/bin` and `/sbin`.             |
| `/boot`           | Files required to boot the system (kernel, GRUB).                      |
| `/dev`            | Represents devices as files (like `/dev/sda1` for disks).              |
| `/mnt` & `/media` | Mount points for external devices.                                     |
| `/opt`            | Third-party or optional software packages.                             |
| `/proc`           | Virtual filesystem showing running processes and system info.          |



💡 Key Notes

Linux is case-sensitive — /Home ≠ /home.
Everything (even hardware) is treated as a file.
System configuration is stored in plain text files under /etc/.
The command tree / (after installing tree) displays the structure visually.
Permissions control who can read, write, or execute each file.


🚀 Summary

The Linux file system is built around simplicity and consistency —
everything starts from /, and every component of the system (commands, configuration, hardware) is accessed through it.
