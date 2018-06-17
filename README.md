# Command Line Magic


## Commands List
* Change directory: `cd directory/path/from-your-current-directory` (use ../ to back up a level)
* Create a folder: `mkdir`
* Create a new file: `touch filename`
* Edit a file in Vim: `vim filename`
* Exit Vim: hit the escape key, then `:wq` and hit enter

## Create aliases for commonly used commands
It saves a ton of time. I don't love that you may end up forgetting what the actual command is, but the time it saves is huge, and it's pretty easy to keep a github file with your aliases and add them to a new machine.

1. Create an aliases file. Type `touch .aliases` in your terminal.
2. Open the file. You can use your editor of choice. To be wild and crazy and stick with the CLI, use `vim .aliases`. (Make sure you're in the directory that has your aliases file. Hit `i` for insert in order to add to or edit the file.)
3. Add whatever aliases you'd like. Here are my current github aliases:
  ```
  #Git
  alias gs='git status'
  alias ga='git add'
  alias gaa='git add .'
  alias gb='git branch'
  alias gbva='git branch -va'
  alias gc='git commit'
  alias gcm='git commit -m'
  alias gf='git fetch'
  alias gfp='git fetch -p'
  alias gp='git pull'
  alias gl='git log'
  alias gco='git checkout'
  ```
  `#Git` is just a commented line to keep things organized. If I type `gs` in my terminal, it runs `git status`.
  
  4. Save the file. (In Vim, hit escape, then `:wq`, hit enter)
  5. Open your bash profile. (`vim .bash_profile` - if you don't have a bash profile go ahead and make one)
  6. Add `source ~/.aliases`, save, and restart your CLI. Test out your aliases. It's magic!


## Edit what your CLI displays.
By default your text seems to always be one color, which makes it really hard to reference what you've done - your commands blend in with the output.

I can't explain exactly how this works, it's code I inherited from a friend, but it is a lifesaver. Add it to your .bash_profile and restart your CLI.

```
#command prompt customization
prompt() {
  local last_status=$?

  local WHITE="\[\033[1;37m\]"
  local GREEN="\[\033[0;32m\]"
  local CYAN="\[\033[0;36m\]"
  local GRAY="\[\033[0;37m\]"
  local BLUE="\[\033[0;34m\]"
  local LIGHT_BLUE="\[\033[1;34m\]"
  local YELLOW="\[\033[1;33m\]"
  local RED="\[\033[1;31m\]"
  local no_color='\[\033[0m\]'

  local time="${YELLOW}\d \@$no_color"
  local whoami="${GREEN}\u$no_color"
  local dir="${CYAN}\w$no_color"

  local branch
  if git rev-parse --git-dir >/dev/null 2>/dev/null ; then
    branch=$(git branch | awk '/^\*/ { print $2 }')
    branch="${branch:+$LIGHT_BLUE$branch }"
  else
    unset branch
  fi

  local driver
  if test -n "$M_DRIVER" ; then
    driver="$LIGHT_BLUE($M_DRIVER)"
  fi

  local last_fail
  if test $last_status -ne 0 ; then
    last_fail="=> ${YELLOW}Err: $last_status${no_color}\n"
  else
    unset last_fail
  fi

  PS1="\n$time $whoami $branch$dir\n$last_fail$driver$no_color \$ "
}
PROMPT_COMMAND=prompt
# retain $PROMPT_DIRTRIM directory components when the prompt is too long
PROMPT_DIRTRIM=3
```

### Disclaimer:
This is definitely not an area of expertise for me, let me know if you have feedback or suggestions!
