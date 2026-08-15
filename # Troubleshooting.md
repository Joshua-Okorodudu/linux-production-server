# Troubleshooting

## Issue 1

### Problem

```
etc/group: No such file or directory
```

### Cause

The absolute path was omitted.

### Solution

```bash
cat /etc/group
```

---

## Issue 2

### Problem

```
sudo: chown:IT: command not found
```

### Cause

A space was missing after the `chown` command.

### Solution

```bash
sudo chown :IT /company/IT
```

---

## Issue 3

### Problem

```
mkdir: cannot create directory '/company/IT'
```

### Cause

The parent directory `/company` had not been created.

### Solution

```bash
sudo mkdir /company
```

---

## Issue 4

### Problem

```
Permission denied
```

### Cause

The user did not belong to the required Linux group.

### Solution

Verified group membership using:

```bash
id username
```

Adjusted permissions using:

```bash
sudo usermod -aG group username
sudo chmod 770 directory
```

---

## Issue 5

### Problem

User was required to change password at next login.

### Cause

The password expiration policy was configured using:

```bash
sudo chage -d 0 username
```

### Solution

The user logged in and changed the password as required.
