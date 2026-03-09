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

---

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

---

## whatis command

Displays a short description from the manual page.

```
    whatis ls
```

---

## man command

Displays the full manual page.

```
    man date
```

---

## help command

Used for **Bash built-in commands**.

Examples:

```
    help if
    help exit
```

---

## info command

Another documentation system used by some programs.

```
    info ls
```

---
---

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

---

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

---

## Shell Variables

Shell variables:

- Exist **only in the current shell**
- Are **not inherited by child processes**
- Are used internally by the shell

Each shell (bash, zsh, etc.) has its own set of variables.

---

# Commands for Working with Variables

Several commands help manage environment variables:

| Command | Description |
|-------|-------------|
| `env` | Run programs in a modified environment or display variables |
| `printenv` | Print environment variables |
| `set` | Show all variables and shell functions |
| `unset` | Remove a variable |
| `export` | Convert a shell variable to an environment variable |

---

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

---

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

---

# Using the env Command

```
env
```

Displays all environment variables.

---

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

---

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

---

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

---

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

---

## Set Environment Variable in One Command

```
export MY_NEW_VAR="My New Variable"
```

---

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

---

# Setting Variable for a Single Command

You can assign a variable only for a specific command:

```
DEBUG=1 myapp --verbose
```

The variable exists only during that command execution.

---

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

---

# Persistent Environment Variables

To make variables permanent, add them to configuration files.

---

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

---

## System-wide Shell Configuration

```
/etc/profile
```

Example:

```
export JAVA_HOME="/path/to/java"
export PATH=$PATH:$JAVA_HOME/bin
```

---

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

---

## Additional System Scripts

```
/etc/profile.d/*.sh
```

Used for application-specific environment variables.

---

# Understanding Shell Startup Files

Different configuration files load depending on shell type.

### Login Shell

Loaded when logging in via SSH or console:

```
~/.bash_profile
~/.profile
```

---

### Interactive Shell

Loaded when opening a new terminal:

```
~/.bashrc
```

---

### Zsh Shell

```
~/.zshrc
```

---

# Apply Changes Immediately

After editing configuration files, reload them:

```
source ~/.bashrc
```

---

# Quick Reference

| Task | Command |
|----|----|
| List environment variables | `printenv` or `env` |
| Print specific variable | `echo $HOME` |
| Create shell variable | `MY_VAR=value` |
| Create environment variable | `export MY_VAR=value` |
| Remove variable | `unset MY_VAR` |
| Add directory to PATH | `export PATH="$HOME/bin:$PATH"` |
| Show all variables | `set` |
| Reload config | `source ~/.bashrc` |

---
---


