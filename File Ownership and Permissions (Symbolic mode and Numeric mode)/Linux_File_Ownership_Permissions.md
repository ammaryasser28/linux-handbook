🗂 File Ownership and Permissions in Linux

Linux is a multi-user system, so managing who can access or modify files is crucial.
Every file has owner, group, and permissions.

🏷️ 1. Understanding Ownership
| Element    | Description                        |
| ---------- | ---------------------------------- |
| **Owner**  | The user who owns the file         |
| **Group**  | The group associated with the file |
| **Others** | All other users on the system      |

Check ownership with:
ls -l filename

Example output:
-rw-r--r-- 1 amr users 1024 Oct 12 13:00 file.txt

amr → owner
users → group
rw-r--r-- → permissions

🔐 2. Understanding Permissions

Permissions define who can read, write, or execute a file:
| Symbol | Permission |
| ------ | ---------- |
| `r`    | Read       |
| `w`    | Write      |
| `x`    | Execute    |

Three categories:
| Category | Symbol | Meaning                |
| -------- | ------ | ---------------------- |
| Owner    | `u`    | User who owns the file |
| Group    | `g`    | Group members          |
| Others   | `o`    | Everyone else          |


✏️ 3. Symbolic Mode (u/g/o/a + +, -, =)

Change permissions using letters:
| Command                    | Description                                  |
| -------------------------- | -------------------------------------------- |
| `chmod u+x file`           | Add execute permission for owner             |
| `chmod g-w file`           | Remove write permission for group            |
| `chmod o=r file`           | Set read-only for others                     |
| `chmod a+x file`           | Add execute permission for all (a = all)     |
| `chmod u=rwx,g=rx,o= file` | Owner: rwx, Group: rx, Others: no permission |
Notes:
+ → add permission
- → remove permission
= → set exact permission (removes any existing permissions first)

🔢 4. Numeric (Octal) Mode

Permissions can also be set using numbers:
| Number | Permission                   |
| ------ | ---------------------------- |
| 0      | --- (no permission)          |
| 1      | --x (execute)                |
| 2      | -w- (write)                  |
| 3      | -wx (write + execute)        |
| 4      | r-- (read)                   |
| 5      | r-x (read + execute)         |
| 6      | rw- (read + write)           |
| 7      | rwx (read + write + execute) |
Format: chmod XYZ filename
X → owner permissions
Y → group permissions
Z → others permissions
Example:
chmod 755 script.sh
7 → owner: rwx
5 → group: r-x
5 → others: r-x

🧭 5. Changing Ownership
| Command                 | Description            |
| ----------------------- | ---------------------- |
| `chown user file`       | Change owner of file   |
| `chown user:group file` | Change owner and group |
| `chgrp group file`      | Change group of file   |
Example:
sudo chown amr:users file.txt
sudo chgrp admin file.txt

💡 Tips

Use ls -l to check current permissions and ownership.
Prefer symbolic mode for quick edits, numeric mode for exact settings.
Always ensure proper permissions for security.
