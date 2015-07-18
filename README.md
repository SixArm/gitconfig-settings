# Git » gitconfig files

Git configuration files.

This has git aliases, branches, merges, syntax coloring, merges, credentials, and more.

For the complete list of aliases, and all the configurations, please see the files in the `gitconfig.d` directory.

There are two files that are specific to the operating system; use the one that's right for your system.

  * specific-to-osx
  * specific-to-windows

## Install

Clone:

    git clone https://github.com/SixArm/sixarm_git_gitconfig.git

If you already have a `.gitconfig` file and you want to include all these files, then add this to your `.gitconfig` file:

    [include]
       path = sixarm_git_gitconfig/gitconfg

If you prefer to customize which files to include, you can choose specific files, for example:

    [include]
       path = sixarm_git_gitconfig/gitconfig.d/alias-for-feature-flow.txt
       path = sixarm_git_gitconfig/gitconfig.d/specific-to-osx.txt

If you prefer to have full control of these files, you can copy them wherever you like on your system, and edit them as you like. 


## Alias shortcuts

One-letter shortcuts speed up typing:

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

One-letter shortcuts often have shortcuts for popular options:

    git ap = add --patch
    git ci = commit --interactive
    git ds = diff --staged
    git lg = log --graph


## Alias commands

Here are some of our favorites. For more, see `gitconfig.d/alias*`.

Get all updates to our project:

    git get = !git pull --rebase && git submodule update --init --recursive

Rebase interactive on our unpushed commits:

    git rbi = !git rebase -i @{u}

Summarize your own changes since yesterday, suitable for a daily standup meeting:

    log-standup = !git log --since yesterday --pretty=short --author `git config user.email`

Find any text in any commit ever:

    git grep-all = !"git rev-list --all | xargs git grep '$1'"


## Feature flow aliases

Here are aliases suitable for a simple feature flow. For details, see `gitconfig.d/alias-for-feature-flow.txt`.

Create a new feature branch:

    git feature-start = '!branch=$1; git checkout master; git pull; git checkout -b "$branch" master'

Update the feature branch:

    git feature-update = '!branch=$(git branch-name); git checkout master; git pull; git checkout "$branch"; git rebase master'

Share the feature branch:

    git feature-share = '!branch=$(git branch-name); git push -u origin "$branch"'


## Publishing aliases

Here are a couple our favorites; for the complete list, see `gitconfig.d`.

Publish the current branch by pushing and tracking:

    git publish = "!git push -u origin $(git branch-name)"

Unpublish the current branch by deleting the remote branch:

    git unpublish = "!git push origin :$(git branch-name)"



## Cleaning aliases

Here are some of our favorites; for the complete list, see `gitconfig.d`.

Delete all branches that have been merged into master:

    git master-cleanse = !"git checkout master && git branch --merged | xargs git branch -d; git branch -r --merged origin/master | sed 's/ *origin\///' | grep -v '^master$' | xargs -I% git push origin :% 2>&1 | grep --colour=never 'deleted'"


Prune stale items:

    git pruner = !git prune --expire=now; git reflog expire --expire-unreachable=now --rewrite --all

Repack the way Linus recommends:

    git repacker = !git repack -a -d -f --depth=300 --window=300 --window-memory=1g



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
