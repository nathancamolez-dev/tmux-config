Logic to make the directory of the tmux the ~ (default one) for the session. 
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
In the directory ~/.local/scripts
You have to add the scripts that is on the directory scripts

Add on .bashrc 
```
PATH="$PATH":"$HOME/.local/scripts/"
bind '"\C-f":"tmux-sessionizer\n"'
```

Add on .zshrc (if you are using it)
```
bindkey -s ^f "tmux-sessionizer\n"
bindkey -s ^t "tmux-new-session\n"
```
