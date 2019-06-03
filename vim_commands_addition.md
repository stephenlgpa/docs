# Vim again

Ref: [Vim 101: A Beginner's Guide to Vim][1]

This is what I have heard.

Vim is modal. Say that again. **Modal**. The Insert Mode is for writing text, and Command Mode is for editing it and moving around.

> "Just to hammer this home: If you stay in insert mode for long, you're doing something wrong. The pattern in Vi(m) is: Move around in normal mode. Make short inserts (a word here, a sentence there). Or manipulate the text with Ex commands like :substitute. Repeat.
> Try to teach yourself to leave insert mode (via <Esc>, hopefully conveniently accessible on your keyboard) as soon as the stream of characters coming from your brain starts to trickle off. The next insertion is just an `i`/`a` away. 

## Moving through a document in Vim

- h 	moves the cursor one character to the left.
- j 	moves the cursor down one line.
- k 	moves the cursor up one line.
- l 	moves the cursor one character to the right.
- 0 	moves the cursor to the beginning of the line.
- $ 	moves the cursor to the end of the line.
- w 	move forward one word.
- b 	move backward one word.
- G 	move to the end of the file.
- gg 	move to the beginning of the file.
- \`. 	move to the last edit.

Prefacing the command with a number will execute the number that many times. E.g. `10w` moves the cursor ahead 10 words.

## Editing in Vim

- d	starts the delete operation.
- dw	will delete a word.
- d0	will delete to the beginning of a line.
- d$	will delete to the end of a line.
- dgg	will delete to the beginning of the file.
- dG	will delete to the end of the file.
- u	undo the last operation.
- Ctrl-r	redo the last undo.

# Search and Replace Text

In Command Mode: 

/text	search for next occurrence of "text"
/n	search for next occurrence of "text"
/N	search for previous occurrence of "text"
?text	search for previous occurrence of "text"
:%s/text/replacementText/g	search and replace text
:%s/text/replacementText/gc	search and replace text with confirmation

## Copying and Pasting Text

v	highlight one character at a time.
V	highlight one line at a time.
Ctrl-v	highlight by columns.
p	paste text after the current line.
P	paste text on the current line.
y	yank text into the copy buffer.
yy	yank current line into the copy buffer.













[1]:[https://www.linux.com/learn/vim-101-beginners-guide-vim]
