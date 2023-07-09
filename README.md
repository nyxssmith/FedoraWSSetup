# FedoraWSSetup
My personal setup of packages to install once setting up a new install of fedora WS

Most of my setup is dotfiles that live in my home folder, or flatpak apps. I just mount my home folder drive at `/home` to restore configs

# Package Installs

### Docker
```bash
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo usermod -aG docker nyx

sudo systemctl enable --now docker

```


### Shell Utilities

Packages used by shell extensions

```bash
sudo dnf install xprop fzf hstr

```
# Config Files


# .zshrc
```bash
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi


# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
# source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme

# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="/home/nyx/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
#ZSH_THEME="robbyrussell"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to automatically update without prompting.
# DISABLE_UPDATE_PROMPT="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# Caution: this setting can cause issues with multiline prompts (zsh 5.7.1 and newer seem to work)
# See https://github.com/ohmyzsh/ohmyzsh/issues/5765
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.

source $HOME/.oh-my-zsh/custom/plugins/calc.plugin.zsh/calc.plugin.zsh
source $HOME/.oh-my-zsh/custom/plugins/zsh-bash-completions-fallback/zsh-bash-completions-fallback.plugin.zsh
#source $HOME/.oh-my-zsh/custom/plugins/zsh-plugin-vscode/vscode.plugin.zsh

plugins=(git colored-man-pages python safe-paste sudo web-search zsh-interactive-cd ssh-agent aws docker)


source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"



#ZSH_THEME="agnosterzak"

#ZSH_THEME=""

# theme overrides
export TYPEWRITTEN_SYMBOL=">"
export TYPEWRITTEN_RELATIVE_PATH="adaptive"
export TYPEWRITTEN_CURSOR="terminal"


#export TYPEWRITTEN_COLOR_MAPPINGS="current_directory:red"


export TYPEWRITTEN_COLORS="arrow:cyan;symbol:blue;current_directory:red"



# typrwriten themse
#fpath+=$HOME/.zsh/typewritten
#autoload -U promptinit; promptinit
#prompt typewritten

# aliases

alias gp='git push && python3 /home/nyx/Git/actionsStatusCLI/actionsStatus.py'
alias gs='git status'
alias ghostscript='/usr/bin/gs'

alias awss='/home/nyx/Git/DevSetup/scripts/aws'

complete -C /usr/bin/terraform terraform

alias fix-flatpak-theme='/home/nyx/Git/gnome-ftu/gftu.py'

# HSTR configuration - add this to ~/.zshrc
alias hh=hstr                    # hh to be alias for hstr
setopt histignorespace           # skip cmds w/ leading space from history
export HSTR_CONFIG=hicolor       # get more colors
bindkey -s "\C-r" "\C-a hstr -- \C-j"     # bind hstr to Ctrl-r (for Vi mode check doc)

export HISTFILE=~/.zsh_history
export HSTR_PROMPT=">"

export HISTFILESIZE=100000
export HISTSIZE=${HISTFILESIZE}

bindkey -s "\C-r" "\C-a hstr -- \C-j"


zstyle :omz:plugins:ssh-agent agent-forwarding on




source ~/powerlevel10k/powerlevel10k.zsh-theme
# source ~/powerlevel10k/powerlevel10k.zsh-theme

```


