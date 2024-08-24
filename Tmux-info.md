
# Tmux Cheat Sheet

## **Basics**

### Starting and Exiting Tmux
- **Start a new session**: 
  ```bash
  tmux
  ```
- **Start a new session with a name**:
  ```bash
  tmux new -s session_name
  ```
- **Detach from the session** (leave it running):
  ```bash
  Ctrl+b d
  ```
- **List all sessions**:
  ```bash
  tmux ls
  ```
- **Attach to a session**:
  ```bash
  tmux attach -t session_name
  ```
- **Kill a session**:
  ```bash
  tmux kill-session -t session_name
  ```

### Window Management
- **Create a new window**:
  ```bash
  Ctrl+b c
  ```
- **Switch between windows**:
  ```bash
  Ctrl+b (window number)
  ```
- **Rename a window**:
  ```bash
  Ctrl+b ,
  ```
- **Close the current window**:
  ```bash
  Ctrl+b &
  ```

### Pane Management
- **Split the window horizontally**:
  ```bash
  Ctrl+b %
  ```
- **Split the window vertically**:
  ```bash
  Ctrl+b "
  ```
- **Switch between panes**:
  ```bash
  Ctrl+b (arrow keys)
  ```
- **Resize a pane**:
  ```bash
  Ctrl+b (hold Ctrl and use arrow keys)
  ```
- **Close the current pane**:
  ```bash
  Ctrl+b x
  ```

## **Intermediate**

### Session Management
- **Rename a session**:
  ```bash
  tmux rename-session -t old_name new_name
  ```
- **Move a window to a different session**:
  ```bash
  tmux move-window -s source_session:window_number -t target_session
  ```

### Pane Synchronization
- **Synchronize input across all panes in a window**:
  ```bash
  Ctrl+b :
  setw synchronize-panes on
  ```
- **Turn off synchronization**:
  ```bash
  Ctrl+b :
  setw synchronize-panes off
  ```

### Scrolling
- **Enter copy mode (to scroll)**:
  ```bash
  Ctrl+b [
  ```
- **Scroll up/down**:
  ```bash
  Use arrow keys or PgUp/PgDn
  ```
- **Exit copy mode**:
  ```bash
  q
  ```

## **Advanced**

### Customization
- **Change the prefix key**:
  ```bash
  set-option -g prefix C-a
  unbind C-b
  bind C-a send-prefix
  ```
- **Change pane border colors**:
  ```bash
  set -g pane-border-style fg=blue
  set -g pane-active-border-style fg=green
  ```

### Scripting
- **Automate session creation**:
  ```bash
  tmux new-session -d -s my_session
  tmux rename-window -t my_session:0 'Main'
  tmux send-keys -t my_session:0 'htop' C-m
  tmux new-window -t my_session:1 -n 'Logs'
  tmux send-keys -t my_session:1 'tail -f /var/log/syslog' C-m
  tmux attach -t my_session
  ```

### Plugins and Extensions
- **Install Tmux Plugin Manager (TPM)**:
  ```bash
  git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
  ```
- **Add plugins to your `~/.tmux.conf`**:
  ```bash
  set -g @plugin 'tmux-plugins/tpm'
  set -g @plugin 'tmux-plugins/tmux-sensible'
  
  # Initialize TPM
  run '~/.tmux/plugins/tpm/tpm'
  ```
- **Install plugins**:
  ```bash
  Ctrl+b I
  ```

### Mouse Support
- **Enable mouse support**:
  ```bash
  set -g mouse on
  ```

### Cheat Sheet Summary
- **Start/Exit**: `tmux`, `Ctrl+b d`
- **Windows**: `Ctrl+b c` (new), `Ctrl+b ,` (rename), `Ctrl+b &` (close)
- **Panes**: `Ctrl+b %` (horizontal), `Ctrl+b "` (vertical), `Ctrl+b x` (close)
- **Session**: `tmux ls`, `tmux attach -t`, `tmux kill-session -t`
