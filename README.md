# SixArm.com » Git » <br> gitconfig files

Git configuration for alias commands, branch management, syntax coloring, merge strategies, and more.


## Setup

Get these files:

    git clone https://github.com/SixArm/sixarm_git_gitconfig.git

Copy these files wherever you want to keep them, such as:

    mkdir ~/.gitconfig.d
    cp sixarm_git_gitconfig/gitconfig.d/* ~/.gitconfig.d/

Edit your `~/.gitconfig` file to include any of the files you want to use:

    [include]
       path = ~/.gitconfig.d/alias.txt
       path = ~/.gitconfig.d/alias-for-cvs.txt
       path = ~/.gitconfig.d/alias-for-gitk.txt
       path = ~/.gitconfig.d/alias-for-rails.txt
       path = ~/.gitconfig.d/alias-for-svn.txt
       path = ~/.gitconfig.d/apply.txt
       path = ~/.gitconfig.d/branch.txt
       path = ~/.gitconfig.d/color.txt
       path = ~/.gitconfig.d/core.txt
       path = ~/.gitconfig.d/diff.txt
       path = ~/.gitconfig.d/github.txt
       path = ~/.gitconfig.d/merge.txt
       path = ~/.gitconfig.d/mergetool.txt
       path = ~/.gitconfig.d/push.txt
       path = ~/.gitconfig.d/rerere.txt
       path = ~/.gitconfig.d/user.txt

You can override any of items by adding your own item later in the file.

For example, to use our git log aliases and also override "git l" with your own definition:

    [include]
       path = ~/.gitconfig.d/alias.txt

    [alias]
       l = log --graph --oneline


## Meld

To use the mergetool `meld-with-three-windows`, put the script on your path, for example:

    cp bin/meld-with-three-windows /usr/local/bin


## Personalization

You can override any of these settings by using your own gitconfig file.

Customize the gitconfig file sections for user:

    [user]
      email = alice@example.com
      name = Alice Anderson

Do you use GitHub? If so, you can customize the github section for your user id and token:

    [github]
      user = alice
      token = alice-token

Do you prefer terse status messages?

    [alias]
      s = status -sb

Do you prefer log message summaries?

    [alias]
      l = log --graph --oneline

Do you prefer using `most` as a pager? (Get it by doing `brew install most` or `apt-get install most` etc.)

    [core]
      pager = most

To use better pretty formatting:

    [format]
      pretty = "%H %ci %ce %ae %d %s"


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


## More

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

## Thanks

  * [Joel Parker Henderson](https://github.com/joelparkerhenderson)
  * [Bill Lazar](https://github.com/billsaysthis)
  * [Joe Nelson](https://github.com/begriffs)
  * [Scott Lindsay](http://stackoverflow.com/users/167384/scott-lindsay)
  * [baudtack](http://baudtack.com)
  * [Ruben Verborgh](http://ruben.verborgh.org)
  * [Rob Kennedy](http://cs.wisc.edu/~rkennedy)
  * [Corey Haines](http://coreyhaines.com/)
  * [Mislav Marohnić](http://mislav.uniqpath.com/)
  * [Gary Bernhardt](http://destroyallsoftware.com)
