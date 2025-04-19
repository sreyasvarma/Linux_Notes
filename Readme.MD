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
```

## Basic Bash Concepts

| Concept        | Example / Syntax                          | Description                  |
|----------------|-----------------------------------------|------------------------------|
| Variable       | `name="Linux"`                          | Declares a variable           |
| Print          | `echo "Hi $name"`                       | Prints text or variable value |
| If Condition   | `if [ $a -gt $b ]; then echo "A"; fi` | Conditional logic             |
| For Loop       | `for i in {1..5}; do echo $i; done`    | Loop over a sequence          |
| While Loop     | `while [ $i -lt 5 ]; do echo $i; ((i++)); done` | While loop            |
| Read Input     | `read name`                            | Takes input from user         |
| Function       | `greet() { echo "Hi $1"; }`            | Defines a function            |
| Call Function  | `greet "Alice"`                        | Calls a function with argument|

---

## Running a Script

```bash
chmod +x script.sh # Make script executable
./script.sh # Run the script
```

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

```bash
ls -l script.sh
```

Example output:

```
-rwxr-xr-- 1 user group 123 Apr 19 14:00 script.sh
```

### Adding Execute Permission

To allow a script to be executed, add execute permission:

```bash
chmod +x script.sh
```

or for the user only:

```bash
chmod u+x script.sh
```

### Running the Script

Once executable, run the script with:

```bash
./script.sh
```

---

## Bash `if` Statement Syntax and Examples

### Basic `if` Statement

```bash
if [ condition ]
then
  commands
fi
```

Example:

```bash
a=5
b=30
if [ $a -lt $b ]
then
  echo "a is less than b"
fi
```

Output:

```
a is less than b
```

### `if...else` Statement

```bash
if [ condition ]
then
  commands if true
else
  commands if false
fi
```

Example:

```bash
a=99
b=45
if [ $a -lt $b ]
then
  echo "a is less than b"
else
  echo "a is greater than b"
fi
```

Output:

```
a is greater than b
```

### `if...elif...else` Statement

```bash
if [ condition1 ]
then
  commands1
elif [ condition2 ]
then
  commands2
else
  commands3
fi
```

Example to determine triangle type:

```bash
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
```

---

## Bash `case` Statement Syntax

The `case` statement is useful for matching a variable against multiple patterns:

```bash
case $variable in
pattern1)
  commands ;;
pattern2)
  commands ;;
*)
  default commands ;;
esac
```

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
| `u`     | Undo                           |
| `Ctrl + r` | Redo                         |

### Miscellaneous

| Command                      | Action                                           |
|------------------------------|--------------------------------------------------|
| `:2,4cop6`                   | Copies lines 2 to 4 and pastes it after line 6   |
| `:1,3d`                      | Deletes lines 1 to 3                             |
| `:w /root/Desktop/filename`  | Saves the file to the Desktop                    |
| `:set nu`                    | Shows line numbers                               |
| `:set nonu`                  | Removes line numbers                             |

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

# 🐧 Linux Interview questions

## Basic Linux Commands & Concepts

1. What is the difference between ls and ll commands?  
   `ls` lists files and directories in the current directory.  
   `ll` is equivalent to `ls -l`, providing a detailed listing with information such as permissions, owner, size, and modification time.

2. What is a directory in Linux? How do you create one?  
   A directory in Linux is a folder used to organize files.  
   To create a directory, use the `mkdir` command:  
   ```bash
   mkdir directory_name
   ```

3. How do you view the contents of a file in Linux?  
   You can use commands like `cat`, `less`, `more`, `head`, or `tail` to view file contents:  
   ```bash
   cat filename
   less filename
   ```

4. Explain the difference between rm, rmdir, and unlink.  
   `rm` removes files or directories (with `-r` for directories).  
   `rmdir` removes empty directories.  
   `unlink` removes a single file (similar to `rm` but only for files).

5. What are symbolic links and how do you create them?  
   Symbolic links are references or pointers to other files or directories.  
   To create a symbolic link:  
   ```bash
   ln -s target_file symlink_name
   ```

6. What does the chmod command do? Can you give examples of its usage?  
   `chmod` changes file or directory permissions.  
   To give full permissions to the owner and read/execute to others:  
   ```bash
   chmod 755 file_name
   ```  
   To give read/write/execute permissions to the owner only:  
   ```bash
   chmod 700 file_name
   ```

7. How do you check disk space usage in Linux?  
   Use the `df` command to display disk space usage:  
   ```bash
   df -h
   ```

8. Explain the difference between ps, top, and htop commands.  
   `ps` displays a snapshot of running processes.  
   `top` provides a dynamic, real-time view of processes and system performance.  
   `htop` is an interactive process viewer, similar to `top`, but more user-friendly.

9. How can you redirect the output of a command to a file?  
   Use `>` to redirect output to a file:  
   ```bash
   command > output_file
   ```  
   To append output to a file, use `>>`:  
   ```bash
   command >> output_file
   ```

10. What is a pipe in Linux, and how do you use it?  
    A pipe (`|`) allows the output of one command to be used as input for another:  
    ```bash
    ls | grep "file"
    ```

## Filesystem & File Permissions

1. What are file permissions in Linux, and how do you interpret them?  
   File permissions determine access rights for users. They are displayed as a string like `rwxr-xr--`:  
   `r` = read, `w` = write, `x` = execute  
   The first set is for the file owner, the second for the group, and the third for others.

2. What is the difference between a soft link and a hard link?  
   Soft link (symlink): A symbolic link that points to the original file, can span across different filesystems, and may break if the target file is deleted.  
   Created using:  
   ```bash
   ln -s target_file link_name
   ```  
   Hard link: Points directly to the data blocks of the original file, and cannot span across different filesystems. Deleting the original file doesn't affect the hard link.  
   Created using:  
   ```bash
   ln target_file link_name
   ```

3. Explain the purpose of `/etc/fstab` file.  
   `/etc/fstab` is a configuration file that contains information about disk partitions, their mount points, and filesystems. It is used by the system to automatically mount file systems at boot.

4. How can you change file ownership in Linux?  
   Use the `chown` command to change file ownership:  
   ```bash
   chown owner:group file_name
   ```

5. What is the find command and how would you search for a file in a directory?  
   The `find` command searches for files and directories in a specified path:  
   ```bash
   find /path/to/directory -name "filename"
   ```

6. What is the du command used for, and how does it differ from df?  
   `du` (disk usage) reports the space used by files and directories:  
   ```bash
   du -sh /path/to/directory
   ```  
   `df` (disk free) shows the available disk space on the filesystem.

7. What is the difference between chmod 777 and chmod 755?  
   `chmod 777` gives read, write, and execute permissions to everyone (owner, group, others).  
   `chmod 755` gives read, write, and execute permissions to the owner, and read and execute permissions to the group and others.
