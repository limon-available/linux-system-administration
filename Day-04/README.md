# Day 04 – Installing Software & Exploring the Linux Filesystem

## Overview

On Day 04 of my Linux System Administration learning journey, I explored Ubuntu's package management system, installed software using APT, navigated important Linux directories, inspected system configuration files and logs, and played a terminal-based game.

**Environment:**

- OS: Ubuntu 24.04 LTS
- Platform: AWS EC2
- User: `ubuntu`
- Package Manager: APT
- Terminal File Manager: Midnight Commander

---

## 1. Updating Package Information

First, I refreshed the local package index using APT.

```bash
sudo apt update
```

This command downloads the latest package information from the configured repositories. It does not upgrade installed software.

## 2. Searching for Software Packages

I searched for Midnight Commander using:

```bash
apt search "midnight commander"
```

This displayed available packages related to Midnight Commander.

## 3. Installing Midnight Commander

Installed Midnight Commander using:

```bash
sudo apt install mc
```

Checked the installed version:

```bash
mc --version
```

Started the application:

```bash
mc
```

Midnight Commander is a terminal-based file manager with a two-panel interface.

**Useful navigation:**

- `Tab` – Switch between the two panels.
- `Enter` – Open a directory or file.
- `F3` – View a file.
- `F10` – Exit Midnight Commander.

## 4. Exploring Important Linux Directories

Explored important directories using `ls -la`.

### `/root`

```bash
sudo ls -la /root
```

The `/root` directory is the home directory of the root administrator.

It is normally restricted to the root user.

### `/home`

```bash
ls -la /home
```

Contains the home directories of regular users.

My EC2 instance contained:

- `/home/ubuntu`
- `/home/limon`

### `/sbin`

```bash
ls -la /sbin
```

Found that `/sbin` is a symbolic link pointing to `/usr/sbin`.

```text
/sbin -> usr/sbin
```

The `/usr/sbin` directory contains many system administration utilities.

### `/etc`

```bash
ls -la /etc
```

The `/etc` directory contains system-wide configuration files.

Some important files and directories:

| Path            | Purpose                                          |
| --------------- | ------------------------------------------------ |
| `/etc/passwd`   | User account information                         |
| `/etc/shadow`   | Password hashes and password-related information |
| `/etc/group`    | Group information                                |
| `/etc/ssh/`     | SSH configuration                                |
| `/etc/hostname` | System hostname                                  |
| `/etc/hosts`    | Local hostname-to-IP mapping                     |
| `/etc/fstab`    | Filesystem mount configuration                   |
| `/etc/apt/`     | APT configuration                                |

### `/var/log`

```bash
ls -lah /var/log
```

The `/var/log` directory stores system and application log files.

Important log files:

| File             | Purpose                                  |
| ---------------- | ---------------------------------------- |
| `auth.log`       | Authentication and authorization events  |
| `syslog`         | General system messages                  |
| `kern.log`       | Kernel-related messages                  |
| `dmesg`          | Kernel and boot messages                 |
| `dpkg.log`       | Package installation and removal history |
| `cloud-init.log` | Cloud-init initialization logs           |
| `wtmp`           | Login and logout records                 |

---

## 5. Inspecting Linux User Accounts

Viewed the contents of `/etc/passwd`:

```bash
cat /etc/passwd
```

Each entry contains seven fields separated by colons (`:`).

Example:

```text
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
```

| Field | Value          | Description                                  |
| ----- | -------------- | -------------------------------------------- |
| 1     | `ubuntu`       | Username                                     |
| 2     | `x`            | Password information stored in `/etc/shadow` |
| 3     | `1000`         | User ID (UID)                                |
| 4     | `1000`         | Group ID (GID)                               |
| 5     | `Ubuntu`       | User description                             |
| 6     | `/home/ubuntu` | Home directory                               |
| 7     | `/bin/bash`    | Default login shell                          |

Some system accounts use `/usr/sbin/nologin` as their login shell to prevent interactive login.

### Checking User Identity and Groups

```bash
id ubuntu
```

This command displays the user's UID, primary GID, and group memberships.

My `ubuntu` user belonged to the following groups:

- ubuntu
- adm
- cdrom
- sudo
- dip
- lxd

The `sudo` group allows authorized users to execute administrative commands.

---

## 6. Inspecting SSH Configuration

Viewed the SSH server configuration file:

```bash
sudo less /etc/ssh/sshd_config
```

Important SSH configuration directives include:

- `Port` – Defines the SSH listening port.
- `PermitRootLogin` – Controls direct root login.
- `PasswordAuthentication` – Controls password-based authentication.

Exited the `less` viewer by pressing:

```text
q
```

**Note:** I inspected the configuration without modifying it.

---

## 7. Inspecting Authentication Logs

Listed the log directory:

```bash
ls -lah /var/log
```

Viewed the latest 20 authentication log entries:

```bash
sudo tail -n 20 /var/log/auth.log
```

Authentication logs help administrators investigate:

- Successful SSH logins
- Failed authentication attempts
- Sudo command activity
- Other authentication-related events

---

## 8. Installing and Playing BSD Games

Installed BSD Games:

```bash
sudo apt install bsdgames
```

Started the Hangman game:

```bash
hangman
```

Played a terminal-based word guessing game.

This was a simple practical exercise to explore software installation and command-line applications.

---

## 9. Exploring APT Repository Configuration

Inspected Ubuntu's repository configuration:

```bash
cat /etc/apt/sources.list.d/ubuntu.sources
```

Important configuration fields:

| Field        | Description                               |
| ------------ | ----------------------------------------- |
| `Types`      | Package types                             |
| `URIs`       | Repository server addresses               |
| `Suites`     | Ubuntu release and update channels        |
| `Components` | Repository sections                       |
| `Signed-By`  | Keyring used to verify package signatures |

My Ubuntu instance used the following repositories:

**Main repository:**

```text
URIs: http://us-east-1.ec2.archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
```

**Security repository:**

```text
URIs: http://security.ubuntu.com/ubuntu
Suites: noble-security
```

The `noble` suite represents Ubuntu 24.04 LTS.

The AWS EC2 instance used an AWS regional Ubuntu mirror.

---

## 10. Commands Practiced

```bash
sudo apt update
apt search "midnight commander"
sudo apt install mc
mc --version
mc

sudo ls -la /root
ls -la /home
ls -la /sbin
ls -la /etc
ls -lah /var/log

cat /etc/passwd
id ubuntu

sudo less /etc/ssh/sshd_config
sudo tail -n 20 /var/log/auth.log

sudo apt install bsdgames
hangman

cat /etc/apt/sources.list.d/ubuntu.sources
```

---

## 11. What I Learned

By completing Day 04, I gained practical experience with:

- Updating package information using APT.
- Searching and installing software packages.
- Navigating the Linux filesystem using Midnight Commander.
- Understanding important directories such as `/root`, `/home`, `/sbin`, `/etc`, and `/var/log`.
- Understanding Linux user accounts, UIDs, GIDs, and groups.
- Inspecting SSH server configuration.
- Reading authentication logs.
- Installing and running terminal applications.
- Understanding APT repository configuration.
- Identifying symbolic links in the Linux filesystem.

---

## Conclusion

Day 04 helped me understand how Linux administrators manage software, explore system directories, inspect user accounts, review authentication logs, and work with package repositories.

I completed the practical exercises on an Ubuntu 24.04 LTS AWS EC2 instance.

**Next:** Linux Upskill Challenge – Day 05.
