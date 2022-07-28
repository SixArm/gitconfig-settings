# gitconfig settings

Git configuration settings, files, aliases, branches, merges, syntax coloring, merges, credentials, and more.

Examples:

  * Nicknames such as `git s` doing `git status`
  * Workflows such as `git rbi` doing a rebase, interactively, on unpushed commits.
  * Helpers such as `git optimize` doing a prune and repack.
  
For the complete list, see the files in the `gitconfig.d` directory.


## Install

Install for novices:

  1. Get these files:

        git clone https://github.com/SixArm/sixarm_git_gitconfig.git

  2. Create your own personal `.gitconfig` file, or edit your existing file, such as:

        edit ~/.gitconfig

  3. Add these lines:

        [include]
           path = sixarm_git_gitconfig/gitconfig

Install for experts:

  1. If you want full control, then you can copy any of these files and edit them as you like.

  2. The `alias.txt` file has the bulk of the items - start with that file.

  3. If you want to include some files, but not others, then you can use this syntax:

        [include]
           path = sixarm_git_gitconfig/gitconfig.d/alias.txt
           path = sixarm_git_gitconfig/gitconfig.d/color.txt

Install for specific operating systems:

  1. If your system is OSX, and you want to enable the keychain credential manager, then add this:

        [include]
           path = sixarm_git_gitconfig/gitconfig.d/specific-to-osx.txt

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


  

## Stash

A recent addition to git which defaults the -p flag to `git stash show`. This makes `git stash show` show the diff from that stash. In our opinion, this should be the default.

  ~~~gitconfig
  git config --global stash.showPatch true
  ~~~


## Autostash

Automatically stash and unstash the working directory before and after rebases. This makes it possible to rebase with changes in the repo.

  ~~~gitconfig
  git config --global rebase.autostash true
  ~~~


## Decorate

Always decorate `git log`.

  ~~~gitconfig
  git config --global log.decorate full
  ~~~  
  

## Autosquash

Setting autosquash enables it by default for all interactive rebases. When committing you can specify `--squash=<commit>` or `--fixup=<commit>`, then `git rebase -i --autosquash` will automatically move and mark the relevant commits in your rebase queue. 

  ~~~gitconfig
  rebase.autoSquash true
  ~~~


## User config

We prefer to be explicit about user configuration, rather than to use the default user configuration, which looks for a local identity, then looks for a global user identity, then tries to guess a user identity based on your current user and machine.

  ~~~gitconfig
  user.useConfigOnly true
  ~~~

The `useConfigOnly` setting mandates an explicit configuration. Then we can remove any global git user and/or git email. Then git will require the correct configuration of any local repository before allowing commits.


## Commit intent

When performing a rebase (interactive or not) it can be difficult to remember what the original intent of a specific commit is when it's mixed with conflict markers. This shows the original commit being rebased.

  ~~~gitconfig
  alias.original "!git show $(cat .git/rebase-apply/original-commit)"
  ~~~


## Recursive git

If you accidentally type `git git foo`, then correct it.

  ~~~gitconfig
  alias.git "!git"
  ~~~

## Merge tool

    merge.tool <yourtool>

