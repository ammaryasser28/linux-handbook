📂 File and Directory Commands

| Command     | Description                                                                   | Example                                     |
| ----------- | ----------------------------------------------------------------------------- | ------------------------------------------- |
| **`pwd`**   | Print the current working directory.                                          | `pwd` → `/home/amr`                         |
| **`ls`**    | List files and directories.                                                   | `ls -l` → detailed list                     |
| **`ls -R`** | List all files **recursively** — يظهر محتوى المجلدات وكل ما بداخلها.          | `ls -R work`                                |
| **`cd`**    | Change the current directory.                                                 | `cd /etc`                                   |
| **`mkdir`** | Create a new directory.                                                       | `mkdir test`                                |
| **`rmdir`** | Remove an empty directory.                                                    | `rmdir test`                                |
| **`rm`**    | Remove files or directories.                                                  | `rm file.txt` or `rm -r folder`             |
| **`rm -i`** | Remove files **with confirmation prompt** (safer).                            | `rm -i file.txt`                            |
| **`rm -f`** | Remove files **forcefully without asking** — ⚠️ very dangerous.               | `rm -f file.txt`                            |
| **`cp`**    | Copy files or directories.                                                    | `cp file.txt /home/amr/`                    |
| **`mv`**    | Move or rename files.                                                         | `mv old.txt new.txt`                        |
| **`touch`** | Create an empty file or update timestamp (or multiple using brace expansion). | `touch notes.txt` / `touch file{1..20}`     |
| **`cat`**   | Display the contents of a file.                                               | `cat file.txt`                              |
| **`more`**  | View file contents page by page (forward only).                               | `more /etc/passwd`                          |
| **`less`**  | View large files with scrolling and search.                                   | `less /etc/passwd`                          |
| **`head`**  | Show the first 10 lines of a file.                                            | `head file.txt` / `head -n 20 file.txt`     |
| **`tail`**  | Show the last 10 lines of a file.                                             | `tail file.txt` / `tail -f /var/log/syslog` |
