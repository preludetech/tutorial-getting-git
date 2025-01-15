# Understanding upstream branches 

In [the last section](./12-multiple-branches.md) you were given the challenge of pushing your new branches to Github.


## Exploring branches

Earlier, we used the command `git branch` to see what branches were available. Here are a few more things you can do:

Try this out:

```
git branch -a
```

This will output something like this:

```
* main
  remotes/origin/main
```

This command will list your local branches as well as your remote branches. For more detail on how this works, try type in `git branch --help`.

Now try this out:

```
git branch -v
```

Can you understand what you see there? 

Now try this one:

```
git branch -vv
```

This command will give you a bunch of information. Here wyou will be able to see if your local branches have upstream branches, and where those upstreams are.

Eg:

```
  feature/contact_page 67748be [origin/feature/contact_page] Added contact page link to home page
```

This tells us that our local `feature/contact_page` branch is set up so that it will push to and pull from the `feature/contact_page` branch on the remote named `origin`.

You can also type in `git branch -a -vv` - this will give you an idea of which remote branches are out of date. Can you see how?

## Pushing specific branches 

Git is a **distributed** version control system. The basic idea is that every copy of the repo will get a copy of every commit. You do have to choose when to push (upload) and pull (download) the different commits. It doesn't happen automatically, you are in control!

Let's say you checkout your contact feature branch and then push it:

```
git checkout feature/contact_page
git push
```

This will upload all the commits that are in the history of the `feature/contact_page` branch. It will push the `HEAD` commit and all it's ancestors (its parent, the parent's parent, etc).

It will not automatically push the commits that are on your portfolio or main branch. It will only update the `upstream`.
