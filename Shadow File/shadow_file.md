🛡️ Understanding /etc/shadow in Linux
📌 Overview

The /etc/shadow file in Linux stores hashed passwords and password aging information for system users.
It is highly protected and can only be read by the root user, making system authentication more secure.

🔐 Why /etc/shadow?

Historically, encrypted passwords were stored in /etc/passwd, but /etc/passwd is world-readable, creating a security risk.
To fix that, Linux systems started storing password hashes inside the shadow file instead.
| File          | Contains                               | Permissions          |
| ------------- | -------------------------------------- | -------------------- |
| `/etc/passwd` | User account info (no password hashes) | Readable by everyone |
| `/etc/shadow` | Password hashes + password policies    | Root-only access     |

🧩 File Structure

Each line in /etc/shadow represents one user account.
The fields are separated using : and structured as follows:
```
username:password:last_change:min:max:warn:inactive:expire:reserved
```
| Field           | Description                                          |
| --------------- | ---------------------------------------------------- |
| **username**    | User account name                                    |
| **password**    | Hashed password or special symbol                    |
| **last_change** | Days since Jan 1 1970 when password was last updated |
| **min**         | Minimum days before password can be changed          |
| **max**         | Maximum days before password must be changed         |
| **warn**        | Days before expiration to warn the user              |
| **inactive**    | Days after expiration before account is disabled     |
| **expire**      | Date (in days since epoch) when account expires      |
| **reserved**    | Reserved for future use                              |

🔑 Password Field Special Values
| Value           | Meaning                                                |
| --------------- | ------------------------------------------------------ |
| `$id$salt$hash` | Normal hashed password format                          |
| `!`             | Account is locked (cannot authenticate using password) |
| `*`             | System account (no password login allowed)             |
| empty           | **Very dangerous** → account has *no password*         |

✅ Common Hash Types
| Prefix | Algorithm                         |
| ------ | --------------------------------- |
| `$1$`  | MD5                               |
| `$5$`  | SHA-256                           |
| `$6$`  | SHA-512 (default & recommended ✅) |

📌 Example Entry
```
amr:$6$8Fhuw...$d9Lp5..:19500:0:99999:7:::
```
Breakdown:
$6$ → SHA-512 encryption
19500 → Last changed password date
99999 → Password practically never expires
7 → Warn 7 days before expiration

✅ Security Notes
Only root should read /etc/shadow
File permissions must remain strict:
```
-r-------- 1 root root /etc/shadow
```
Hashes should always use strong algorithms (SHA-512)
Removing password or setting it to ! should be done with caution


