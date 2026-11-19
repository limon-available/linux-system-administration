# Day 03 – Linux Administration: User, Privileges & System Configuration

This repository documents my hands-on Linux System Administration practice using an **AWS EC2 Ubuntu Server**.

Day 03 focused on Linux user password management, hostname and timezone configuration, system reboot, login history, and sudo audit logs.

## Environment

| Component        | Details                 |
| ---------------- | ----------------------- |
| Cloud Provider   | AWS EC2                 |
| Operating System | Ubuntu Server 24.04 LTS |
| Instance Type    | t3.micro                |
| Architecture     | x86-64                  |
| Linux User       | ubuntu                  |
| Hostname         | limon-linux-lab         |
| Timezone         | Asia/Dhaka (UTC+06:00)  |
| Access Method    | SSH Key Authentication  |

## Practical Tasks

### 1. Linux User Password Management

Initially, I attempted to change the current user's password using:

```bash
passwd
```

It returned:

```text
passwd: Authentication token manipulation error
passwd: password unchanged
```

Since the EC2 user account did not have a usable current password for this operation, I used sudo privileges:

```bash
sudo passwd ubuntu
```

Result:

```text
passwd: password updated successfully
```

**Verify password status:**

```bash
sudo passwd -S ubuntu
```

Example output:

```text
ubuntu P 2026-11-18 0 99999 7 -1
```

The `P` status indicates that a password is set.

**Key Learning:**

- Changing a Linux account password using `passwd`.
- Using `sudo passwd username` to set another user's password with administrative privileges.
- Understanding the difference between Linux account passwords and SSH private keys.

### 2. Hostname Configuration

Changed the server hostname to `limon-linux-lab`.

```bash
sudo hostnamectl set-hostname limon-linux-lab
```

**Verify hostname:**

```bash
hostname
hostnamectl
```

Result:

```text
Static hostname: limon-linux-lab
```

**Key Learning:**

- Managing Linux hostnames.
- Using `hostnamectl` for system hostname configuration.

### 3. Timezone Configuration

Checked available timezones:

```bash
timedatectl list-timezones | grep Dhaka
```

Output:

```text
Asia/Dhaka
```

Changed the system timezone:

```bash
sudo timedatectl set-timezone Asia/Dhaka
```

**Verify timezone:**

```bash
timedatectl
date
```

Relevant output:

```text
Time zone: Asia/Dhaka (+06, +0600)
System clock synchronized: yes
NTP service: active
```

**Key Learning:**

- Configuring system timezone.
- Understanding UTC and local time.
- Checking NTP synchronization.

### 4. System Reboot and Uptime Monitoring

Rebooted the EC2 Ubuntu server:

```bash
sudo reboot
```

After reconnecting through SSH, checked server uptime:

```bash
uptime
uptime -s
```

Example output:

```text
20:01:07 up 0 min, 1 user, load average: 0.04, 0.01, 0.00
2026-11-18 20:00:25
```

**Key Learning:**

- Rebooting a Linux server safely.
- Reconnecting to an EC2 instance after reboot.
- Monitoring uptime and system load.

### 5. Login History Monitoring

Checked successful login history:

```bash
last
```

Checked login history for a specific user:

```bash
last ubuntu
```

Useful information from the output:

- Username
- Login terminal
- Source IP address
- Login time
- Logout time
- System reboot history

**Note:** The `last limon` command returned no matching entries because the actual SSH login account was `ubuntu`.

### 6. Failed Login Attempts

Checked failed login attempts:

```bash
sudo lastb
```

Output:

```text
btmp begins Wed Nov 18 16:06:32 2026
```

No failed login records were displayed in the available `btmp` log.

**Key Learning:**

- Monitoring failed login attempts.
- Understanding Linux authentication history.
- Using `lastb` for basic security monitoring.

### 7. Sudo Audit Log Monitoring

Inspected sudo-related system journal entries:

```bash
sudo journalctl -e _COMM=sudo
```

Example log:

```text
ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/lastb
```

Understanding the log fields:

| Field       | Description            |
| ----------- | ---------------------- |
| `ubuntu`    | User who executed sudo |
| `TTY`       | Terminal session       |
| `PWD`       | Working directory      |
| `USER=root` | Target privileged user |
| `COMMAND`   | Executed command       |

Also observed PAM session events:

```text
pam_unix(sudo:session): session opened for user root
pam_unix(sudo:session): session closed for user root
```

**Key Learning:**

- Inspecting sudo activity.
- Understanding privileged command execution.
- Monitoring administrative actions through system logs.

## Important Commands Practiced

| Command                         | Purpose                                    |
| ------------------------------- | ------------------------------------------ |
| `passwd`                        | Change current user's password             |
| `sudo passwd username`          | Set a user's password with root privileges |
| `sudo passwd -S username`       | Check password status                      |
| `hostnamectl`                   | Manage system hostname                     |
| `timedatectl`                   | Manage system date and timezone            |
| `date`                          | Display current date and time              |
| `sudo reboot`                   | Reboot the system                          |
| `uptime`                        | Display system uptime and load average     |
| `uptime -s`                     | Show system boot time                      |
| `last`                          | Show successful login history              |
| `lastb`                         | Show failed login attempts                 |
| `journalctl`                    | Inspect system journal logs                |
| `sudo journalctl -e _COMM=sudo` | Inspect sudo-related logs                  |

## Skills Practiced

- Linux User and Password Management
- Sudo Privilege Management
- Hostname Configuration
- Timezone Configuration
- System Reboot and Uptime Monitoring
- Login History Auditing
- Failed Authentication Monitoring
- Sudo Log Inspection
- AWS EC2 Ubuntu Server Administration
- SSH-Based Remote Server Management

## Key Takeaways

Through this practical session, I gained hands-on experience in basic Linux server administration and learned how to:

1. Manage Linux user passwords.
2. Configure server hostname and timezone.
3. Reboot and reconnect to a cloud-based Linux server.
4. Monitor system uptime and login history.
5. Inspect failed authentication attempts.
6. Review sudo activity for basic administrative auditing.

---

**Learning Path:** Linux Upskill Challenge – Day 03

**Environment:** AWS EC2 | Ubuntu Server 24.04 LTS

**Status:** Completed
