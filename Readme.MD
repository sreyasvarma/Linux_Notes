# 🐧 Linux Study Notes

A quick reference to understanding how a Linux system works and useful resources for deeper learning.

---

## 📖 Structure of a Linux System

A Linux system is generally divided into three main parts:

### 🖥️ 1. **Hardware**
This includes all the physical components that your system runs on:
- CPU
- RAM
- Disks
- Peripherals

### 🧠 2. **Linux Kernel**
The **core** of the Linux operating system.  
It manages communication between hardware and software:
- Controls memory and processes
- Manages device drivers and system calls
- Handles networking and filesystems

### 👤 3. **User Space**
Where users and applications interact with the system.  
This includes:
- User interfaces (shells, GUIs)
- Utilities and commands (e.g., `ls`, `grep`, `nano`)
- User processes and services

---

## 📚 References & Learning Resources

| Resource | Description |
|----------|-------------|
| [**The Linux Documentation Project**](https://tldp.org) | Guides, HOWTOs, and technical documentation. Old-school look, but excellent content. |
| [**Linux Journey**](https://linuxjourney.com) | Beginner-friendly visual guide through Linux topics. Great for learning at your own pace. |
| [**ExplainShell**](https://explainshell.com) | Paste any command and get a breakdown of what each part does. Perfect for understanding shell syntax. |
| [**LinuxCommand.org**](https://linuxcommand.org) | Focused on command-line basics and shell scripting for beginners and power users alike. |

---

# Common Bash Concepts

## Basic Script Template
```bash
#!/bin/bash
echo "Hello, World!"

## Basic Bash Concepts

| Concept        | Example / Syntax                          | Description                 |
|----------------|-----------------------------------------|-----------------------------|
| Variable       | `name="Linux"`                          | Declares a variable          |
| Print          | `echo "Hi $name"`                       | Prints text or variable value|
| If Condition   | `if [ $a -gt $b ]; then echo "A"; fi` | Conditional logic            |
| For Loop       | `for i in {1..5}; do echo $i; done`    | Loop over a sequence         |
| While Loop     | `while [ $i -lt 5 ]; do echo $i; ((i++)); done` | While loop           |
| Read Input     | `read name`                            | Takes input from user        |
| Function       | `greet() { echo "Hi $1"; }`            | Defines a function           |
| Call Function  | `greet "Alice"`                        | Calls a function with argument|

---

## Running a Script

chmod +x script.sh # Make script executable
./script.sh # Run the script

---

## System Management Commands

### Process and Resource Monitoring

| Command     | Description                      |
|-------------|---------------------------------|
| `ps aux`    | Show all running processes       |
| `top`       | Live system resource usage       |
| `htop`      | Interactive process viewer (if installed) |
| `kill PID`  | Terminate a process by its PID   |
| `df -h`     | Disk space usage in human-readable format |
| `du -sh`    | Show size of current directory   |
| `free -h`   | Show memory usage                |
| `uptime`    | Show system uptime and load average |

### Managing Services with systemctl

| Command                     | Description                       |
|-----------------------------|---------------------------------|
| `systemctl status`          | View overall system status        |
| `systemctl start nginx`     | Start a service                   |
| `systemctl stop nginx`      | Stop a service                   |
| `systemctl restart nginx`   | Restart a service                |
| `systemctl enable nginx`    | Enable service on boot           |
| `systemctl disable nginx`   | Disable service from boot        |
| `systemctl is-active nginx` | Check if a service is running    |

---

## vi/vim Cheat Sheet (Editing Files in Terminal)

### Modes

- `Esc` — Normal mode
- `i` — Insert before cursor
- `a` — Insert after cursor
- `:` — Command-line mode

### Insert Mode Commands

| Command | Description                  |
|---------|------------------------------|
| `i`     | Insert at cursor             |
| `I`     | Insert at beginning of line  |
| `a`     | Append after cursor          |
| `A`     | Append at end of line        |
| `o`     | Open new line below          |
| `O`     | Open new line above          |

---

## File Permissions and Executing Bash Scripts

### Understanding File Permissions

Linux file permissions control who can read, write, or execute a file. Permissions apply separately to:

- **User** (owner)
- **Group**
- **Others**

Permission types:

- **Read (r)**: Ability to read the file
- **Write (w)**: Ability to modify the file
- **Execute (x)**: Ability to run the file as a program or script

### Checking Permissions

Use `ls -l` to view permissions:

ls -l script.sh

Example output:

-rwxr-xr-- 1 user group 123 Apr 19 14:00 script.sh

### Adding Execute Permission

To allow a script to be executed, add execute permission:

chmod +x script.sh

or for the user only:

chmod u+x script.sh

### Running the Script

Once executable, run the script with:

./script.sh

---

## Bash `if` Statement Syntax and Examples

### Basic `if` Statement

if [ condition ]
then
commands
fi

Example:

a=5
b=30
if [ $a -lt $b ]
then
echo "a is less than b"
fi

Output:

a is less than b

### `if...else` Statement

if [ condition ]
then
commands if true
else
commands if false
fi

Example:

a=99
b=45
if [ $a -lt $b ]
then
echo "a is less than b"
else
echo "a is greater than b"
fi

Output:

a is greater than b

### `if...elif...else` Statement

if [ condition1 ]
then
commands1
elif [ condition2 ]
then
commands2
else
commands3
fi

Example to determine triangle type:

read a
read b
read c

if [ $a == $b -a $b == $c ]
then
echo EQUILATERAL
elif [ $a == $b -o $b == $c -o $a == $c ]
then
echo ISOSCELES
else
echo SCALENE
fi

---

## Bash `case` Statement Syntax

The `case` statement is useful for matching a variable against multiple patterns:

case $variable in
pattern1)
commands ;;
pattern2)
commands ;;
*)
default commands ;;
esac

- Patterns can include wildcards and multiple options separated by `|`.
- The `*)` pattern acts as a default case.
- Each pattern block ends with `;;`.
- The statement ends with `esac` (case spelled backward).

---

## 📝 vi/vim Cheat Sheet (Editing Files in Terminal)

### 📌 Modes
- `Esc` — Normal mode
- `i` — Insert before cursor
- `a` — Insert after cursor
- `:` — Command-line mode

### 🖊️ Insert Mode
| Command | Description                     |
|---------|---------------------------------|
| `i`     | Insert at cursor                |
| `I`     | Insert at beginning of line     |
| `a`     | Append after cursor             |
| `A`     | Append at end of line           |
| `o`     | Open new line below             |
| `O`     | Open new line above             |


### 💾 Save and Exit
| Command | Action                         |
|---------|--------------------------------|
| `:w`    | Save file                      |
| `:q`    | Quit                           |
| `:wq`   | Save and quit                  |
| `:q!`   | Quit without saving            |

### ✂️ Editing
| Command | Action                          |
|---------|---------------------------------|
| `x`     | Delete character                |
| `dd`    | Delete line                     |
| `yy`    | Copy line                       |
| `p`     | Paste after cursor              |
| `u`     | Undo                            |
| `Ctrl + r` | Redo                         |

### 🔍 Searching
- `/text` — Search forward
- `?text` — Search backward
- `n` — Repeat search

---

## 💻 Common Terminal Commands

| Command | Description                       |
|---------|-----------------------------------|
| `ls`    | List files and directories        |
| `cd`    | Change directory                  |
| `pwd`   | Print current directory           |
| `touch file.txt` | Create a new file        |
| `mkdir mydir` | Create a new directory      |
| `rm file.txt` | Remove a file               |
| `rmdir mydir` | Remove an empty directory   |
| `cp file1 file2` | Copy file                |
| `mv file1 newname` | Rename/move file       |
| `cat file.txt` | View file content          |
| `echo "hello"` | Print text                 |
| `clear` | Clear the terminal screen         |

---

> ✨ *This document is a living reference — feel free to fork and add your own insights!*

