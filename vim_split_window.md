# Splitting Windows in VIM

Use the following in COMMAND MODE.


|   Command   |   Notes   |
|   -------   |   -----   |
| **:split** | Open current file in new split window pane (split horizontally)
| **ctrl-w ctrl-w (or ctrl-w w)** | rotates through panes, top to bottom
| **ctrl-h/j/k/l** | Moves to the corresponding window (left, down, up, right)
| **:close** | Closes current window
| **:quit** | Closes current window (quits Vim on last window)
| **:split \<filename\>** | Split a window on another file
| **:new** | Split a window on new empty file
| **:nsplit** | Split a window of n line height
| **ctrl-w +/-** | Increase or decrease the size of a window split
| **n ctrl-w** _ | Set the window to height n
| **Vertical Splits** |
| **:vsplit** | View of current file in new vertical split to right (all other commands are the same)
