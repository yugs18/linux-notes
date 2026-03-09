# Command Path in Shell

The command path is a variable used by the shell to determine **where to look for executable files** when running commands.

Linux commands are essentially programs stored in specific directories. Normally, you would need to type the **absolute path** of a program to run it. However, the shell automatically searches certain directories listed in the `$PATH` environment variable.

This allows you to run commands without typing the full path every time.

Example:

```
/bin/ls
```

Instead of typing the full path, you can simply run:

```
ls
```

because `/bin` is included in `$PATH`.

---

# Viewing the Current `$PATH`

To display the directories stored in `$PATH`:

```
echo $PATH
```

For a cleaner output (one directory per line):

```
echo "${PATH//:/$'\n'}"
```

---

# Finding the Location of a Command

To see which directory a command comes from:

```
which date
```

To display **all matching command paths**:

```
which -a ls
```

---

# Add Directory to PATH Variable

Adding a directory to `$PATH` allows you to run programs or scripts stored there **from anywhere in the system**.

---

## Temporarily Add a Directory to `$PATH`

This change lasts **only for the current terminal session**.

```
export PATH="/bin/myscripts:$PATH"
```

---

## Permanently Add a Directory to `$PATH`

To permanently add a directory, edit the user's `.bashrc` file.

```
nano ~/.bashrc
```

Add the following line at the end of the file:

```
export PATH="/bin/myscripts:$PATH"
```

Save the file and apply the changes:

```
source ~/.bashrc
```

Alternatively, log out and log back in.

---

# Remove a Directory from `$PATH`

To remove a directory from `$PATH`, edit the appropriate configuration file and remove the entry.

Common locations:

- `~/.bashrc` → user-specific configuration
- `/etc/environment` → system-wide configuration

# Finding the Type of a Linux Command

The `type` command shows whether a command is:

- a shell builtin
- an alias
- a function
- an external program

Examples:

```
type command
type -t command
type -a command
```

---

# Hard Links vs Soft Links

## Hard Links

Hard links create **multiple directory entries for the same file**.

Characteristics:

- Cannot link directories
- Cannot cross filesystem boundaries
- All links refer to the same underlying inode
- If the original file is deleted, the data remains accessible through the hard link

---

## Soft Links (Symbolic Links)

Symbolic links are **special files that point to another file or directory**.

Characteristics:

- Can link directories
- Can cross filesystem boundaries
- If the original file is removed, the symbolic link becomes broken

---

# Finding the Real Path of a Symlink

Sometimes commands are symbolic links.

To see the link:

```
ls -l /bin/ls
```

To resolve the real file path:

```
realpath /bin/ls
```

or

```
readlink -f /bin/ls
```

---

# Display Information About Commands

```
command -v date
```

This displays the location of a command.

---

# Finding Command Binaries and Man Pages

The `whereis` command finds the binary, source code, and manual page for a program.

Example:

```
whereis gcc
```

Search only for binaries:

```
whereis -b ls
```

Search only for manual pages:

```
whereis -m date
```

---

# Finding Files in Linux

## locate command

Search for files quickly using a database:

```
locate -b '\date'
```

---

## find command

Search directly in the filesystem:

```
find / -name "date" -ls
```

To search the entire system (requires sudo):

```
sudo find / -name "date" -ls
```

---

# Displaying Help About Linux Commands

Linux provides several ways to access command documentation.

## whatis command

Displays a short description from the manual page.

```
whatis ls
```

## man command

Displays the full manual page.

```
man date
```

## help command

Used for **Bash built-in commands**.

Examples:

```
help if
help exit
```

## info command

Another documentation system used by some programs.

```
info ls
```

# Environment Variables in Linux

Environment variables are dynamic values that affect the behavior of processes and programs running on a system.

Variables in Linux are generally classified into two types:

- **Environment Variables**
- **Shell Variables**

---

# Variable Syntax

Variables are defined using the following syntax:

```
KEY=value
KEY="Some other value"
KEY=value1:value2
```

Important rules:

- Variable names are **case-sensitive**
- By convention, environment variables are **UPPERCASE**
- **No spaces** are allowed around `=`
- Multiple values are separated using `:`

Example:

```
PATH=/usr/local/bin:/usr/bin:/bin
```

# Types of Variables

## Environment Variables

Environment variables:

- Are **available system-wide**
- Are **inherited by child processes**
- Affect how programs behave

Examples:

- `PATH`
- `HOME`
- `USER`
- `LANG`

## Shell Variables

Shell variables:

- Exist **only in the current shell**
- Are **not inherited by child processes**
- Are used internally by the shell

Each shell (bash, zsh, etc.) has its own set of variables.

# Commands for Working with Variables

Several commands help manage environment variables:

