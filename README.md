dubstep logic 
```
if [ -n "$TMUX" ]; then
    export TMUX_DIR=$(tmux display-message -p '#{pane_current_path}')

    unfunction cd 2>/dev/null

    cd() {
        if [ -n "$1" ]; then
            builtin cd "$@"
        else
            builtin cd "$TMUX_DIR"
        fi
    }
fi
```
