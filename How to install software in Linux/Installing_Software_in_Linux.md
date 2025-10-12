🛠 How to Install Software in Linux – Package Managers

Linux doesn’t have .exe files like Windows.
Instead, it uses package managers to install, update, and remove software.

There are multiple ways depending on the Linux distribution and package type.

📦 1. Using APT (Debian/Ubuntu based)

APT is the standard package manager for Debian, Ubuntu, Linux Min
| Command                         | Description                             |
| ------------------------------- | --------------------------------------- |
| `sudo apt update`               | Refresh package lists from repositories |
| `sudo apt upgrade`              | Upgrade all installed packages          |
| `sudo apt install package_name` | Install a new package                   |
| `sudo apt remove package_name`  | Remove a package                        |
| `sudo apt search package_name`  | Search for packages                     |


🐧 2. Using YUM / DNF (RedHat, CentOS, Fedora)

YUM / DNF is used in RedHat, CentOS, Fedora.
| Command                         | Description                         |
| ------------------------------- | ----------------------------------- |
| `sudo yum install package_name` | Install a package (RHEL/CentOS 7)   |
| `sudo dnf install package_name` | Install a package (Fedora, RHEL 8+) |
| `sudo yum remove package_name`  | Remove a package                    |
| `sudo yum update`               | Update installed packages           |


⚡ 3. Using Snap (Universal Packages)

Snap packages work across most Linux distributions.
| Command                          | Description              |
| -------------------------------- | ------------------------ |
| `sudo snap install package_name` | Install a snap package   |
| `sudo snap remove package_name`  | Remove a snap package    |
| `snap list`                      | List installed snaps     |
| `snap find package_name`         | Search for snap packages |


💡 Tips

Always update your package lists before installing anything.
Use sudo to run commands with administrative privileges.
Check official docs for software compatibility.
Prefer package managers (apt, dnf, snap) over source installation for simplicity and updates.



