📂 File and Directory Commands

| Command     | Description                                                                                 | Example                                      |
| ----------- | ------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **`pwd`**   | Print the current working directory.                                                        | `pwd` → `/home/amr`                          |
| **`ls`**    | List files and directories.                                                                 | `ls -l` → detailed list                      |
| **`ls -R`** | List all files **recursively** — يظهر محتوى المجلدات وكل ما بداخلها.                        | `ls -R work`                                 |
| **`cd`**    | Change the current directory.                                                               | `cd /etc`                                    |
| **`mkdir`** | Create a new directory.                                                                     | `mkdir test`                                 |
| **`rmdir`** | Remove an empty directory.                                                                  | `rmdir test`                                 |
| **`rm`**    | Remove files or directories.                                                                | `rm file.txt` or `rm -r folder`              |
| **`cp`**    | Copy files or directories.                                                                  | `cp file.txt /home/amr/`                     |
| **`mv`**    | Move or rename files.                                                                       | `mv old.txt new.txt`                         |
| **`touch`** | Create an empty file or update its timestamp.                                               | `touch notes.txt`                            |
| **`cat`**   | Display the contents of a file.                                                             | `cat file.txt`                               |
| **`more`**  | View file contents **page by page (forward only)** — press `Space` to go to the next page.  | `more /etc/passwd`                           |
| **`less`**  | View large files with **scrolling (forward & backward)** — use arrow keys or `/` to search. | `less /etc/passwd`                           |
| **`head`**  | Show the **first 10 lines** of a file (default).                                            | `head file.txt` or `head -n 20 file.txt`     |
| **`tail`**  | Show the **last 10 lines** of a file (default).                                             | `tail file.txt` or `tail -f /var/log/syslog` |
