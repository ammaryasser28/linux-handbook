👤 Linux User Accounts

Linux is a multi-user system, which means multiple users can use the system simultaneously.
Managing user accounts and permissions is a key skill for system administration.

| Type             | Approx. UID Range | Purpose                                         |
| ---------------- | ----------------: | ----------------------------------------------- |
| root (superuser) |                 0 | Full system administration                      |
| system users     |           1 – 999 | Accounts for system services (usually no login) |
| regular users    |             1000+ | Normal human user accounts                      |

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
| Command            | Description                                                                                                                                                        |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`su`**           | Switch to the **root user** (or another user) **without loading their environment**. You stay in the same directory and keep the current environment variables.    |
| **`su -`**         | Switch to the **root user** (or another user) **and load their full login environment** (like a fresh login). Changes directory to the user’s home (e.g. `/root`). |
| **`su username`**  | Switch to a specific user (requires that user’s password). Keeps the current environment.                                                                          |
| **`sudo command`** | Run **a single command** as root (or another user) **without switching sessions**. Uses your own password (if configured in `/etc/sudoers`).                       |
| **`sudo -i`**      | Open an **interactive root shell** — similar to `su -`, but uses your credentials through `sudo` instead of asking for the root password.                          |


💡 Tips

Always use sudo for administrative tasks.
Avoid logging in directly as root; use sudo instead.
Keep passwords strong and unique.
Regularly check /etc/passwd and /etc/group for system auditing.


Ways to Grant Root / Administrative Privileges to a User
| Method                                                           | Command Example                       | Safety        | Notes                                                             |
| ---------------------------------------------------------------- | ------------------------------------- | ------------- | ----------------------------------------------------------------- |
| **Editing `/etc/sudoers` manually (nano, vim, …)**               | `sudo nano /etc/sudoers`              | ❌ Risky       | Any syntax error can break sudo completely                        |
| **Using `visudo` (recommended way)**                             | `sudo visudo`                         | ✅ Safe        | Checks syntax before saving — prevents breaking sudo              |
| **Creating a sudoers file under `/etc/sudoers.d/` using visudo** | `sudo visudo -f /etc/sudoers.d/ammar` | ✅✅ Safest     | Separate file — easier to revoke, follows best security practices |
| **Adding user to the wheel (or sudo) group**                     | `sudo usermod -aG wheel ammar`        | ✅ Medium Safe | Depends on system configuration — grants broad sudo privileges    |
