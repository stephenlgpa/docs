[Vim Editor Commands](https://www.radford.edu/~mhtay/CPSC120/VIM_Editor_Commands.htm)

# Vim Editor Commands

Vim is a unix text editor.

---

## Modes

Vim works in a number of modes.

- **Command Mode** (`esc`)
	- issue commands
	- navigate and edit text
- **Insert Mode** (`a`/`A`/`i`/`I`/`o`/`O`)
	- insert text
- **Visual Mode** (`v`)
	- mark text
	- copy paste

## Common VIM Commands

### Text Entry Commands (to begin text entry)

- `a`	Append text following current cursor position
- `A`	Append text to the end of current line
- `i`	Insert text before the current cursor position
- `I`	Insert text at the beginning of the cursor line
- `o`	Open up a new line following the current line and add text there
- `O`	Open up a new line in front of the current line and add text there

The following commands are used only in the commands mode.

### Cursor Movement Commands

- `h`	Moves the cursor one character to the left
- `l`	Moves the cursor one character to the right
- `k`	Moves the cursor up one line
- `j`	Moves the cursor down one line
- `nG` or `:n`	Cursor goes to the specified (n) line (e.g. 10G goes to line 10)
- `^F`	Forward screenful
- `^B`	Backward screenful
- `^f`	One page forward
- `^b`	One page backward
- `^U`	Up half screenful
- `^D`	Down half screenful
- `$`	Move cursor to the end of current line
- `0` (zero)	Move cursor to the beginning of current line
- `w`	Forward one word
- `b`	Backward one word

### Exit Commands

- `:wq`	Write file to disk and quit the editor
- `:q!`	Quit (no warning)
- `:q`	Quit (a warning is printed if a modified file has not been saved)
- `ZZ`	Save workspace and quit the editor (same as :wq)
- `: 10,25 w temp`	Write lines 10 through 25 into file named temp. Of course, other line numbers can be used. (Use :f to find out the line numbers you want.
- `qall`	Quits VIM unless there are unmodified files.
- `wall`	Saves all unmodified files.
- `:wqall`	Writes all modified files and quits VIM.
- `:qall!`	Quits VIM without saving any modified files


### Text Deletion Commands

- `x`	Delete character
- `dw`	Delete word from cursor on
- `db`	Delete word backward
- `dd`	Delete line
- `d$`	Delete to end of line
- `d^`	(d caret, not CTRL d) Delete to beginning of line

### Yank (has most of the options of delete)-- VI's copy commmand

- `yy`	yank current line
- `y`$	yank to end of current line from cursor
- `yw`	yank from cursor to end of current word
- `5yy`	yank, for example, 5 lines

### Paste (used after delete or yank to recover lines.)

- `p`	paste below cursor
- `P`	paste above cursor
- `2p` paste from buffer 2 (there are 9)
- `u`	Undo last change
- `U`	Restore line
- `J`	Join next line down to the end of the current line

### Split Windows Commands

- `:split`	Creates a new split window on the current file.
- `:split filename.txt`	Creates new split window with the file 'filename.txt'.
- `:5split`	Open a new split '5' lines high. Can include a filename to edit.
- `:new`	Creates a new split window on a new file.
- `ctrl-w w` `ctrl-w ctrl-w`	Moves between split windows.
- `:close`	Closes the window, not exiting VIM on the last window.
- `:quit` or `ZZ`	Also close the current window, but will exit VIM last window.
- `:only`	Closes all windows but the current one. If there are unsaved changes in other windows, the command will produce an error.
- `ctrl-w +`	Add a line to the height of the current window.
- `ctrl-w -`	Subtract a line from the height of the current window.
- `4 ctrl-w +`	Makes the window 4 lines higher.
- `2 ctrl-w -`	Makes the window 2 lines lower.
- `n ctrl-w _`	Set the window height to `n` lines.
- `ctrl-w _`	Set the window height to its maximum.

### Split Windows Vertically

- `vsplit`	splits the current window vertically
- `vsplit filename.txt`	splits a new window vertically opening the file 'filename.txt'
- `vnew`	Splits a new window vertically

### Moving Between Windows

- `ctrl-w h`	move to window on the left
- `ctrl-w j`	move to window below
- `ctrl-w k`	move to window above
- `ctrl-w l`	move to window on the right
- The cursor keys can also be used. E.g.:
	- `ctrl-w cursor-right`	move to window on the right
	- etc...

### Moving Window Positions

Windows can be moved to different positions on the screen. I've found it takes some divination to predict the final result, but it does work. Simply use the same commands as moving between windows, but with uppercase characters.

- `ctrl-w H`	Move the window to the left
- `ctrl-w J`	Move the window to the bottom
- `ctrl-w K`	Move the window to the top
- `ctrl-w L`	Move the window to the right

### Settings for Window heights

- `set winheight=n`	minimal desired window height (n)
- `set winminheight=n`	hard minimum window height (n)
- `set winwidth=n`	minimum desired window width (n)
- `set winminwidth=n`	hard minimum window width (n)
- `equalalways`	VIM equalises window sizes on demand. 

### Tabs

Tabs (tab pages) are overlapping files (or views of the same file), just like in GUI-based native apps. They make best use of screen space for many files. Within each tab, there can be multiple split windows. 

- `:tabedit filename`	Places all open files into tabs, and opens a new tab editing new file 'filename'.
- `:tab split`	Opens a new tab with the same file being edited.
- `gt`	"Goto Tab": moves to the next tab
- `tab help gt`	Opens a new tab with help for the command `gt`. This will work for any command that opens a new window.
- `:tabonly`	Closes all tabs except the current one, unless there are unsaved changes.
- 

### File Manipulation Commands

- `:w`	Write workspace to original file
- `:w filename`	Write workspace to named file
- `:e filename`	Start editing a new file
- `:r filename`	Read contents of a file to the workspace
- To create a page break, while in the insert mode, press the `ctrl` key. `l. ^L` will appear in your text and will cause the printer to start.

## Other Useful Commands

- Most commands can be repeated **n** times by typing a number, n, before the command. For example `10dd` means *delete 10 lines*.
- `.`	Repeat last command
- `cw`	Change current word to a new word
- `r`	Replace one character at the cursor position
- `R`	Begin overstrike or replace mode, use ESC key to exit
- `:/`	pattern Search forward for the pattern
- `:?`	pattern Search backward for the pattern
- `n`	(used after either of the 2 search commands above to continue to find next occurrence of the pattern.
- `:g/pat1/s//pat2/g`	replace every occurrence of pattern1 (pat1) with pat2
	- Example	`:g/tIO/s//Ada.Text_IO/g`
	- This will find and replace `tIO` by `Ada.text_IO` everywhere in the file.
- `:g/a/s// /g`	replace the letter `a`, by `blank`
- `:g/a/s///g`	replace `a` by `nothing`
		- note: Even this command be undone by `u`

 

Examples

Opening a New File

Step 1	type	vim filename	(create a file named filename)

Step 2	type	i	( switch to insert mode)

Step 3 enter text (enter your Ada program)

Step 4	hit	Esc key	(switch back to command mode)

Step 5	type	:wq	(write file and exit vim)

 

Editing the Existing File

Step 1	type	vim filename	(edit the existing file named filename)

Step 2	move around the file using h/j/k/l key or any appropriate command

h Moves the cursor one character to the left

l Moves the cursor one character to the right

k Moves the cursor up one line

j Moves the cursor down one line

nG or :n Cursor goes to the specified (n) line

(ex. 10G goes to line 10)

Step 3	edit required text (replace or delete or insert)

Step 4	hit Esc key (exit from insert mode if you insert or replace text)

Step 5	type	:wq
