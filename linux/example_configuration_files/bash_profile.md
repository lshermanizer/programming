# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/.local/bin:$HOME/bin

export PATH

# show path and a dollar sign

PS1='\W\$ '

# aliases

alias ll='ls -lrt --color=always'
alias ls='ls      --color=always'
alias dul='du -sh * | sort -h'
ev() {
  emacs "$1" --eval '(setq buffer-read-only t)'
}
