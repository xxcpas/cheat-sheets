# tmux user guide

## Installation

`brew install tmux`

Install the plugin manager: https://github.com/tmux-plugins/tpm

## Customization

Edit the file `~/.tmux.conf`

## Commands

`C` = Ctrl key
`M` = Alt/Option key

### Sessions

`tmux` to start a session
`tmux new -s <session name>` to start a session with the given name

`C-a $` to rename the current session
`C-a s` to display the active sessions, `q` or `Esc` to exit this view

`C-a d` to detach from the current session
`C-a D` to detach from a session to choose

`tmux ls` to list running sessions
`tmux attach -t 0` to attach to session `0`
`tmux rename-session -t 0 <session name>` to rename session `0` to the given session name
`tmux kill-session -t 0` to kill session `0`

`C-a C-s` to save the session (plugin *resurect*)
`C-a C-r` to restor the session (plugin *resurect*)

### Windows

`C-a c` to create a new window (in the current session)
`C-a ,` to rename the current window
`C-a p` to go the previous window
`C-a n` to go the next window
`C-a <number>` to go the corresponding window
`C-a &` to close the current window

### Panes

`C-a |` to split vertically
`C-a -` to split horizontally
`C-a <arrow key>` to switch to a different pane
`C-a z` to make the current pane go full screen, and again to shrink it back
`C-a x` to kill the current pane (with confirmation)
`exit` or `C-d` to exit (without confirmation)

### Others

`C-a :` to enter a *tmux* command
* `new` to create a new session

`C-a ?` to show a list of commands

`C-a r` to reload the tmux conf

`M <mouse select>` to select and copy the text into the clipboard
