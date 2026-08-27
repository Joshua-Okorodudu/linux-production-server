# Project 2 — Troubleshooting Notes

## Troubleshooting Scenario 1 — Checking SSH

### Problem

An administrator needs to determine whether the SSH service is running and identify the process responsible for it.

### Step 1 — Check the Service

```bash
systemctl status ssh
```

The service was confirmed to be:

```text
Active: active (running)
```

The status information also showed that the SSH server was listening on port 22.

### Step 2 — Find the Process

```bash
pgrep -a sshd
```

The SSH daemon was identified with:

```text
PID: 1315
```

### Step 3 — Identify the Parent Process

```bash
ps -o pid,ppid,args -p 1315
```

The result showed:

```text
PID    PPID
1315   1
```

This established that the SSH process had parent PID 1.

### Step 4 — Identify PID 1

```bash
ps -p 1 -o pid,args
```

The system reported:

```text
1 /usr/lib/systemd/systemd --system --deserialize=66
```

Therefore, PID 1 was confirmed to be systemd.

### Result

The process relationship was established as:

```text
systemd
PID 1
   |
   +--- sshd
        PID 1315
```

---
## Troubleshooting Scenario 2 — Inspecting an SSH Process

The `/proc` filesystem was used to investigate the SSH process directly.

```bash
cat /proc/1315/status
```

Important information observed included:

```text
Pid: 1315
VmSize: 10744 kB
VmRSS: 7780 kB
Threads: 1
```

This demonstrated that Linux exposes detailed information about running processes through `/proc`.

---

## Troubleshooting Scenario 3 — Understanding Process Hierarchy

The process tree was examined using:

```bash
pstree -p 1
```

The output showed systemd at the top of the userspace process hierarchy and included the SSH daemon.

The relevant relationship was:

```text
systemd(1)
   |
   +--- sshd(1315)
```

This helped demonstrate the relationship between the system manager and running processes.

---

## Troubleshooting Scenario 4 — Monitoring Processes

The `top` command was used to monitor processes in real time.

```bash
top
```

The tool displayed information including:

- PID
- User
- CPU usage
- Memory usage
- Process state
- Virtual memory
- Resident memory
- Command

This provides a useful first step when investigating high CPU or memory usage.

---

## Troubleshooting Scenario 5 — Managing a Background Process

A harmless test process was created:

```bash
sleep 300 &
```

The process was located with:

```bash
pgrep -a sleep
```

The process received PID:

```text
31148
```

The process was then terminated using:

```bash
kill 31148
```

The terminal reported that the process was terminated.

The result was verified using:

```bash
pgrep -a sleep
```

No running `sleep` process remained.

### Lesson

Always verify the result of an administrative action.

---

## Troubleshooting Scenario 6 — Incorrect PID Usage

During the process-management exercise, the following command was initially entered:

```bash
kill PID
```

The shell returned an error because `PID` was treated as literal text rather than as a placeholder.

The correct command used the actual process ID:

```bash
kill 31148
```

The process was successfully terminated.

### Lesson

When documentation uses a value such as `PID`, it normally represents a placeholder for the actual process ID.

For example:

```text
kill PID
```

means:

```text
kill <actual-process-id>
```

---

## Service vs Process Troubleshooting

When troubleshooting Linux, it is important to distinguish between a service and its underlying process.

For example:

```text
Service
ssh.service
    |
    v
Process
sshd
    |
    v
PID
1315
```

A service-level investigation can begin with:

```bash
systemctl status ssh
```

Process-level investigation can then continue with:

```bash
pgrep -a sshd
```

and:

```bash
ps -o pid,ppid,args -p 1315
```

Resource usage can then be investigated with:

```bash
top
```

---

## General Troubleshooting Method

The process used during this project can be summarized as:

```text
1. Identify the problem
          ↓
2. Check the service
          ↓
3. Identify the process
          ↓
4. Find the PID
          ↓
5. Check the parent process
          ↓
6. Inspect process information
          ↓
7. Monitor resource usage
          ↓
8. Take corrective action
          ↓
9. Verify the result
```

This approach provides a structured method for investigating Linux services and processes.

---

## Key Troubleshooting Lessons

1. Check the service before assuming the process is the problem.
2. Use the PID to investigate a specific process.
3. Use the PPID to understand the process's parent.
4. Use `/proc` when detailed process information is required.
5. Use `top` for live resource monitoring.
6. Use SIGTERM before considering SIGKILL.
7. Verify that corrective actions produced the expected result.
8. Be careful when replacing command placeholders with actual values.

---

## Project Conclusion

The troubleshooting exercises demonstrated a practical approach to Linux service and process management.

The project established the ability to investigate services, identify associated processes, trace process relationships, monitor resource usage, control processes and verify results.

These skills form part of the foundation for Linux system administration, infrastructure support, NOC operations and technical support roles.
