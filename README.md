# Git » gitconfig files

Git configuration files.

This has git aliases, branches, merges, syntax coloring, merges, credentials, and more.

For the complete list of aliases, and all the configurations, please see the files in the `gitconfig.d` directory.


## Install

Install for novices:

  1. Get these files:

        git clone https://github.com/SixArm/sixarm_git_gitconfig.git

  2. Create a `.gitconfig` file, or edit you existing file, such as:

        edit ~/.gitconfig

  3. Add these lines:

        [include]
           path = sixarm_git_gitconfig/gitconfg

Install for experts:

  1. If you want full control, then you can copy any of these files, as edit them as you like.

  2. The `alias.txt` file has the bulk of the items - start with that file.

  3. If you want to include some files, but not others, then you can use this syntax:

        [include]
           path = sixarm_git_gitconfig/gitconfig.d/alias.txt
           path = sixarm_git_gitconfig/gitconfig.d/color.txt

Install for specific operating systems:

  1. If your system is OSX, and you want to enable the keychain credential manager, then add this:

        [include]
           path = sixarm_git_gitconfig/gitconfig.d/specific-to-osx

  2. If your system is Windows, and you want to enable the system credential manager, then add this:

        [include]
           path = sixarm_git_gitconfig/gitconfig.d/specific-to-windows.txt


## Alias shortcuts

One letter shortcuts are for fast typing:

    a = add
    b = branch
    c = commit
    d = diff
    f = fetch
    g = grep
    l = log
    m = merge
    o = checkout
    p = pull
    r = remote
    s = status
    w = whatchanged

There are many two letter shortcuts for popular commands and options, such as these:

    ap = add --patch
    be = branch --edit-description
    ci = commit --interactive
    ds = diff --staged
    lg = log --graph
	ss = status --short

To see the complete list, please see the files in the `gitconfig.d` directory.


## Favorites

Here are some of our alias favorites that we use often:

Get everything new:

    get = !git pull --rebase && git submodule update --init --recursive

Rebase interactive on our unpushed commits:

    rbi = !git rebase --interactive @{u}

Summarize changes for a daily standup meeting:

    log-standup = !git log --since yesterday --pretty=short --author `git config user.email`

Find text in any commit ever:

    grep-all = !"git rev-list --all | xargs git grep '$1'"


## Publishing

Here are a couple our favorites for publishing. For the complete list, see `gitconfig.d/alias.txt`.

Publish the current branch by pushing and tracking:

    publish = "!git push -u origin $(git branch-name)"

Unpublish the current branch by deleting the remote branch:

    unpublish = "!git push origin :$(git branch-name)"



## Cleaning

Here are some of our favorites; for the complete list, see `gitconfig.d`.

Prune stale items:

    pruner = !git prune --expire=now; git reflog expire --expire-unreachable=now --rewrite --all

Repack the way Linus recommends:

    repacker = !git repack -a -d -f --depth=300 --window=300 --window-memory=1g

Delete all branches that have been merged into master:

    master-cleanse = !"git checkout master && git branch --merged | xargs git branch -d; git branch -r --merged origin/master | sed 's/ *origin\///' | grep -v '^master$' | xargs -I% git push origin :% 2>&1 | grep --colour=never 'deleted'"


## Feature Flow

Alias configuration for our feature flow. For details, see `gitconfig.d/alias-for-feature-flow.txt`.

Create a new feature branch:

    feature-start = '!branch=$1; git checkout master; git pull; git checkout -b "$branch" master'

Update the feature branch:

    feature-update = '!branch=$(git branch-name); git checkout master; git pull; git checkout "$branch"; git rebase master'

Share the feature branch:

    feature-share = '!branch=$(git branch-name); git push -u origin "$branch"'

If your team uses a different feature flow, you may want to skip including these aliases, or you may want to edit these aliases to match your team's feature flow.


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

To install git tab completion, we go to the git source code directory then run:

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
