# SixArm.com » Git » gitconfig for user, alias, color, branch, etc. 

Git configuration settings for our git users, command aliases, 
syntax coloring, branch management, and merge strategies.


## Setup

Get these files:

    git clone ...

To include all these files, add this to the top of your <code>~/.gitconfig</code>

    [include]
       path = sixarm_git_gitconfig/gitconfig-aliases.txt
       path = sixarm_git_gitconfig/gitconfig-basics.txt
       path = sixarm_git_gitconfig/gitconfig-color.txt
       path = sixarm_git_gitconfig/gitconfig-github.txt
       path = sixarm_git_gitconfig/gitconfig-user.txt


## Personalization

Customize the gitconfig file sections for user:

    [user]
      email = sixarm@sixarm.com
      name = SixArm


## GitHub

Do you use GitHub? If so, you can customize the github section for your user id and token:

    [github]
      user = sixarm
      token = sixarm-token


## Suggestion for branch auto setup merge

We tell git-branch and git-checkout to setup new branches so that git-pull
will appropriately merge from that remote branch. 

    git config --global branch.autosetupmerge true

If we didn't do this, we would have to add --track to our branch command or manually merge remote tracking branches with "fetch" and then "merge".


## Suggestion for tab completion

To install git tab completion, we go to the git soure code directory then run:

    echo "source ./contrib/completion/git-completion.bash" >> /etc/bash.bashrc


## Suggestion for git GUI apps

Read http://git.or.cz/gitwiki/InterfacesFrontendsAndTools

Our favorite open source free GUI for Ubuntu is http://cola.tuxfamily.org/