| Command    | Description                                                 |
| ---------- | ----------------------------------------------------------- |
| `env`      | Run programs in a modified environment or display variables |
| `printenv` | Print environment variables                                 |
| `set`      | Show all variables and shell functions                      |
| `unset`    | Remove a variable                                           |
| `export`   | Convert a shell variable to an environment variable         |

# Listing Environment Variables

The most common command is:

```
printenv
```

Example output:

```
SHELL=/bin/bash
USER=linuxize
HOME=/home/linuxize
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
TERM=xterm-256color
```

## Display a Specific Variable

```
printenv HOME
```

Output:

```
/home/linuxize
```

Multiple variables:

```
printenv LANG PWD
```

# Using the env Command

```
env
```

Displays all environment variables.

# Using the set Command

```
set
```

Displays:

- environment variables
- shell variables
- shell functions

Because output is large, use:

```
set | less
```

# Printing Variables with echo

You can display variables using:

```
echo $VARIABLE_NAME
```

Example:

```
echo $BASH_VERSION
```

Output:

```
5.2.21(1)-release
```

# Setting Variables

## Creating a Shell Variable

```
MY_VAR="Linux"
```

Check it:

```
echo $MY_VAR
```

Output:

```
Linux
```

However this variable is **not an environment variable**.

Verify with:

```
printenv MY_VAR
```

(no output)

# Exporting Environment Variables

Convert a shell variable to an environment variable:

```
export MY_VAR
```

Now it becomes available to child processes.

Verify:

```
printenv MY_VAR
```

Output:

```
Linux
```

## Set Environment Variable in One Command

```
export MY_NEW_VAR="My New Variable"
```

# Variables in Child Shells

Without export:

```
bash -c 'echo $MY_VAR'
```

Output:

(empty)

With export:

```
export MY_VAR
bash -c 'echo $MY_VAR'
```

Output:

```
Linux
```

# Setting Variable for a Single Command

You can assign a variable only for a specific command:

```
DEBUG=1 myapp --verbose
```

The variable exists only during that command execution.

# Removing Variables

Use `unset`:

```
unset MY_VAR
```

Verify removal:

```
echo $MY_VAR
```

Output:

(empty)

# Persistent Environment Variables

To make variables permanent, add them to configuration files.

## System-wide Variables

```
/etc/environment
```

Example:

```
FOO=bar
TEST_VAR="Example"
```

This file **does not support `export`**.

## System-wide Shell Configuration

```
/etc/profile
```

Example:

```
export JAVA_HOME="/path/to/java"
export PATH=$PATH:$JAVA_HOME/bin
```

## User-specific Configuration

For Bash users:

```
~/.bashrc
```

Example:

```
export PATH="$HOME/bin:$PATH"
```

For Zsh users:

```
~/.zshrc
```

## Additional System Scripts

```
/etc/profile.d/*.sh
```

Used for application-specific environment variables.

# Understanding Shell Startup Files

Different configuration files load depending on shell type.

### Login Shell

Loaded when logging in via SSH or console:

```
~/.bash_profile
~/.profile
```

### Interactive Shell

Loaded when opening a new terminal:

```
~/.bashrc
```

### Zsh Shell

```
~/.zshrc
```

# Apply Changes Immediately

After editing configuration files, reload them:

```
source ~/.bashrc
```

# Quick Reference

| Task                        | Command                         |
| --------------------------- | ------------------------------- |
| List environment variables  | `printenv` or `env`             |
| Print specific variable     | `echo $HOME`                    |
| Create shell variable       | `MY_VAR=value`                  |
| Create environment variable | `export MY_VAR=value`           |
| Remove variable             | `unset MY_VAR`                  |
| Add directory to PATH       | `export PATH="$HOME/bin:$PATH"` |
| Show all variables          | `set`                           |
| Reload config               | `source ~/.bashrc`              |

# Redirects in Linux

The shell in Linux provides a powerful way to manage **input and output streams** of commands. This mechanism is called **Redirection**.

Linux is a multi-user, multitasking operating system. Every process typically has three standard streams opened:

| Stream         | Description                                       | Default  |
| -------------- | ------------------------------------------------- | -------- |
| **stdin (0)**  | Standard Input – where the process reads input    | Keyboard |
| **stdout (1)** | Standard Output – where normal output is written  | Terminal |
| **stderr (2)** | Standard Error – where error messages are written | Terminal |

---

# Output Redirection

Output redirection allows you to send the output of a command to a **file instead of the terminal**.

## Redirect Output to File

```
command > file
```

Example:

```
ls > files.txt
```

This writes the output of `ls` to `files.txt`.

If the file exists, it will be **overwritten**.

## Append Output to File

To append output instead of overwriting:

```
command >> file
```

Example:

```
date >> log.txt
```

This adds the output to the end of `log.txt`.

