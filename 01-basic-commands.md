# Basic Linux Commands

## Navigation

### pwd
Print working directory.  
Tells you which directory you are currently in.

### cd
Change directory.

- `cd <path>` → Move to a specific path  
- `cd` → Go directly to home directory  
- `cd ..` → Go to parent directory  

### /
Root of the file system.  
Absolute paths start with `/`.

### .
Represents the current working directory (relative path).

---

## Listing Files

### ls
List contents of a directory.

Useful flags:
- `ls -l` → Long format output
- `ls -a` → Show hidden files
- `ls -la` → Long format + hidden files

---

## Viewing Files

### less
A pager. Used to view file contents page by page.

### cat
Display entire file content in terminal.

### head
Shows first 10 lines by default.

### tail
Shows last 10 lines by default.

---

## File & Directory Management

### touch
Create a file.

### mkdir
Create a directory.

- `mkdir -p` → Create multiple nested directories at once.

### mv
Move files OR rename files.

- `mv -i file1.txt /path/to/move/` → prompts before overwriting a file in the destination if a file with the same name exists.
- `mv -u ...` → moves the file if it is newer version.
- `mv -v ...` → verbose output.
- `mv -f ...` → forces the move.
- `mv /source/ /path/to/` → moves an entire directory and it's contents.
- `mv --backup` → creates a backup of the existing file in the destination if the the same file name exists.
- `mv --no-clobber`

### cp
Copy files.

- `cp -r` → Copy entire directories.

### rm
Remove a file.

- `rm -r` → Remove non-empty directory.

### rmdir
Remove an empty directory.

---

## Editors

### nano
Simple command-line text editor.

### vim / vi
More advanced and powerful text editor.