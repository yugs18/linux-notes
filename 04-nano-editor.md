# Nano Editor

Nano is a simple and beginner-friendly command-line text editor used in Linux systems.  
It is commonly used for quick file editing, especially when working in the terminal.

---

# Opening or Creating a File

To open or create a file with Nano:

```
nano <filename>
```

Example:

```
nano notes.txt
```

If the file does not exist, Nano will create it.

---

# Nano Interface Basics

When Nano opens, you will see:

- File content area in the center
- Command shortcuts at the bottom
- Status bar above the shortcuts

Example of shortcut notation:

```
^X
```

> The `^` symbol represents the **Ctrl key**.

So:

```
^X = Ctrl + X
```

---

# Basic Navigation

Move the cursor using:

- Arrow keys → move up, down, left, right
- `Ctrl + A` → move to beginning of line
- `Ctrl + E` → move to end of line
- `Ctrl + Y` → move one page up
- `Ctrl + V` → move one page down

---

# Editing Text

You can start typing immediately in Nano.

Basic editing operations:

- **Backspace** → delete previous character
- **Delete key** → delete character under cursor
- **Enter** → create a new line

---

# Saving a File

To save changes:

```
Ctrl + O
```

Steps:

1. Press `Ctrl + O`
2. Nano will ask for the file name
3. Press **Enter** to confirm

---

# Exiting Nano

To exit Nano:

```
Ctrl + X
```

If the file has unsaved changes, Nano will ask:


Save modified buffer?


Options:

- `Y` → Yes (save changes)
- `N` → No (discard changes)
- `Ctrl + C` → cancel exit

---

# Cutting and Pasting Text

## Cut a line

```
Ctrl + K
```

Cuts the current line.

---

## Paste text

```
Ctrl + U
```

Pastes the last cut text.

---

# Searching Text

To search inside the file:

```
Ctrl + W
```

Steps:

1. Press `Ctrl + W`
2. Enter the word you want to search
3. Press **Enter**

Nano will jump to the matching text.

---

# Go to a Specific Line

To jump to a specific line number:

```
Ctrl + _
```

Then enter:

```
line_number
```

Example:

```
25
```

This moves the cursor to **line 25**.

---

# Nano Help Menu

To open Nano help:

```
Ctrl + G
```

This shows all Nano commands and shortcuts.

---

# Important Nano Shortcuts Summary

| Shortcut | Action |
|--------|--------|
| Ctrl + O | Save file |
| Ctrl + X | Exit Nano |
| Ctrl + K | Cut line |
| Ctrl + U | Paste line |
| Ctrl + W | Search text |
| Ctrl + G | Help menu |
| Ctrl + A | Beginning of line |
| Ctrl + E | End of line |

---

# Nano Configuration

Nano settings can be customized using the configuration file:

```
~/.nanorc
```

This file allows you to enable options like:

- syntax highlighting
- line numbers
- tab settings