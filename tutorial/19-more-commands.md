# More Git commands 

We have covered a lot of ground! In this section we are going to touch on a few other commands you will likely come across in your developer journey. We wont go into these in great detail in this workshop. 

We will be relying on Atlassian's excellent documentation to understant these concepts. 

Please take some time to read these docs. You should have all the tools you need to understand these.

When there are worked examples, including code or commands, please read them line by line. Make sure you understand each and every line! And remember to ask questions if you get stuck!

## Git rebase 

Rebase rewrites history. It is often used instead of `git merge`.

Read [this](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase) for a good explanation.

It's useful to know about Rebase becuse it is used very often. With rebase you can make sure your commit history is linear and this makes it easier to understand and navigate. 

## Git stash 

Sometimes you get into a situation where you are not quite ready to commit your code, but you need to switch branches and work on something else. This is where `git stash` comes in.

Read [this](https://www.atlassian.com/git/tutorials/saving-changes/git-stash) for a good explanation.

## Git tag

In Git, a tag is a kind of label that points to a specific commit. You can think of it as a branch that doesn't get updated. Once you have tagged a commit, then the tag will stay with that commit.

Tags are often used for tracking versions. Eg a specific commit can be tagged as `v1.3.2`.

Learn more [here](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)

## Undoing changes 

Sometimes you will want to unstage a file, undo a commit, remove an ignored file or similar. 

Read [this](https://www.atlassian.com/git/tutorials/undoing-changes) to get an idea of some of what you can do.

Pay special attention to the `git reset` command, it is commonly used and commonly confused with `checkout`.