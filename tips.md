# Git Tips

## Log

http://gitready.com/advanced/2009/01/20/bend-logs-to-your-will.html

Most of these tips are from Scott Chacon’s gitcast on git log and R. Tyler Ballance’s git protip series.

`git log -<n>`
  
Show `n` number of commits. For example, `git log -2` shows the last two commits.

`git log --stat`

Show files changed and insertions/deletions. Basically the normal output of git commit appended to each message.

`git log --name-status`

Show SVN-like add/modified/deleted for each commit. Very basic but still gives a decent idea about what’s changed.

`git log --oneline`

Compress each commit to its SHA1 and message on one line. Pipe to wc -l if you want to count commits.

`git log -- origin..HEAD`

Show commits that have not been pushed to your origin remote. (Thanks for the tip, Ryan Bates!)

`git log <file>`

Show commits that affected only the file given.

`git log --no-merges --author=dave`

Show commits that dave has worked on, and ignore any merge commits to reduce noise.

`git log --since="1 week ago"`

Show commits that have happened since last week. Could easily be replaced with `yesterday`, `1 year ago`, `3 months ago`, `12/31/2014` and so on. There’s also other time based options: `--after`, `--until`, and `--before`.

`git log --grep='^Bump'`

Search commit messages to find ones that start with the string “Bump”. This will take in any regular expression, so if you’re looking for that one commit you did and all you can remember is a part of the message, --grep will find it.

Search commits for matching text.

`git --no-pager log`

Don’t want to use less to view your commits? This option will just give you the straight output if you need it.



