## Display the current branch and folder path in terminal

macOS Catalina or above (10.15+ incl. Big Sur 11.0) which has deprecated bash in favour of zsh, here is my .zshrc file:

(create a .zshrc file in the home directory: /Users/gbruins/.zshrc)
```
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}
COLOR_DEF='%f'
COLOR_USR='%F{243}'
COLOR_DIR='%F{197}'
COLOR_GIT='%F{39}'
NEWLINE=$'\n'
setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n@%M ${COLOR_DIR}%d ${COLOR_GIT}$(parse_git_branch)${COLOR_DEF}${NEWLINE}%% '
```