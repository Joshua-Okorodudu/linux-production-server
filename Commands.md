# Commands Used

## Server Information

| Command          | Purpose                    |
| ---------------- | -------------------------- |
| `hostnamectl`    | Display server information |
| `lsb_release -a` | Display Ubuntu version     |
| `ip a`           | View network interfaces    |
| `df -h`          | Display disk usage         |
| `free -h`        | Display memory usage       |

---

## User Management

| Command   | Purpose                  |
| --------- | ------------------------ |
| `adduser` | Create a user            |
| `id`      | Display user information |
| `passwd`  | Manage user passwords    |
| `chage`   | Configure password aging |

---

## Group Management

| Command           | Purpose                       |
| ----------------- | ----------------------------- |
| `groupadd`        | Create a new group            |
| `usermod -aG`     | Add user to a secondary group |
| `cat /etc/group`  | Display all groups            |
| `grep /etc/group` | Search for specific groups    |

---

## Directory Management

| Command  | Purpose                           |
| -------- | --------------------------------- |
| `mkdir`  | Create directories                |
| `ls`     | List files and folders            |
| `ls -l`  | Display detailed file information |
| `ls -ld` | Display directory information     |

---

## Ownership

| Command | Purpose                |
| ------- | ---------------------- |
| `chown` | Change ownership       |
| `chgrp` | Change group ownership |

---

## Permissions

| Command | Purpose                               |
| ------- | ------------------------------------- |
| `chmod` | Modify file and directory permissions |

---

## User Switching

| Command         | Purpose                |
| --------------- | ---------------------- |
| `su - username` | Switch to another user |
| `whoami`        | Display current user   |

---

## System Files

| Command                     | Purpose                               |
| --------------------------- | ------------------------------------- |
| `cat /etc/passwd`           | Display user accounts                 |
| `cat /etc/group`            | Display groups                        |
| `grep username /etc/shadow` | View password information (root only) |
