# screen Command Cheat Sheet  
| Command     |    Description    |
|:------------|:------------------|
| screen -S <session_name> | Start a new session with session name |
| screen -ls | List running sessions / screens |
| screen -x | Attach to a running session |
| screen -r <session_name> | Attach to a running session with name |
| screen -d <session_name> | Detach a running session |
| Ctrl-a c | Create new window |
| Ctrl-a | Change to last-visited active window |
| Ctrl-a <number> | Change to window by number |
| Ctrl-a " | See window list |
| Ctrl-a ' <number or title> | Change to window by number or name |
| Ctrl-a n or Ctrl-a <space> | Change to next window in list |
| Ctrl-a p or Ctrl-a <backspace> | Change to previous window in list |
| Ctrl-a w | Show window bar |
| Ctrl-a A | Rename current window |
| Ctrl-a x | Lock (password protect) display |  
| Ctrl-a k | Kill current window |
| Ctrl-a \ | Kill all windows |
| Ctrl-a S | Split display horizontally |
| Ctrl-a | or Ctrl-a V | Split display vertically |
| Ctrl-a tab | Jump to next display region |
| Ctrl-a X | Remove current region |
| Ctrl-a Q | Remove all regions but the current one |
| Ctrl-a H | Enable logging in the screen session |
| Ctrl-a M | Monitor a window for output (a notification pops up when that window has activity). |
| Ctrl-a _ | Watch a window for absence of output (such as when a process finishes) |  

Started with the list at: https://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/  
Some content also from: https://phoenixnap.com/kb/how-to-use-linux-screen-with-commands, https://devhints.io/screen  


# tmux Command Cheat Sheet  
| Command     |    Description    |
|:------------|:------------------|
| $tmux | Create new session with default session name |
| $tmux new | Create new session with default session name |
| $tmux new-session | Create new session with default session name |
| $tmux new -s session_name | Creates a new session called "session_name" |
| Ctrl+b : | Enters command mode |
| Ctrl+b :new -s session_name | Creates new session within an existing session |
| $tmux ls | List active tmux sessions |
| $tmux list-sessions | List active tmux sessions |
| Ctrl+b s | List active tmux sessions |
| $tmux a -t session_name | Attaches to session by the name "session_name" |
| $tmux at -t session_name | Attaches to session by the name "session_name" |
| $tmux attach -t session_name | Attaches to session by the name "session_name" |
| $tmux attach-session -t session_name | Attaches to session by the name "session_name" |
| $tmux kill-ses -t session_name | Kills session by the name "session_name" |
| $tmux kill-session -t session_name | Kills session by the name "session_name" |
| Ctrl+b d | Detaches from the session, leaving the session running in the background |
| Ctrl+b $ | Rename the session name |
| Ctrl+b ( | Move to the previous session |
| Ctrl+b ) | Move to the next session |

Started with the list at: https://www.golinuxcloud.com/tmux-cheatsheet/  
How-To page at: https://github.com/tmux/tmux/wiki  
