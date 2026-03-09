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