# Linux & Web Servers Guide for Beginners

## Table of Contents

| #  | **Action**         | **Windows CMD Command**   | **Linux Bash Equivalent**   |
| -- | ------------------------ | ------------------------------- | --------------------------------- |
| 1  | Change directory         | `cd <directory>`              | `cd <directory>`                |
| 2  | List directory contents  | `dir`                         | `ls`                            |
| 3  | Create a directory       | `mkdir <directory>`           | `mkdir <directory>`             |
| 4  | Remove a directory       | `rmdir <directory>`           | `rmdir <directory>` or rm -r    |
| 5  | Delete a file            | `del <filename>`              | `rm <filename>`                 |
| 6  | Copy a file              | `copy <source> <destination>` | `cp <source> <destination>`     |
| 7  | Move a file              | `move <source> <destination>` | `mv <source> <destination>`     |
| 8  | Rename a file            | `rename <oldname> <newname>`  | `mv <oldname> <newname>`        |
| 9  | Display a message        | `echo <message>`              | `echo <message>`                |
| 10 | Ping a host              | `ping <hostname>`             | `ping <hostname>`               |
| 11 | Clear screen             | `cls`                         | `clear`                         |
| 12 | Display IP configuration | `ipconfig`                    | `ifconfig` or `ip a`          |
| 13 | List running tasks       | `tasklist`                    | `ps aux` or `top`             |
| 14 | Kill a running process   | `taskkill /IM <process-name>` | `killall <process-name>`        |
| 15 | Disk check               | `chkdsk <drive>:`             | `fsck` (run on unmounted disks) |

