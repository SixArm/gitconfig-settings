# Git » gitconfig files

Git configuration for aliases, branches, merges, syntax coloring, merges, and more.

## Alias nicknames:

One-letter nicknames to speed up typing:

    git a = add
    git b = branch
    git c = commit
    git d = diff
    git f = fetch
    git g = grep
    git l = log
    git m = merge
    git o = checkout
    git p = pull
    git r = remote
    git s = status
    git w = whatchanged

A few of our favorite nicknames with options:

    git ap = add --patch
    git ci = commit --interactive
    git ds = diff --staged
    git lg = log --graph


## Alias commands

A few of our favorite commands:

Get all updates to our project:

    git get = !git pull --rebase && git submodule update --init --recursive

Rebase interactive on our unpushed commits:

    git rbi = !git rebase -i @{u}

Summarize your own changes since yesterday, suitable for a daily standup meeting:

    log-standup = !git log --since yesterday --pretty=short --author `git config user.email`

Find text in any commit ever:

    git grep-all = !"git rev-list --all | xargs git grep '$1'"




## Workflow aliases

Publish the current branch by pushing and tracking:

    git publish = "!git push -u origin $(git branch-name)"

Unpublish the current branch by deleting the remote branch:

    git unpublish = "!git push origin :$(git branch-name)"



## Optimization aliases

Delete all local branches that have already been merged into the local master:

    git master-cleanse-local = !"git checkout master && git branch --merged | xargs git branch -d"

Delete all remote branches that have already been merged into the remote master:

    git master-cleanse-remote = !"git branch -r --merged origin/master |
      sed 's/ *origin\///' | grep -v '^master$' |
      xargs -I% git push origin :% 2>&1 |
      grep --colour=never 'deleted'"

Clean everything that is unreachable:

    git pruner = !git prune --expire=now; git reflog expire --expire-unreachable=now --rewrite --all

Repack the way Linus recommends:

    git repacker = !git repack -a -d -f --depth=300 --window=300 --window-memory=1g


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


## User personalization

If you use the `user.txt` file, you will want to personalize it:

    [user]
      email = alice@example.com
      name = Alice Anderson


## GitHub personalization

If you use GitHub and the `github.txt` file, you will want to personalize it:

    [github]
      user = alice
      token = alice-token


## Customization

You can customize any of the file items by editing the file as you like.

You can also customize any of the file items by adding your own item later in your own gitconfig file.

For example you can include our aliases then customize "git l" with your own definition:

    [include]
       path = ~/.gitconfig.d/alias.txt

    [alias]
       l = log --graph --oneline


## Format

To use better pretty formatting:

    [format]
      pretty = "%H %ci %ce %ae %d %s"


## Status

If you like terse status messages:

    [alias]
      s = status -sb

## Log

If you like log summaries:

    [alias]
      l = log --graph --oneline


## Meld merge tool

We like using the `meld` mergetool because it is powerful and can use three windows for comparisons.

This repo includes a script for running `meld` with three windows.

To use meld with three windows, put the script on your path, for example:

    cp bin/meld-with-three-windows /usr/local/bin


## Most pager

If you prefer using `most` as a pager:

    [core]
      pager = most

To get `most`, do `brew install most` on OSX, or `apt-get install most` on Ubuntu, etc.


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
  * [Joe Nelson](http://begriffs.com)
  * [Rob Miller](https://github.com/robmiller)
