Title: Setting the Bash Prompt in Tmux
Date: May 15, 2019
Tags: ubuntu,tmux,vim,bash,prompt
Comments: This search came about from wanting to change the standard Bash prompt. I document how to do that here, but the changes didn't initially take, as I realised there are a number of configuration files the system uses, as well as a number of contexts of shell usage where they apply. This is my attempt at making sense of the topic. I roughly follow the research journey, with references for listed.




# Setting the Bash Prompt in Tmux

[1]: https://techantidote.com/tmux-not-displaying-bash-prompt-colors/
[2]: https://askubuntu.com/questions/125526/vim-in-tmux-display-wrong-colors
[3]: https://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell

## bash colours in tmux not working

Ref 1: [techantidote - tmux not displaying bash prompt colors][1] from the next link...
Ref 2: [Ask Ubuntu - Vim in tmux displays wrong colours][2]

These are interesting, but the setting suggested to ~/.tmux.conf had no effect.

```
vim ~/.tmux.conf
set -g default-terminal "screen-256color"
```

## Login and Interactive Shells

This reference details well the different types of shells, and what they read for configuration.

Ref 3: [Stack Exchange, Linux and Unix: Difference Between Login Shell and Non-Login Shell?][3]

> A login shell is the first process that executes under your user ID when you log in for an interactive session. The login process tells the shell to behave as a login shell with a convention: passing argument 0, which is normally the name of the shell executable, with a - character prepended (e.g. -bash whereas it would normally be bash). Login shells typically read a file that does things like setting environment variables: `/etc/profile` and `~/.profile` for the traditional Bourne shell,`~/.bash_profile` additionally for bash†, `/etc/zprofile` and `~/.zprofile` for zsh†, `/etc/csh.login` and `~/.login` for csh, etc.
> 
> † I'm simplifying a little, see the manual for the gory details.

> When you log in on a text console, or through SSH, or with su -, you get an interactive login shell. When you log in in graphical mode (on an X display manager), you don't get a login shell, instead you get a session manager or a window manager.



**My summary...**

A login shell occurs when you first login for an interactive session. It has name of `-bash` by default. It reads the following config files:

- `/etc/profile` (Bourne)
- `~/.profile` (Bourne)
- `~/.bash_profile (bash)`



**From the man pages...**

> **INVOCATION**
> 
> A login shell is one whose first character of argument zero is a -, or one started with the --login option.
>
> An interactive shell is one started without non-option arguments (unless -s is specified) and without the -c option whose standard input and error are both connected to terminals (as determined by isatty(3)), or one started with the -i option.  PS1 is set and $- includes i if bash is interactive, allowing a shell script or a startup file to test this state.
>
> The following paragraphs describe how bash executes its startup files.  If any of the files exist but cannot be read, bash reports an error.
>
> Tildes are expanded in filenames as described below under Tilde Expansion in the EXPANSION section.
>
>
> When bash is invoked as an interactive login shell, or as a non-interactive shell with the `--login` option, it first reads and executes commands from the file `/etc/profile`, if that file exists.  After reading that file, it looks for `~/.bash_profile`,  `~/.bash_login`,  and  `~/.profile`,  in  that  order,  and reads and executes commands from the first one that exists and is readable.  The `--noprofile` option may be used when the shell is started to inhibit this behavior.
>
> When an interactive login shell exits, or a non-interactive login shell executes the exit builtin command, bash reads and executes  commands from the file `~/.bash_logout`, if it exists.
>
> When  an  interactive  shell  that is not a login shell is started, bash reads and executes commands from `/etc/bash.bashrc` and `~/.bashrc`, if these files exist.  This may be inhibited by using the `--norc` option.  The `--rcfile` file option will force bash to read and execute commands from file instead of `/etc/bash.bashrc` and `~/.bashrc`.
>
> When  bash  is started non-interactively, to run a shell script, for example, it looks for the variable `BASH_ENV` in the environment, expands its value if it appears there, and uses the expanded value as the name of a file to read and execute.  Bash behaves as if the following command were executed:
>
```
if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
```
>
> but the value of the PATH variable is not used to search for the filename.

So the file-read order for an interactive login shell (such as when logging in with ssh) is:

1. `/etc/profile`
2. ... then the first it finds of:
	- `~/.bash_profile`
	- `~/.bash_login`
	- `~/.profile`

Now, I have `~/.bashrc` sourced in `~/.bash_profile	`, meaning it is also run to add some other capabilities, and the prompt is changed there. 

**file:** `~/bash_profile`

```
if [ -s ~/.bashrc ]; then
	source ~/.bashrc;
fi
```

Then `~/.bashrc` has `$force_color_prompt` set to `yes` (I uncommented this to turn on) which makes a following `if` statement true:

```
if [ "$color_prompt" = yes ]; then
	PS1='\[\033[32m\]\W $ \[\033[37m\]'
else
	PS1=`${debian_chroot:+($debian_chroot)} \u@\h:\w\$ '
fi

# The fourth line originally contained
	PS1='${debian_chroot:+($debian_chroot)} [\d \t] \u@\h:\w\$ '
# which was why it was showing [\d \t] in the prompt!
```

So I'm not sure for now if this is "good" but it seems to work. Bash runs the following files in this order for interactive login shells:

1. `/etc/.profile`
2. `~/.bash_profile`
3. `~/.bashrc`
