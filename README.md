# SixArm.com » Git » gitconfig for user, alias, color, branch, etc. 

Git configuration settings for our git users, command aliases, 
syntax coloring, branch management, and merge strategies.


## Setup

Get these files:

    git clone https://github.com/SixArm/sixarm_git_gitconfig.git

To include all these files, add this to the top of your <code>~/.gitconfig</code>

    [include]
       path = sixarm_git_gitconfig/gitconfig-alias.txt
       path = sixarm_git_gitconfig/gitconfig-alias-for-cvs.txt
       path = sixarm_git_gitconfig/gitconfig-alias-for-gitk.txt
       path = sixarm_git_gitconfig/gitconfig-alias-for-rails.txt
       path = sixarm_git_gitconfig/gitconfig-alias-for-svn.txt
       path = sixarm_git_gitconfig/gitconfig-basics.txt
       path = sixarm_git_gitconfig/gitconfig-color.txt
       path = sixarm_git_gitconfig/gitconfig-github.txt
       path = sixarm_git_gitconfig/gitconfig-user.txt

This repo configures git to use the `most` pager rather than `less` or
`more`. You can install `most` like this:

    # Homebrew, in OS X
    brew install most

    # Ubuntu
    sudo aptitude install most

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


## Pager

Change the pager from `less` to `most`:

    [core]
      pager = most


## Suggestion for expert users

Show terse output for git status:

    [alias]
      s = status -sb



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


## Contributors

  * [Joel Parker Henderson](https://github.com/joelparkerhenderson)    
    
  * [Bill Lazar](https://github.com/billsaysthis)

  * [Joe Nelson](https://github.com/begriffs)

  * Many more from the links below


## For More

For more git config ideas, and for credit for many of the aliases here, please see these excelent resources:
 
  * <https://git.wiki.kernel.org/index.php/Aliases>
  * <http://stackoverflow.com/questions/267761/what-does-your-gitconfig-contain>
  * <http://superuser.com/questions/169695/what-are-your-favorite-git-aliases>
  * <http://stackoverflow.com/questions/1309430/how-to-embed-bash-script-directly-inside-a-git-alias>
  * <http://code.joejag.com/2013/everyday-git-aliases/>
  * <http://blog.apiaxle.com/post/handy-git-tips-to-stop-you-getting-fired/>
  * <https://ochronus.com/git-tips-from-the-trenches/>
  * <http://mislav.uniqpath.com/2010/07/git-tips/>
  * <https://ochronus.com/git-tips-from-the-trenches/>
  * <http://mislav.uniqpath.com/2010/07/git-tips/>

Thanks also to StackOverflow help:

  * [Scott Lindsay](http://stackoverflow.com/users/167384/scott-lindsay)
  * [baudtack](http://baudtack.com)
  * [Ruben Verborgh](http://ruben.verborgh.org)
  * [Rob Kennedy](http://cs.wisc.edu/~rkennedy)

