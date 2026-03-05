# Vim Novice

## Move the cursor around
- `h` or left arrow key → move left
- `l` or right arrow key → move right
- `k` or up arrow key → move up
- `j` or down arrow key → move down

## Creating / Opening a file
```
vim <filename>
```

### Vim modes
Vim editor has two primary modes for beginners to understand:

- **Command mode (Normal mode)**
- **Editing mode (Insert mode)**

---

## Exiting from Vim
In command mode, type:
```
:q!
```

- `:` → prefixes a command  
- `q` → quit Vim  
- `!` → instructs Vim **not to save changes**

---

## Character Deletion
In command mode, press:
```
x
```

Deletes the character under the cursor.

---

## Inserting text
To insert text, press:
```
i
```

Then Vim enters **Insert mode** and the bottom will show:
```
-- INSERT --
```

---

## Saving edited file
To save the changes:
```
:wq
```

- `w` → write (save) changes
- `q` → quit Vim

Shortcut:

```
Shift + ZZ
```

---

# Vim Operators and Motions

## Deleting words
In command mode, bring the cursor to the beginning of the word and press:

```
dw
```

`dw` stands for **delete word**.

---

## Delete to the end of the line
In command mode press:

```
d$
```

In Vim, the `$` sign often indicates **the end of a line**.

---

## Motions and count number

Motion keys:

- `e` → move cursor to end of the word
- `w` → move cursor to beginning of the next word

Example:

```
5e
```

Moves cursor to the **end of the 5th word**.

Other useful motions:

- `$` → end of the line
- `0` → beginning of the line

---

## Deleting multiple words

```
d4w
```

Deletes **four words**.

---

## Deleting lines

```
dd
```

Delete a single line.

```
100dd
```

Delete **100 lines**.

---

## Undo

```
u
```

Undo the last change.

---

# Vim Apprentice User Level

## Paste command
When deleting lines, words, or characters using the `d` command, Vim stores them in a **buffer (register)**.

Use:

```
p
```

to paste the deleted content.

---

## Replace operator

```
r
```

Replace the current character.

Example:

```
rg
```

Replaces the character under the cursor with **g**.

---

## Change operator
To replace multiple characters use the `c` operator.

Example:

```
c$
```

Replaces text **from the cursor to the end of the line**.

---

# Vim Experienced User Level

## Advanced navigation

```
G
```

Go to **end of file**

```
gg
```

Go to **beginning of file**

```
nG
```

Go to **line number n**

Example:

```
20G
```

Jump to line **20**.

---

## Searching text

Search commands:

```
/keyword
```

Search forward.

```
?keyword
```

Search backward.

Example:

```
/edit
```

Search for **edit** moving forward.

Navigation:

- `n` → next result
- `N` → previous result

Note:

If searching with `/`,  
- `n` moves forward  
- `N` moves backward  

If searching with `?`, the behavior reverses.

---

## Substitution (Replace text)

Replace first occurrence in a line:

```
:s/bash/perl/
```

Replace all occurrences in the same line:

```
:s/bash/perl/g
```

Replace in the entire document:

```
:%s/bash/perl/g
```

Replace within a line range:

```
:20,40s/bash/perl/g
```

This replaces **bash with perl between lines 20 and 40**.

---

# Vim Veteran User Level

## Execute external commands in shell

```
:!date
```

Runs a shell command from inside Vim.

---

## More options to write a file

```
:w
```

Write (save) file without quitting Vim.

```
:w temp.txt
```

Save the current content into **temp.txt**.

---

## Save selected text to a file

You can visually select text and save it to another file.

Steps:

1. Press `v` to enter **visual mode**
2. Select text using navigation keys
3. Use:

```
:w newfile.txt
```

This writes the selected text to another file.

---

## Retrieve content from another file

```
:r file.txt
```

This inserts the contents of **file.txt** into the current file.

---

# Vim Expert User

## Open operator

Insert a new line **below** the cursor:

```
o
```

Insert a new line **above** the cursor:

```
O
```

---

## Copy and paste

Yank (copy) a line:

```
yy
```

Paste copied line:

```
p
```

Copy multiple lines:

```
5yy
```

Copy **five lines**.

---

## Customize Vim environment

Vim settings are stored in:

```
~/.vimrc
```

You can customize keybindings, themes, and editor behavior using this file.