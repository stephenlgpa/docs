# Splitting Windows in VIM

Use the following in COMMAND MODE.


| Command  |  Notes |
| :------  | :----- |
| **`:split`** | Open current file in new split window pane (split horizontally)
| **`ctrl-w ctrl-w (or ctrl-w w)`** | Rotates through panes, top to bottom
| **`ctrl-w h/j/k/l`** | Moves to the corresponding window (left, down, up, right)
| **`:close`** | Closes current window
| **`:only`** | Closes all windows but the current (error if there are unsaved changes in any file)
| **`:quit`** | Closes current window (quits Vim on last window)
| **`:split <filename>`** | Split a window on another file
| **`:new`** | Split a window on new empty file
| **`:nnew`** | Split a window of 'n' lines on new empty file
| **`:nsplit`** | Split a window of n line height
| **`ctrl-w +/-/=`** | Increase/decrease/equalise window height(s)/width(s)
| **`n ctrl-w _`** | Set the window to height/width n (no `:`)
| **`ctrl-w _`** | Set window to maximum height
| **`ctrl-w r`** | Rotate window downwards
| **`ctrl-w R`** | Rotate window upwards
| **`ctrl-w x`** | Exchange current window with next one
| **Vertical Splits** |
| **`:vertical`** | Can be inserted before other commands to work vertically.
| **`:vsplit`** | View of current file in new vertical split to right (all other commands are the same)
| **`:vnew`** | Split a window vertically on a new file
