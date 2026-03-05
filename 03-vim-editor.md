// Basic of vim editor

# Vim Novice

## Move the cursor around
- h or left arror key
- l or right arrow key
- k or up arror key
- j or down arror key

## Creating/Opening a file
```
    vim <filename>
```

### vim modes
- Vim editor has two modes
    - command mode
    - editing mode

## Exiting from vim
- In command mode, type ':q!'
    - **:** -> prefaces our command
    - **q** -> quit out of Vim
    - **!** -> instructs Vim to not save the changes

## Character Deletion
- In command mode, press **x** to delete a character on which cursor is.

## Inserting text
- To insert text, press **i** in command mode and in the bootom it will show
```
    --INSERT--
```

## Saving edited file
- To save the changes
```
    :wq
```
- **w** -> will write changes
- **q** -> quit out of Vim

- **SHIFT + zz** -> shortcut for the same thing.

---

# Vim Operators and Motions

## Deleting words
- In command mode, bring cursor to the beginning of the word and press **dw**
- **dw** stands for Delete Word.

## Delete to the end of the line
- in command mode, press **d$**

> In vim, **$** sign is often used to indicate "to the end of" something.

## Motions and count number
- In command mode, entering motion key **e**, cursor will be placed to the end of the word. **w** for the beginning of the following word.
- **5e** means end of the 5th word.
- **$** -> end of the line
- **0** -> beginning of the line

## Deleting multiple words
- **d4w** -> delete 4 words.

## Deleting lines
- **dd** -> delete a single line
- **100dd** -> delete 100 lines

## Undo
- **u** -> undo the changes

---

# Vim apprentice user level

## Paste command
- when deleting lines, words or char using **d** command, vim saves them in cache. using **p** use can paste them anywhere.

## Replace operator
- **r** -> to replace the current character.
```
    rg
```
- g will replace the character on which cursor is.

## change operator
- To replace multiple characters use **c**.
- **c$** -> to replace rest of the line.

---

# Vim Experienced user level

## Advanced navigation
- **G (SHIFT + g)** -> to get to end of the file
- **gg** -> to get to the beginning of the file
- **nG** -> to get to nth line

## Searching text
- **/** or **?** -> to search for keywords or phrases.
- **/edit** -> search edit key word in forward direction. To go to next, use **n** or back **N**.
- **?edit** -> search edit key word in backward direction. To go to next, use **N** or back **n**.

> Keep in mind that if you search with / then the n key will move forward to next result and N will move backwards to previous result. If searching with ?, the keys swap – n will go backwards and N will go forward.

## Subsitution
- Vim can replace a given a pattern keyword throughout the whole text. Vim also gives you an option to replace your pattern within a certain range of line numbers. This process is called substitution. To replace the first occurrence of keyword “bash” with “perl” in your document, you can use command :s/bash/perl/. If there is a more than one keyword of “bash” on the same line, you can use command :s/bash/perl/g.

- This command can be used to replace keyword “bash” with “perl” in whole document: :%s/bash/perl/g. There may be a situation where you need to substitute a keyword within a certain line range only. In this case, you replace % with the line range. The :20,40s/bash/perl/g command would substitute “bash” for “perl” only between lines 20 and 40.

---

# Vim Veteran user level

## Execute external commands on shell
- **:!date**

## More option to write a file
- **:w** -> write without quitting vim
- **:w temp.txt** -> write to a diffent file

## Save selected text to the file
- Let’s say that you are in a situation where you have no mouse and no other windows available, and you need to take the selected text from a currently opened file and save it to another file. This situation often happens with remote ssh / telnet logins. In this case, you would use the v operator and highlight text with your navigation keys, followed by :w to save selected text to different file.

## Retrieve content from file
- **:r file.txt** -> retrive the content of file.txt to the currently opened file.

---

# Vim expert user

## open operator
- Insert a new line below your cursor with o
- Insert a new line above your cursor with O

## Copy and paste
- Yank (copy) a line with y command
- Paste the copied line with p command
- To yank five lines, use command 5y

## Customize vim’s environment
- Vim settings are stored in the ~/.vimrc file

---