# Error Redirection

Error messages can be redirected separately.

## Redirect Error Output

```
command 2> file
```

Example:

```
ls nonexistentfile 2> error.txt
```

The error message will be written to `error.txt`.

## Append Error Output

```
command 2>> file
```

Example:

```
ls nonexistentfile 2>> errors.log
```

# Redirect Both Output and Errors

Sometimes you want to store **both stdout and stderr**.

```
command > file 2>&1
```

Example:

```
ls /home /nonexistent > output.txt 2>&1
```

This writes both normal output and errors into `output.txt`.

# Discard Output

Linux provides a special device called **/dev/null**.

Anything redirected here is discarded.

Example:

```
command > /dev/null
```

Ignore errors:

```
command 2> /dev/null
```

Ignore both output and errors:

```
command > /dev/null 2>&1
```

# Input Redirection

Input can also be redirected from a file instead of the keyboard.

```
command < file
```

Example:

```
sort < names.txt
```

The command reads input from `names.txt`.

# Pipes

A **pipe** sends the output of one command as input to another command.

Symbol:

```
|
```

Example:

```
ls | less
```

Here:

- `ls` produces output
- `less` receives it as input

Another example:

```
ps aux | grep firefox
```

# Here Documents

A **here document** allows multiple lines of input to be passed to a command.

```
command << EOF
text line 1
text line 2
EOF
```

Example:

```
cat << EOF
Hello
Linux
EOF
```

# File Descriptors

Each stream has a number called a **file descriptor**.

| Descriptor | Name   |
| ---------- | ------ |
| 0          | stdin  |
| 1          | stdout |
| 2          | stderr |

Example:

```
ls > output.txt
```

Same as:

```
ls 1> output.txt
```

---

# Quick Reference

| Symbol      | Meaning                        |
| ----------- | ------------------------------ |
| `>`         | Redirect output                |
| `>>`        | Append output                  |
| `2>`        | Redirect error                 |
| `2>>`       | Append error                   |
| `<`         | Redirect input                 |
| `\|`        | Pipe output to another command |
| `/dev/null` | Discard output                 |

---

# Examples

Save command output:

```
ls > files.txt
```

Append logs:

```
date >> log.txt
```

Ignore errors:

```
rm file.txt 2> /dev/null
```

Pipe commands:

```
cat file.txt | grep linux
```

# Super User (Root)

The **Super User**, also known as the **root user**, is a special account in Linux that has **complete administrative privileges** over the system.

The root user has unrestricted access to:

- All files and directories
- System configuration files
- User accounts
- Installed software
- Hardware devices

Because of this unrestricted access, the root user can perform **any operation on the system**.

---

# Root User Capabilities

The root user can perform tasks such as:

- Installing or removing software
- Creating or deleting user accounts
- Changing file ownership and permissions
- Modifying system configuration files
- Starting and stopping system services
- Managing hardware devices
- Accessing all files on the system

Example:

```
apt install nginx
```

Installing software usually requires root privileges.

---

## Why Root Access Is Dangerous

Because the root user has no restrictions, incorrect commands can damage the system.

Examples of dangerous commands:

```
rm -rf /
```

This could delete the entire filesystem.

For this reason, it is recommended to avoid working directly as root unless necessary.

---

# Accessing the Super User

There are two common ways to gain root privileges.

## sudo Command

`sudo` allows a permitted user to run a command as the root user.

Syntax:

```
sudo command
```

Example:

```
sudo apt update
```

The user will be prompted for their own password.

`sudo` is the recommended method for performing administrative tasks.

## su Command

The `su` command allows switching to another user account.

To switch to root:

```
su
```

You must enter the root user's password.

Example:

```
su -
```

The `-` loads the root user's environment.

# Difference Between sudo and su

| Command | Description                                        |
| ------- | -------------------------------------------------- |
| `sudo`  | Run a single command with root privileges          |
| `su`    | Switch to another user account                     |
| `su -`  | Switch to another user with full login environment |

Example with sudo:

```
sudo systemctl restart nginx
```

Example with su:

```
su -
```

# Checking the Current User

To see the current user:

```
whoami
```

Example output:

```
root
```

# Running a Root Shell Temporarily

You can start a root shell using:

```
sudo -i
```

or

```
sudo su
```

This gives you a temporary root session.

# Best Practices for Using Root

- Use sudo instead of logging in as root
- Only run commands requiring administrative privileges
- Avoid modifying system files unless necessary
- Always double-check commands before running them

# Quick Reference

| Command        | Purpose                            |
| -------------- | ---------------------------------- |
| `sudo command` | Run command as root                |
| `su`           | Switch user                        |
| `su -`         | Switch user with login environment |
| `whoami`       | Show current user                  |
| `sudo -i`      | Start root shell                   |

---
---
---