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


# Ways to Grant Root / Administrative Privileges to a User

Below table summarizes common methods to give a regular user administrative (root) capabilities on a Linux system. Each row shows the method, example command(s), pros, cons and a short recommendation.

| Method (Arabic)                                   |                                      Method (English) | Example command(s)                                                      | Pros                                                          | Cons                                                         | Recommendation                                      |
| ------------------------------------------------- | ----------------------------------------------------: | ----------------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| إضافة في `sudoers` عبر ملف منفصل                  |                         Add user via `/etc/sudoers.d` | ```bash                                                                 |                                                               |                                                              |                                                     |
| echo "ammar ALL=(ALL) ALL"                        |                         sudo tee /etc/sudoers.d/ammar |                                                                         |                                                               |                                                              |                                                     |
| sudo chmod 440 /etc/sudoers.d/ammar               |                                                       |                                                                         |                                                               |                                                              |                                                     |
| ```                                               |                دقيق، قابل للتدقيق (logs)، سهل التراجع | يحتاج حذر عند تحرير sudoers (استخدم `visudo` أو ملفات `sudoers.d`)      | **مستحسن** — أفضل توازن بين أمان ومرونة                       |                                                              |                                                     |
| إضافة للمجموعة التي تملك sudo (`sudo` أو `wheel`) |                      Add user to `sudo`/`wheel` group | Ubuntu/Debian: `sudo usermod -aG sudo ammar`                            |                                                               |                                                              |                                                     |
| RHEL/Fedora: `sudo usermod -aG wheel ammar`       |            سهل للإدارة (مجموعات)، مناسب للـ ops teams | يعتمد على إعدادات `/etc/sudoers`؛ يمنح صلاحيات واسعة إذا المجموعة مفعلة | **مستحسن** إذا تم إدارة المجموعات بشكل صحيح                   |                                                              |                                                     |
| منح صلاحيات محددة في ملف sudoers                  |              Grant limited sudo for specific commands | `echo "ammar ALL=(ALL) /usr/bin/apt, /usr/bin/systemctl"                | sudo tee /etc/sudoers.d/ammar-limited                         |                                                              |                                                     |
| sudo chmod 440 /etc/sudoers.d/ammar-limited`      | يعطي أقل قدر ممكن من الامتيازات — مبدأ الأقل امتيازًا | يحتاج معرفة المسارات الدقيقة للأوامر؛ إدارة أكثر تعقيدًا                | **مستحسن** للمهام الآلية أو المحددة                           |                                                              |                                                     |
| تمكين حساب root (تعريف كلمة مرور)                 |                      Enable root account (set passwd) | `sudo passwd root`                                                      | يتيح تسجيل دخول مباشر كـ root                                 | مخاطرة أمنية عالية؛ يصعب تتبع الأفعال والـ SSH login ممكن    | **غير مفضّل** إلا لحالة خاصة ومراقبة مشددة          |
| تغيير UID إلى 0 (تحويل المستخدم إلى root فعليًا)  |              Change user's UID to 0 (make user UID=0) | `sudo usermod -u 0 -o ammar` (***خطير***)                               | يجعل المستخدم مكرراً لـ root جسمانياً                         | خطير جدًا: تعارضات ملكية، صعوبة في التتبع، مشاكل أمنية كبيرة | **لا يُنصح** مطلقًا إلا لخبراء وبحالة نادرة جداً    |
| جعل برنامج يعمل بصلاحيات root عبر setuid          |                                         setuid binary | `sudo chown root:root /path/to/prog && sudo chmod 4755 /path/to/prog`   | يمكن منح وظيفة محددة صلاحية root دون إعطاء المستخدم root كامل | إذا لم يُكتب البرنامج بأمان يصبح ثغرة خطيرة                  | **لا يُنصح** إلا لمطورين ذوي خبرة ومع فحص أمني صارم |

---

## Quick examples & notes

### Example: give full sudo to `ammar` safely

```bash
echo "ammar ALL=(ALL) ALL" | sudo tee /etc/sudoers.d/ammar
sudo chmod 440 /etc/sudoers.d/ammar
```

### Example: give `ammar` limited rights (only apt & systemctl)

```bash
echo "ammar ALL=(ALL) /usr/bin/apt, /usr/bin/systemctl" | sudo tee /etc/sudoers.d/ammar-limited
sudo chmod 440 /etc/sudoers.d/ammar-limited
```

### Add `ammar` to `sudo` or `wheel` group

```bash
# Debian/Ubuntu
sudo usermod -aG sudo ammar

# RHEL/CentOS/Fedora
sudo usermod -aG wheel ammar
```

### Enable root account (use with caution)

```bash
sudo passwd root
```

### Dangerous — change UID to 0 (do not use unless you know exactly why)

```bash
sudo usermod -u 0 -o ammar
```

---

## Short recommendations

* **Best practice:** prefer `/etc/sudoers.d/` entries and limited sudo rules (least privilege).
* **Use group-based approach** (`sudo`/`wheel`) for team management.
* **Avoid changing UID to 0** or granting setuid binaries unless unavoidable and thoroughly audited.
* **Avoid regular direct root logins**; prefer `sudo` for traceability.



(غير `main` لاسم الفرع لو بتستخدم فرع مختلف)

