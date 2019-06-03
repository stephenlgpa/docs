# TMUX COMMANDS

Author: Stephen Grabner
Topic: Basic commands to use with tmux
Date: 2019-04-19

----

This information is from the tmux man page. Use the following commands by first entering `ctrl-a`.


## Panes

- `%`		Open new vertical pane to right of current
- `"`		Open new horizontal pane to bottom of current
- `!`		Break the pane out of the window
- `o`		Move to next pane
- `->`	Move to pane on right (arrow right)
- `<-`	Move to pane of left (arrow left)
- `up`	Move to pane above (arrow up)
- `down`	Move to pane below (arrow down)
- `x`		Kills the current pane
- `q`		Display pane indices briefly
- `{`		Swaps current pane with previous one
- `}`		Swaps current pane with next one


## Pane Layouts

In tmux, 'M-' is the meta key, bound to the option/alt key.

- `M-1 to 5`	Display window in default layout 1-5
- `space`	Display window panes in next default layout
- `C-arrow keys`	Resize pane 1 cell in that direction
- `M-arrow keys`	Resize pane 5 cells in that direction

## Windows

- `c`		Create a new window
- `,`		Rename window
-  `n`		Next window
- `p`		Previous window
- `0-9`	Choose that window number
- `#`		Kills the current window (exits tmux if last window)

