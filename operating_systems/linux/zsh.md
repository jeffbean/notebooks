# Moving to zsh from bash

## Why?

After looking at some examples and arguments for one to the other I saw some features that personally want are plugins for things like Docker, Django and GIT.

With seeing the power of these plugins and options around history sharing between sessions are big for me. I have bash settings to try and mimic the history sharing but it is not always perfect.

# Installing.

After a short search on where to start the [oh-my-zsh](http://ohmyz.sh/) project looked like the first place to start.

So easy:

    curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh


# My plugins

I didnt go too crazy here and stuck with some simple plugins for now.

    plugins=(git django python docker)


## Adding history

    # History
    # ~~~~~~~

    HISTSIZE=1000
    SAVEHIST=1000
    HISTFILE=$HOME/.zsh_history

    setopt SHARE_HISTORY        # Share history across sessions
    setopt HIST_IGNORE_SPACE    # commands starting w/ a space don't go into history

    # SHARE_HISTORY seems to imply both of these, at least that's how the manpage
    #   reads, so let's comment them out for now.
    #
    # setopt INC_APPEND_HISTORY   # Incrementally append history to file
    # setopt EXTENDED_HISTORY     # Save the timestamp and duration of commands to history file
