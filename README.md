# Command Line Magic

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


## Commands List
Change directory: `cd directory/path/from-your-current-directory` (use ../ to back up a level)
Create a folder: `mkdir`
Create a new file: `touch filename`
Edit a file in Vim: `vim filename1`
Exit Vim: hit the escape key, then `:wq` and hit enter

### Disclaimer:
This is definitely not an area of expertise for me, let me know if you have feedback or suggestions!
