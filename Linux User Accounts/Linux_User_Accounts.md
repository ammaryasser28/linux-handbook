👤 Linux User Accounts

Linux is a multi-user system, which means multiple users can use the system simultaneously.
Managing user accounts and permissions is a key skill for system administration.

🏷️ 1. Viewing Users and Groups
| Command           | Description                                    |
| ----------------- | ---------------------------------------------- |
| `whoami`          | Show the current logged-in user                |
| `id`              | Show user ID (UID), group ID (GID), and groups |
| `groups username` | List all groups a user belongs to              |
| `cat /etc/passwd` | Display all users on the system                |
| `cat /etc/group`  | Display all groups on the system               |


➕ 2. Creating and Modifying Users
| Command                           | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| `sudo adduser username`           | Create a new user (interactive, sets password) |
| `sudo useradd username`           | Create a new user (non-interactive)            |
| `sudo passwd username`            | Set or change user password                    |
| `sudo usermod -aG group username` | Add user to a group                            |
| `sudo deluser username`           | Remove a user (Debian/Ubuntu)                  |
| `sudo userdel username`           | Remove a user (other distros)                  |


🛡 3. Managing Groups
| Command                               | Description           |
| ------------------------------------- | --------------------- |
| `sudo groupadd groupname`             | Create a new group    |
| `sudo groupdel groupname`             | Delete a group        |
| `sudo usermod -aG groupname username` | Add user to a group   |
| `groups username`                     | Show groups of a user |


🔑 4. Switching Users
| Command        | Description                                |
| -------------- | ------------------------------------------ |
| `su username`  | Switch to another user (requires password) |
| `sudo -i`      | Switch to root user                        |
| `sudo command` | Run a single command as root               |


💡 Tips

Always use sudo for administrative tasks.
Avoid logging in directly as root; use sudo instead.
Keep passwords strong and unique.
Regularly check /etc/passwd and /etc/group for system auditing.
