# Linux System Administration – Hands-on Learning

A practical learning journey focused on Linux System Administration, server management, and cloud infrastructure.

I am documenting my daily hands-on practice while learning Linux administration using an AWS EC2 Ubuntu Server.

The goal is to develop practical skills required for **Linux System Administrator** and **System Engineer** roles.

## Learning Environment

| Component        | Details                 |
| ---------------- | ----------------------- |
| Cloud Provider   | AWS                     |
| Cloud Service    | Amazon EC2              |
| Operating System | Ubuntu Server 24.04 LTS |
| Instance Type    | t3.micro                |
| Architecture     | x86-64                  |
| Access Method    | SSH                     |
| Shell            | Bash                    |
| Server Hostname  | limon-linux-lab         |

## Learning Progress

| Day                          | Topics                                                                    | Status    |
| ---------------------------- | ------------------------------------------------------------------------- | --------- |
| [Day 01](./Day-01/README.md) | Linux Fundamentals & Getting Started                                      | Completed |
| [Day 02](./Day-02/README.md) | Filesystem Navigation & File Management                                   | Completed |
| [Day 03](./Day-03/README.md) | User Management, Sudo & System Configuration                              | Completed |
| [Day 04](./Day-04/README.md) | Software Installation & Filesystem Exploration                            | Completed |
| [Day 05](./Day-05/README.md) | Bash Shell Productivity, Command History, Dotfiles & Prompt Customization | Completed |

## Topics I'm Learning

### Linux Fundamentals

- Linux command-line interface
- Filesystem hierarchy
- Absolute and relative paths
- File and directory management
- Linux manual pages and documentation
- Bash shell fundamentals
- Command-line productivity

### User and System Administration

- Linux user and password management
- Sudo privileges
- Hostname and timezone configuration
- System reboot and uptime monitoring
- Login history and system logs
- User and group identification

### File and Access Management

- File permissions (`chmod`)
- Ownership management (`chown`, `chgrp`)
- User, group, and other permissions
- Permission notation (`rwx`, `755`, `644`)
- Hidden files and directories
- Linux dotfiles and user configurations

### Software and Package Management

- APT package management
- Updating package lists
- Searching and installing software
- Exploring installed command-line tools
- Understanding APT repository configuration
- Midnight Commander (`mc`)

### Bash Shell and Command-Line Productivity

- Bash command history (`history`)
- Re-executing previous commands (`!n`)
- Reverse history search (`Ctrl + R`)
- Tab completion for commands and file paths
- Viewing files with `more` and `less`
- Navigating and searching text files
- Bash configuration (`.bashrc`, `.profile`)
- Bash environment variables (`SHELL`, `PS1`)
- Customizing the Bash prompt using `PS1`
- Editing configuration files using Nano

### Server Administration

- Linux process management
- Service management with systemd
- Disk and storage management
- Networking and troubleshooting
- SSH administration
- Log monitoring
- Exploring system configuration files

## Skills & Tools

**Operating Systems**

- Ubuntu Server 24.04 LTS
- Linux

**Cloud & Infrastructure**

- AWS EC2
- SSH
- Linux Server Administration

**Command-Line Tools**

- Bash
- GNU Core Utilities
- APT
- Midnight Commander
- `more` and `less`
- Nano
- `history`
- `journalctl`
- systemd

**Version Control**

- Git
- GitHub

## Repository Structure

```text
linux-system-administration/
│
├── README.md
│
├── Day-01/
│   └── README.md
│
├── Day-02/
│   └── README.md
│
├── Day-03/
│   └── README.md
│
├── Day-04/
│   └── README.md
│
└── Day-05/
    ├── README.md
    └── day5-summary.txt
```

## Learning Approach

- Follow a structured daily learning plan.
- Practice commands directly on an Ubuntu Server.
- Perform real server administration tasks.
- Explore Linux configuration files and system directories.
- Document commands, outputs, and practical learnings.
- Maintain progress through GitHub.
- Build practical knowledge through continuous experimentation.

## Learning Resource

- [Linux Upskill Challenge](https://github.com/livialima/linuxupskillchallenge)

---

**Current Goal:** Build practical Linux System Administration skills through consistent hands-on practice.

**Status:** In Progress 🚀