1. [Linux Command Line – File Operations, Navigation, Permissions](#1-linux-command-line)
2. [Vim &amp; Emacs Editors](#2-vim--emacs-editors)
3. [Package Management](#3-package-management)
4. [Shell Scripting](#4-shell-scripting)
5. [Web Servers](#5-web-servers)

## 1. Linux Command Line

*The command line is a text-based way to control your computer. Think of it like typing instructions instead of clicking icons. **Bash** is the most common "language" for these instructions.*

### Navigation (Moving Around)

- **`pwd`** (Print Working Directory): Shows where you are

  ```bash
  pwd
  # Output: /home/user
  ```
- **`cd`** (Change Directory): Move to a different folder

  ```bash
  cd Documents  # Go into the "Documents" folder
  cd ..         # Go back one level
  cd ~          # Go to your home folder
  ```
- **`ls`** (List): Shows files/folders in your current location

  ```bash
  ls            # Basic list
  ls -l         # Detailed list (permissions, size, date)
  ls -a         # Show hidden files (starting with ".")
  ```

### File Operations

- **`touch`** (Create empty file):
  ```bash
  touch notes.txt  # Creates "notes.txt"
  ```
- **`cp`** (Copy):
  ```bash
  cp notes.txt backup/  # Copy "notes.txt" into the "backup" folder
  ```
- **`mv`** (Move/Rename):
  ```bash
  mv notes.txt old_notes.txt  # Renames the file
  mv notes.txt Documents/     # Moves file to "Documents"
  ```
- **`rm`** (Remove/Delete):
  ```bash
  rm old_notes.txt  # Deletes the file (BE CAREFUL - no undo!)
  ```
- **`mkdir`** (Make Directory):
  ```bash
  mkdir projects   # Creates a new folder named "projects"
  ```

### Permissions

Every file has 3 permission types: **Read (r)**, **Write (w)**, **Execute (x)**, for 3 user types: **Owner**, **Group**, **Others**.

- **`chmod`** (Change Permissions):
  ```bash
  chmod +x script.sh  # Makes "script.sh" executable (like a program)
  chmod 755 file.txt  # Owner: rwx, Group: r-x, Others: r-x
  ```
- **`chown`** (Change Owner):
  ```bash
  chown user:group file.txt  # Changes owner and group
  ```
- View permissions with `ls -l`:
  ```bash
  ls -l
  # Output: -rw-r--r-- 1 user group 123 Jan 1 12:00 file.txt
  # Permissions: - (file), rw- (owner), r-- (group), r-- (others)
  ```

## Understanding Permission Combinations

| Numeric | Symbolic  | Meaning                                            |
| :------ | --------- | -------------------------------------------------- |
| 400     | r-------- | Owner can read                                     |
| 600     | rw------- | Owner can read and write                           |
| 644     | rw-r--r-- | Owner can read/write, others can read              |
| 700     | rwx------ | Owner has full access                              |
| 755     | rwxr-xr-x | Owner has full access, others can read and execute |
| 777     | rwxrwxrwx | Everyone has full access                           |

> **Why It Matters**: Like learning to drive a car, the command line gives you full control over your computer.
> It's faster for repetitive tasks and essential for managing servers or automating work.

---

## 2. Vim & Emacs Editors

**Vim** and **Emacs** are powerful text editors for the command line. They're like supercharged versions of Notepad, but they require learning keyboard shortcuts instead of using a mouse.

### Vim Basics

- **Modes**:
  - **Normal Mode**: Navigation (press `Esc` to enter)
  - **Insert Mode**: Typing text (press `i` to enter)
- **Key Shortcuts**:
  - `i` → Insert text
  - `Esc` → Exit to Normal Mode
  - `:w` → Save
  - `:q` → Quit
  - `:wq` → Save and quit
  - `dd` → Delete a line
  - `/word` → Search for "word"
- **Configuration**:
  Edit `~/.vimrc` to customize settings (e.g., `set number` shows line numbers)

### Emacs Basics

- **Key Shortcuts**:
  - `Ctrl+x Ctrl+f` → Open file
  - `Ctrl+x Ctrl+s` → Save
  - `Ctrl+x Ctrl+c` → Quit
  - `Ctrl+s` → Search
- **Configuration**:
  Edit `~/.emacs` or `~/.emacs.d/init.el` to add settings (e.g., `(setq line-number-mode t)` shows line numbers)

### Example Workflow (Vim)

1. Open a file: `vim notes.txt`
2. Press `i` to type text
3. Press `Esc` to return to Normal Mode
4. Type `:wq` to save and quit

> **Why It Matters**: These editors are lightweight and work anywhere (even on servers). Mastering them makes editing code or configuration files lightning-fast.

---

## 3. Package Management

**Package managers** are like app stores for Linux. They handle installing, updating, and removing software automatically.

### apt (Debian/Ubuntu systems)

- Update software list:
  ```bash
  sudo apt update
  ```
- Install software:
  ```bash
  sudo apt install firefox  # Installs Firefox browser
  ```
- Remove software:
  ```bash
  sudo apt remove firefox
  ```
- Upgrade all installed software:
  ```bash
  sudo apt upgrade
  ```

### yum (Red Hat/CentOS systems)

- Install software:
  ```bash
  sudo yum install python3
  ```
- Remove software:
  ```bash
  sudo yum remove python3
  ```
- Update all software:
  ```bash
  sudo yum update
  ```

> **Why It Matters**: Package managers ensure software is installed correctly with all required dependencies (like puzzle pieces). They also handle security updates automatically.

---

## 4. Shell Scripting

**Shell scripting** is writing sequences of commands in a file to automate tasks. It's like creating a recipe for your computer to follow.

### Basic Script Structure

```bash
#!/bin/bash  # Tells Linux to use Bash
echo "Hello, World!"  # Prints text
```

Save as `hello.sh`, then run:

```bash
bash hello.sh
```

### Variables & Input

```bash
#!/bin/bash
echo "What's your name?"
read name  # Reads user input
echo "Hello, $name!"
```

### Conditions (If/Else)

```bash
#!/bin/bash
if [ "$name" == "Maheedhar" ]; then
  echo "Welcome, Maheedhar!"
else
  echo "You're not Maheedhar!"
fi
```

### Loops

```bash
#!/bin/bash
for i in 1 2 3 4 5; do
  echo "Count: $i"
done
```

> **Why It Matters**: Scripts save time! Instead of typing the same commands daily, automate backups, file organization, or system checks.

---

## 5. Web Servers

**Web servers** are software that delivers websites to browsers. **Apache** and **Nginx** are the most popular. **SSL** encrypts data (HTTPS), and **virtual hosts** let you host multiple websites on one server.

### Install Apache (Ubuntu)

```bash
sudo apt install apache2
```

Start the server:

```bash
sudo systemctl start apache2
```

Visit `http://localhost` in a browser to see the default page.

### Install Nginx (Ubuntu)

```bash
sudo apt install nginx
```

### SSL (HTTPS) with Let's Encrypt

```bash
sudo apt install certbot python3-certbot-apache
sudo certbot --apache -d yourdomain.com
```

This automatically installs a free SSL certificate.

### Virtual Hosts (Host Multiple Sites)

1. Create a config file:
   ```bash
   sudo nano /etc/apache2/sites-available/mysite.conf
   ```
2. Add configuration:
   ```apache
   <VirtualHost *:80>
       ServerName mysite.com
       DocumentRoot /var/www/mysite
   </VirtualHost>
   ```
3. Enable the site:
   ```bash
   sudo a2ensite mysite.conf
   sudo systemctl reload apache2
   ```

> **Why It Matters**: Web servers power the internet! Knowing how to configure them lets you host websites, secure data with SSL, and manage multiple sites efficiently.
