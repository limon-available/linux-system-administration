# Day 5 – More or Less: Bash Shell Productivity and Customization

## Overview

Day 5 focused on improving command-line productivity and learning essential Bash shell features used in Linux System Administration.

The practical exercises covered command auto-completion, command history, file navigation, hidden configuration files, and Bash prompt customization.

All practical exercises were performed using an **AWS EC2 Ubuntu Server**.

## Learning Environment

| Component          | Details           |
| ------------------ | ----------------- |
| Cloud Platform     | AWS EC2           |
| Operating System   | Ubuntu Server     |
| User Account       | `ubuntu`          |
| Hostname           | `limon-linux-lab` |
| Shell              | Bash              |
| Shell Location     | `/bin/bash`       |
| Configuration File | `~/.bashrc`       |
| Editor             | Nano              |

---

## 1. Tab Completion

Tab completion is a Bash feature that automatically completes command names, file names, and directory paths.

### Command Completion

Type the beginning of a command and press `Tab`.

```bash
les
```

Press `Tab` to complete the command:

```bash
less
```

### File Path Completion

```bash
less /etc/serv
```

Press `Tab` to complete the file path:

```bash
less /etc/services
```

### Handling Ambiguous Paths

```bash
less /etc/s
```

Press `Tab` twice to display possible matching entries.

**Key Benefits:**

- Reduces typing effort.
- Prevents command and file path errors.
- Improves terminal productivity.

---

## 2. Bash Command History

Bash stores previously executed commands in command history.

### Display Command History

```bash
history
```

### Display the Last 20 Commands

```bash
history 20
```

### Display the Last 10 Commands

```bash
history | tail -10
```

### Repeat a Previous Command

```bash
!20
```

This executes the command associated with history entry number 20.

For example, the following command repeats the command stored at entry 38:

```bash
!38
```

### Reverse History Search

Press:

```text
Ctrl + R
```

Then type part of a previously executed command.

Example:

```text
(reverse-i-search)`apt': sudo apt update
```

Useful keyboard shortcuts:

| Shortcut         | Description                     |
| ---------------- | ------------------------------- |
| `Ctrl + R`       | Search command history backward |
| `Ctrl + R` again | Find another matching command   |
| `Enter`          | Execute the selected command    |
| `Ctrl + G`       | Exit reverse search             |

**Practical Note:** Always verify a recalled command before executing it, especially commands involving `sudo`, `reboot`, or system configuration changes.

---

## 3. Exploring Hidden Files (Dotfiles)

In Linux, files and directories whose names begin with a dot (`.`) are hidden by convention.

### Navigate to Home Directory

```bash
cd
```

### List Visible Files

```bash
ls
```

### Display Hidden Files

```bash
ls -a
```

### Detailed File Listing

```bash
ls -l
```

### Display All Files with Details

```bash
ls -la
```

### Sort Files by Modification Time

```bash
ls -ltra
```

### Understanding the Options

| Option | Description               |
| ------ | ------------------------- |
| `-l`   | Long listing format       |
| `-a`   | Include hidden files      |
| `-t`   | Sort by modification time |
| `-r`   | Reverse sorting order     |
| `-h`   | Human-readable file sizes |

### Hidden Files Found in the Home Directory

The following files and directories were identified:

| File / Directory            | Purpose                                    |
| --------------------------- | ------------------------------------------ |
| `.bash_history`             | Stores Bash command history                |
| `.bash_logout`              | Commands executed when a login shell exits |
| `.bashrc`                   | Interactive Bash configuration             |
| `.profile`                  | User login environment configuration       |
| `.ssh`                      | SSH keys and configuration                 |
| `.cache`                    | Application cache data                     |
| `.config`                   | User application configurations            |
| `.local`                    | User-specific application data             |
| `.sudo_as_admin_successful` | Ubuntu sudo success marker                 |

### Inspecting Configuration Files

```bash
less ~/.bashrc
```

```bash
less ~/.profile
```

```bash
less ~/.bash_logout
```

```bash
less ~/.bash_history
```

**Important:** Never publish private SSH keys, credentials, or sensitive command history in a public GitHub repository.

---

## 4. Reading Files with `more` and `less`

Linux provides terminal-based utilities for viewing text files without opening a text editor.

### Using `more`

```bash
more ~/.bashrc
```

### Using `less`

```bash
less ~/.bashrc
```

### Navigation Shortcuts in `less`

| Key        | Function                          |
| ---------- | --------------------------------- |
| `g`        | Go to the beginning of the file   |
| `G`        | Go to the end of the file         |
| `/keyword` | Search forward for a keyword      |
| `n`        | Find the next matching result     |
| `N`        | Find the previous matching result |
| `Space`    | Move forward one page             |
| `b`        | Move backward one page            |
| `q`        | Quit                              |

### Comparison: `more` vs `less`

| Feature             | `more`  | `less` |
| ------------------- | ------- | ------ |
| Read text files     | Yes     | Yes    |
| Forward navigation  | Yes     | Yes    |
| Backward navigation | Limited | Yes    |
| Search              | Yes     | Yes    |
| Flexible navigation | Limited | Yes    |

**Key Learning:** `less` provides more flexible navigation and searching capabilities, making it useful when inspecting large configuration files and system logs.

---

## 5. Identifying the Current Shell

The following commands were used to inspect the current shell environment.

### Check the Current Shell

```bash
echo $SHELL
```

Output:

```text
/bin/bash
```

This confirms that Bash is the configured login shell.

### Check the Current Bash Prompt Configuration

```bash
echo $PS1
```

The output displayed the existing Ubuntu Bash prompt configuration, including username, hostname, working directory, and terminal color escape sequences.

---

## 6. Bash Prompt Customization (PS1)

The `PS1` variable controls the appearance of the primary Bash command prompt.

### Important PS1 Escape Sequences

| Escape Sequence | Description                           |
| --------------- | ------------------------------------- |
| `\u`            | Current username                      |
| `\h`            | Short hostname                        |
| `\w`            | Current working directory             |
| `\W`            | Basename of current directory         |
| `\$`            | `$` for normal users and `#` for root |
| `\t`            | Current time                          |
| `\d`            | Current date                          |

