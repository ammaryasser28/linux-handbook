## 🔐 Configure Password Aging in Linux

Password aging helps you **control how long users can keep their passwords** before they must change them — improving system security.

---

### 🧰 1. Using the `chage` Command

The `chage` (change age) command manages password expiration settings for user accounts.

#### 🔍 View Current Password Aging Info:
```
sudo chage -l username
```
Example Output:
```
Last password change                                    : Oct 20, 2025
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 90
Number of days of warning before password expires       : 7
```

⚙️ 2. Set Password Aging Policies
| Option | Description                                              | Example                             |
| ------ | -------------------------------------------------------- | ----------------------------------- |
| `-M`   | Maximum number of days password is valid                 | `sudo chage -M 90 username`         |
| `-m`   | Minimum number of days before changing password          | `sudo chage -m 7 username`          |
| `-W`   | Warn user this many days before expiration               | `sudo chage -W 7 username`          |
| `-I`   | Number of days after expiration before account is locked | `sudo chage -I 30 username`         |
| `-E`   | Set account expiration date (YYYY-MM-DD)                 | `sudo chage -E 2025-12-31 username` |

🧩 Example: Enforce a 90-Day Password Policy
```
sudo chage -m 7 -M 90 -W 7 -I 30 username
```
Meaning:

User must wait 7 days before changing password again.

Password expires after 90 days.

System warns 7 days before expiration.

Account locks 30 days after expiration.

🛡️ 3. Verify the Settings

After configuration, always check:
```
sudo chage -l username
```
and ensure the dates match your security policy.

