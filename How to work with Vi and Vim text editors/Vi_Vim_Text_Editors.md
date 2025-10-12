✍️ How to Work with Vi and Vim Text Editors

Vi and Vim are powerful text editors used in Linux for editing configuration files, scripts, and code.
Vim is an enhanced version of Vi with extra features.

🏷️ 1. Opening and Creating Files
| Command        | Description                  |
| -------------- | ---------------------------- |
| `vi filename`  | Open or create a file in Vi  |
| `vim filename` | Open or create a file in Vim |

🔄 2. Modes in Vi / Vim

Vi/Vim has two main modes:
Normal Mode (default)
Navigate, delete, copy, paste, or switch to other modes.
Insert Mode
For typing text into the file.

Switch Modes:
| Action                              | Key                                                                             |
| ----------------------------------- | ------------------------------------------------------------------------------- |
| Enter Insert Mode                   | `i` (before cursor), `I` (start of line), `a` (after cursor), `A` (end of line) |
| Return to Normal Mode               | `Esc`                                                                           |
| Command Mode (for saving, quitting) | `:` (from Normal Mode)                                                          |

💾 3. Saving and Exiting
| Command       | Description               |
| ------------- | ------------------------- |
| `:w`          | Save file (write changes) |
| `:q`          | Quit editor               |
| `:wq` or `ZZ` | Save and quit             |
| `:q!`         | Quit without saving       |
