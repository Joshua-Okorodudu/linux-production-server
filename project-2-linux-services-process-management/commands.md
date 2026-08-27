# Project 2 — Commands Reference

This document contains the Linux commands practiced during the Linux Services & Process Management project.

## Service Management

### Start SSH

```bash
sudo systemctl start ssh
```

Starts the SSH service.

### Stop SSH

```bash
sudo systemctl stop ssh
```

Stops the SSH service.

### Restart SSH

```bash
sudo systemctl restart ssh
```

Restarts the SSH service.

### Enable SSH
```bash
sudo systemctl enable ssh
```

Configures SSH to start automatically during system boot.

### Check SSH Status

```bash
systemctl status ssh
```

Displays the current status of the SSH service.

### Check Whether SSH Is Enabled

```bash
systemctl is-enabled ssh
```

Shows whether SSH is configured to start automatically during boot.

### List Services

```bash
systemctl list-units --type=service
```

Lists currently loaded service units managed by systemd.

---

## Process Management

### Display Current Shell Processes

```bash
ps
```
Displays processes associated with the current terminal session.

### Display Detailed Process Information

```bash
ps aux
```

Displays a broader list of processes running on the system.

### Find the SSH Process

```bash
pgrep -a sshd
```

Searches for the SSH daemon and displays its PID and command.

### Inspect a Process

```bash
cat /proc/1315/status
```

Displays detailed kernel-maintained information about the SSH process.

### Display PID, PPID and Command

```bash
ps -o pid,ppid,args -p 1315
```

Displays the process ID, parent process ID and command for PID 1315.

### Inspect PID 1

```bash
ps -p 1 -o pid,args
```

Displays information about PID 1.

In this lab, PID 1 was confirmed to be systemd.

### Display the Process Tree

```bash
pstree -p 1
```
Displays the process hierarchy beginning with PID 1, including process IDs.

---

## Process Monitoring

### Live Process Monitoring

```bash
top
```

Displays a continuously updated view of running processes and resource usage.

Press:

```text
q
```

to exit `top`.

---

## Background Processes

### Start a Background Process

```bash
sleep 300 &
```

Starts a harmless `sleep` process in the background.

### Find the Background Process

```bash
pgrep -a sleep
```

Finds the running `sleep` process and displays its PID.

### Display Shell Jobs

```bash
jobs
```

Displays background jobs associated with the current shell.

### Bring a Job to the Foreground

```bash
fg
```

Brings a background job into the foreground.

---

## Process Termination

### Gracefully Terminate a Process

```bash
kill 31148
```

Sends SIGTERM to the process with PID 31148.

### Forcefully Terminate a Process

```bash
kill -9 31148
```

Sends SIGKILL to the specified process.

SIGKILL should normally only be used when a process does not respond to a normal termination request.

### Verify Process Termination

```bash
pgrep -a sleep
```

Used after terminating the test process to verify that it was no longer running.

---

## Practical Troubleshooting Workflow

A basic process and service troubleshooting workflow used during the project was:

```text
Check service status
        ↓
Identify the process
        ↓
Find the PID
        ↓
Identify the parent process
        ↓
Inspect process information
        ↓
Monitor resource usage
        ↓
Take corrective action
        ↓
Verify the result
```

Example:

```bash
systemctl status ssh
pgrep -a sshd
ps -o pid,ppid,args -p 1315
top
```

This workflow can be adapted when investigating Linux services and processes in a production environment.

---

## Important Commands Summary

| Area | Command | Purpose |
|---|---|---|
| Service | `systemctl start ssh` | Start SSH |
| Service | `systemctl stop ssh` | Stop SSH |
| Service | `systemctl restart ssh` | Restart SSH |
| Service | `systemctl enable ssh` | Enable SSH at boot |
| Service | `systemctl status ssh` | Check SSH status |
| Service | `systemctl is-enabled ssh` | Check boot configuration |
| Service | `systemctl list-units --type=service` | List services |
| Process | `ps` | View current processes |
| Process | `ps aux` | View detailed process list |
| Process | `pgrep -a sshd` | Find SSH process |
| Process | `cat /proc/1315/status` | Inspect process details |
| Process | `pstree -p 1` | View process hierarchy |
| Monitoring | `top` | Monitor processes live |
| Jobs | `jobs` | View background jobs |
| Jobs | `fg` | Bring a job to foreground |
| Control | `kill PID` | Send SIGTERM |
| Control | `kill -9 PID` | Send SIGKILL |