# .bashrc
```bash
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac


# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTFILESIZE=100000
HISTSIZE=${HISTFILESIZE}
#HISTSIZE=1000
#HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi


# prompt functions



shorten_prompt () {

python3 << END

location_string = "$1"
folders = location_string.split("/")
folders.pop(0)
starting_letters = []
i = 0
for folder in folders:
    if(i == len(folders)-1):
        starting_letters.append(folder)
        break
    starting_letters.append(folder[0])
    i +=1

output = "/".join(starting_letters)
if "h/nyx" not in output:
    output = output.replace("h/n","~")
else:
    output = "~"
print(output)

END

}

do_git_status (){



#echo "is this git"

GS=$(git status > /dev/null 2>&1)
code=$?

#echo $code

if [ "$code" -eq "0" ]; then


branch=$(git status | grep -w "Your branch" | cut -d ' ' -f 8 | tr -d . | tr -d "'" | cut -d '/' -f 2 ) 

#echo $branch

UPSTREAM=${1:-'@{u}'}
LOCAL=$(git rev-parse @)
REMOTE=$(git rev-parse "$UPSTREAM")
BASE=$(git merge-base @ "$UPSTREAM")


status=""

if [ $LOCAL = $REMOTE ]; then
    #status=":Up-to-date"
    status=""
elif [ $LOCAL = $BASE ]; then
    status=":Need to pull"
elif [ $REMOTE = $BASE ]; then
    status=":Need to push"
else
    status=":Diverged"
fi

echo $branch$status
rm 1 >/dev/null 2>&1
   
   exit;
else
   #echo $(whoami);
   echo"";
   exit;
fi


}



if [ "$color_prompt" = yes ]; then
    #PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\]:  \[\033[01;34m\] \w \[\033[00m\]   \[\033[01;34m\]$(echo "aaa")\[\033[00m\]   \$ '

    #PS1='${debian_chroot:+($debian_chroot)}\[\033[01;34m\]\w \[\033[00m\]   \[\033[01;34m\]$(echo "aaa")\[\033[00m\]   \$ '

    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\]:\[\033[01;99m\]$(do_git_status)\[\033[00m\]:\[\033[01;34m\]$(shorten_prompt \w)\[\033[00m\]\$ '



    #PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u\[\033[00m\]:  \[\033[01;34m\] \w \[\033[00m\]   \$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

PATH=/home/nyx/Scripts/bin:$PATH

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

alias lsfl='cat /home/nyx/Documents/SFL_Links'
alias s='sudo'
alias gca='git commit -a'
alias gu='git reset HEAD~'
alias akp='aws-vault exec klaviyo-prod --'
alias tunnel_jenkins='ssh -Nf -L 8081:localhost:8080 jenkins-eng-1 -i /home/nyx/.ssh/dev_shared_key'
alias gs='git status'
alias gls="git log --all --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"


function jsonformat() {
   python -mjson.tool $1 > /tmp/pp.json || echo "Input not valid JSON" && return
   cat /tmp/pp.json > $1
   echo "Formatted $1"
}

export -f jsonformat




export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# HSTR configuration - add this to ~/.bashrc
alias hh=hstr                    # hh to be alias for hstr
export HSTR_CONFIG=hicolor       # get more colors
shopt -s histappend              # append new history items to .bash_history
export HISTCONTROL=ignorespace   # leading space hides commands from history
export HISTFILESIZE=10000        # increase history file size (default is 500)
export HISTSIZE=${HISTFILESIZE}  # increase history size (default is 500)
# ensure synchronization between bash memory and history file
export PROMPT_COMMAND="history -a; history -n; ${PROMPT_COMMAND}"
# if this is interactive shell, then bind hstr to Ctrl-r (for Vi mode check doc)
if [[ $- =~ .*i.* ]]; then bind '"\C-r": "\C-a hstr -- \C-j"'; fi
# if this is interactive shell, then bind 'kill last command' to Ctrl-x k
if [[ $- =~ .*i.* ]]; then bind '"\C-xk": "\C-a hstr -k \C-j"'; fi

function gitActionsStatus() {
  python3 /home/nyx/Git/actionsStatusCLI/actionsStatus.py
}
export -f gitActionsStatus

alias gp='git push && gitActionsStatus'

alias awss='/home/nyx/Git/DevSetup/scripts/aws'

alias fixvpnroute='sudo ip route add 10.10.20.0/24 dev ppp0'

complete -C /usr/bin/terraform terraform


# image enhancer
alias img_enhance='function ne() { docker run --rm -v "$(pwd)/`dirname ${@:$#}`":/ne/input -it alexjc/neural-enhance ${@:1:$#-1} "input/`basename ${@:$#}`"; }; ne'

alias ssh_jetson='ssh user@192.168.55.1 -XY'


export PATH="$PATH:/opt/mssql-tools/bin"
source <(kubectl completion bash)

#source /opt/deepops/env/bin/activate
source /opt/deepops/env/bin/activate
export IFX_TOOLBOX_UUID=b0c2783d-64ac-3bc8-a6d4-0387950a8069
```



# fstab
```bash


#
# /etc/fstab
# Created by anaconda on Sun Jul  9 18:59:28 2023
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
UUID=7ebe6d8f-9d15-45d1-9e0d-ee36f0927377 /                       btrfs   subvol=root,compress=zstd:1 0 0
UUID=8edd7328-06a0-4e67-81c4-a4a80c5cd68b /boot                   ext4    defaults        1 2
UUID=B81D-C221          /boot/efi               vfat    umask=0077,shortname=winnt 0 2
#UUID=7ebe6d8f-9d15-45d1-9e0d-ee36f0927377 /home                   btrfs   subvol=home,compress=zstd:1 0 0
UUID=7c6fb95c-60e0-4e0d-9402-b60ba23ba7f1 /home ext4 defaults 0 0


```