# SixArm.com » Git » gitconfig for user, alias, color, branch, etc. 

Git configuration settings for our git users, command aliases, 
syntax coloring, branch management, and merge strategies.

## Required

Customize the gitconfig file sections for user:

    [user]
      email = sixarm@sixarm.com
      name = SixArm

Customize the gitconfig file section for GitHub, if you use it:

    [github]
      user = sixarm
      token = sixarm-token


## Recommended: branch auto setup merge

We tell git-branch and git-checkout to setup new branches so that git-pull
will appropriately merge from that remote branch. (If we didn't do this, we 
would have to add --track to our branch command or manually merge remote
tracking branches with "fetch" and then "merge".)

    git config --global branch.autosetupmerge true


## Suggested: tab completion

When we install Git, we can also install git tab completion settings.

To install git tab completion, we go to the git soure code directory then run:

    echo "source ./contrib/completion/git-completion.bash" >> /etc/bash.bashrc


## Git GUI apps

Read http://git.or.cz/gitwiki/InterfacesFrontendsAndTools

Our favorite open source free GUI for Ubuntu is http://cola.tuxfamily.org/