Will automatically use the specified tool when invoking "git mergetool", if you like external utilities to perform merges or conflict resolution (

Try these: emerge, kdiff3, araxis, vimdiff3, meld. The list of builtin tool support is accessible via "git mergetool --tool-help".


## FF

This has saved me:

  ~~~gitconfig
  git config  --global pull.ff only
  ~~~

I can always override an individual pull invocation with either "git pull --rebase" or "git pull --no-ff". This makes it a conscious choice when a fast-forward pull is not possible.

If you set this config, and a fast-forward pull is not possible, here is what git does:

  ~~~shell
  $ git pull
  fatal: Not possible to fast-forward, aborting.
  ~~~


## Signing vs. fast forward

If the workflow rule is that merge commits to master are not permitted (ie. all commits must be rebased onto master first), then one person cannot rebase someone else's signed commits without losing those signatures. 

Theoretically one could devise a tool which allows each contributor to re-sign (in the correct order), but I'm not aware that any such thing exists, and it'd probably be too impractical anyway.

In a shared repository, I prefer creating "useless" merge commits to changing other peoples signatures.


## diff-so-fancy  

I really like diff-so-fancy [1] highlighter as a pager and to review diffs. Previously discussed here on HN here: [2]

  * https://github.com/so-fancy/diff-so-fancy

  * https://news.ycombinator.com/item?id=11057421


## force with lease

If we are stuck and we must push with force, then we use this:

    git push --force-with-lease

Instead of:

    git push -f

The advantage of the former over the latter is that it won't push if we haven't already seen the ref we're overwriting. It avoids the race condition of accidentally "push -f"ing over a commit we haven't seen.

In our opinion, this should be the default.


## Log format

Log format with condensed view, graph, and tags:

  ~~~gitalias
  lg = log --pretty=format:\"%C(yellow)%h%C(reset) %C(green)%ad%C(reset) %C(red)|%C(reset) %s %C(bold blue)[%an]%C(reset)%C(yellow)%d%C(reset)\" --graph --date=short
  ~~~

Log forward that shows dates at the end, in a relative format (2 days ago, 29 hours ago, etc) and the tags/branches before the commit message:

  ~~~gitalias
  lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen%cn%Creset %Cblue(%cr)%Creset' --abbrev-commit --date=relative
  ~~~

Another:

  ~~~gitalias
  lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  ~~~


## Yellow

One thing I like to do is alter the coloring as an aide for `git status` which is giving "changed" a yellow as an intermediary color:

  ~~~gitconfig
  [color "status"]
    untracked = red
    changed = yellow
    added = green
  ~~~


## Vim diff

I'm a long time vim user and my brain is wired to reach for the keyboard shortcuts in vimdiff to jump from diff to diff. 

Also, I really love diffing entire trees in one vim session using the DirDiff plugin (https://github.com/will133/vim-dirdiff).

Here's how I wire it into my .gitconfig, which gets me the alias "git dirdiff":

  ~~~gitconfig
  [difftool "default-difftool"]
    cmd = gvim -f '+next' '+execute \"DirDiff\" argv(0) argv(1)' $LOCAL $REMOTE

  [difftool]
    prompt = false

  [alias]
    dirdiff = difftool --dir-diff
  ~~

I like to use gvim to open new windows separate from my terminal, but if you prefer you can just use plain vim in there as well.

Also, if using vim for viewing diffs, you might want to hack vim's config as well to make it look good. I like to (effectively) disable folding of lines with no diffs so I can still read the whole file- I use the shortcuts ]c (next diff) and [c (previous diff) to jump around diffs. I also like to disable editing in diff mode.

Here's my diff-related .vimrc hackage:

  ~~~vimrc
  if &diff
    set lines=60 columns=184
    set foldminlines=99999
    set nomodifiable
    set nowrite
  endif
  ~~~
reply
  

## tmux

I have a dedicated Git tmux tab for every repo I'm working on, in that tab I use a git shell. Initiated by this bash function:

  ~~~shell
  # A nice shell prompt for inside git repostories
  # Shows a short status of the repository in the prompt
  # Adds an alias `g=git` and makes autocomplete work
  gitprompt() {

      __color_bold_blue='\[$(tput bold)\]\[$(tput setaf 4)\]'
      __color_white='\[$(tput sgr0)\]'

      export GIT_PS1_SHOWDIRTYSTATE=true;
      export GIT_PS1_SHOWSTASHSTATE=true;
      export GIT_PS1_SHOWUNTRACKEDFILES=true;
      export GIT_PS1_SHOWUPSTREAM="auto";
      export GIT_PS1_SHOWCOLORHINTS=true;
      . /usr/lib/git-core/git-sh-prompt;

      local ps1_start="$__color_bold_blue\w"
      local ps1_end="$__color_bold_blue \\$ $__color_white"
      local git_string=" (%s$__color_bold_blue)"

      export PROMPT_COMMAND="__git_ps1 \"$ps1_start\" \"$ps1_end\" \"$git_string\""

      # Short alias for git stuff
      alias g=git

      # Make autocomplete also work fo the `g` alias
      eval $(complete -p git | sed 's/git$/g/g')

  }
  ~~~

So I have this in my `.bashrc` and when I want my bash to get a handy Git prompt I type `gitprompt`.

You do need the file `git-sh-prompt` which should come with git, for me it's located in `/usr/lib/git-core/git-sh-prompt`. It's also available here:

* https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh


## fsckobjects
  
Don't set fsckobjects=true. There are normal repositories that have broken trees which will not download if you have it set. Yes it is irritating and I would rather turn it on, but I had to turn it off after several repos failed for me.

The fsckObjects settings are entirely separate from the SHA. They are about syntactic and semantic rules in the objects themselves (e.g., well-formatted committer name/dates, tree filenames that don't contain "/", etc).

Git doesn't check validity of commit hashes by default.


## Merge/diff tools

* The merge/diff tool I use is p4diff, which comes with P4V (Perforce visual client) and is free.


## tig

To explore the git log, I use tig. https://github.com/jonas/tig

It is a curses interface to git. Screenshot: https://atlassianblog.wpengine.com/wp-content/uploads/tig-2....


## GPG with keybase.io to sign commits

Shameless plug. I published a little guide some months ago, on how to use GPG with keybase.io to sign commits.

Link: https://github.com/pstadler/keybase-gpg-github

Discussion on HN: https://news.ycombinator.com/item?id=12289481


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
  * <https://blog.scottnonnenberg.com/better-git-configuration/>
  * <https://news.ycombinator.com/item?id=14045787>


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