### Temporary Prompt Customization

```bash
PS1='\u@\h:\w\$ '
```

This changes the prompt for the current shell session.

### Colored Bash Prompt

```bash
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

The customization uses:

- Green: Username and hostname.
- Blue: Current working directory.
- Default terminal color: Prompt symbol.

### Making the Customization Permanent

Open the Bash configuration file:

```bash
nano ~/.bashrc
```

Add the following line:

```bash
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

Save and exit:

- `Ctrl + O` – Save the file.
- `Enter` – Confirm the filename.
- `Ctrl + X` – Exit Nano.

Reload the configuration:

```bash
source ~/.bashrc
```

### Verify the Custom Prompt

```bash
echo $PS1
```

Test directory navigation:

```bash
cd /tmp
```

```bash
cd ~
```

The working directory displayed in the prompt should change accordingly.

---

## 7. Creating a Learning Summary with Nano

Nano is a terminal-based text editor used to create and modify text files.

### Create a Summary File

```bash
nano ~/day5-summary.txt
```

The following learning summary was created:

```text
Linux System Administration
Day 5: More or Less

Topics Practiced:

1. Tab Completion
2. Bash Command History
3. Reverse History Search (Ctrl + R)
4. Hidden Files and Dotfiles
5. more and less Commands
6. Bash Configuration (.bashrc)
7. Bash Prompt Customization (PS1)

Practical Environment:
AWS EC2 Ubuntu Server

Shell:
/bin/bash

Learning Outcome:
Learned how to navigate command history,
read configuration files, explore hidden files,
and customize the Bash terminal prompt.
```

### Save and Exit Nano

| Shortcut   | Action           |
| ---------- | ---------------- |
| `Ctrl + O` | Save file        |
| `Enter`    | Confirm filename |
| `Ctrl + X` | Exit editor      |

### Verify the Summary File

```bash
cat ~/day5-summary.txt
```

---

## 8. Practical Commands Reference

A consolidated list of the commands covered in Day 5:

| Command                   | Purpose                              |
| ------------------------- | ------------------------------------ |
| `cd`                      | Navigate to home directory           |
| `ls -a`                   | Display hidden files                 |
| `ls -la`                  | Detailed listing of all files        |
| `ls -ltra`                | List files by modification time      |
| `history`                 | Display command history              |
| `history 20`              | Display recent history entries       |
| `history \| tail -10`     | Display the last 10 entries          |
| `!20`                     | Execute history entry 20             |
| `less ~/.bashrc`          | Read Bash configuration              |
| `more ~/.bashrc`          | Read a file page by page             |
| `echo $SHELL`             | Display configured login shell       |
| `echo $PS1`               | Display current prompt configuration |
| `nano ~/.bashrc`          | Edit Bash configuration              |
| `source ~/.bashrc`        | Reload Bash configuration            |
| `nano ~/day5-summary.txt` | Create a learning summary            |
| `cat ~/day5-summary.txt`  | Display the summary file             |

---

## 9. Learning Outcomes

After completing Day 5, I gained practical experience with:

- Using Bash tab completion for commands and file paths.
- Navigating and searching command history.
- Re-executing previously used commands.
- Identifying hidden files and directories.
- Exploring Linux user configuration files.
- Reading text files using `more` and `less`.
- Understanding Bash shell environment variables.
- Customizing the terminal prompt using `PS1`.
- Editing configuration files using Nano.

These skills improve command-line efficiency and provide a foundation for Linux system administration and server management.

## 10. Next Steps

Continue developing Linux administration skills through hands-on practice with:

- File and directory permissions.
- Process management.
- Package management.
- Service management using `systemctl`.
- Networking and troubleshooting.
- System monitoring and log analysis.

---

**Environment:** AWS EC2 Ubuntu Server

**Learning Track:** Linux System Administration

**Day:** 05 – More or Less

**Goal:** Building practical skills for Linux System Administrator and System Engineer roles.
