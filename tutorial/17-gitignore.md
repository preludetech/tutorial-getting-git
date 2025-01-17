# Gitignore

If you work on a serious project, then you are very likely to have a bunch of files in your local project directory that you don't want Git to track. 

You only want to track actual code that you wrote yourself. You don't want to store things that were automatically downloaded, auto-generated files, secrets,  sqlite test databases, or many other things. 

## Imagine...

Here is a scenario. Imagine that you are working on an e-commerce project with a team of developers. 

Now, you are working on a feature to do with adding items to a "shopping basket". While you work on your feature you need to:

- define some database tables
- write code that stores and fetches data from those tables 

As you do your work, you run your application locally so you can play with your feature and see that it's behaving how you want it to. Of course, you will also write some automated tests to be certain that things work, but you also use your application's GUI to try things out.

As you do this, you make changes to a local development database. You are using sqlite so your database is a single file on your computer.  This file is a binary file, it does not contain human-readable text, just a whole lot of 1s and 0s. The changes to that file are pretty random in a way, you're just playing and testing things out.

Now, one of your team-mates has a similar situation. They are working on a "Forgot Password" feature. Here they need to manage and play with some data to do with user email addresses, passwords and secret tokens. 

So you and your team mate will both be making weird changes to your local sqlite databases.

If you both `git add` your respective sqlite database files, and try to merge your code then there will be some really hairy merge conflicts. This would be painful to merge. And since the data in the database is random test data that you don't even need, fighting this merge conflict would be a waste of time.

Now, let's say you are busy on your work and there have been some big changes to the `main` branch so you `pull` main and merge it into your own branch. This way you have the latest version of the project's accepted code in your branch and you can make sure your code is compatible with that code.  

If that ends up messing with your test data then that can lead to confusing results or more wasted time.

It would be much better if you just didn't commit your random test data.

## What to ignore

Here are some specific examples of things you wouldn't want to track:

- If you are running a Python project then you shouldn't track anything in any directory called `__pycache__/`
- If you are using node then you shouldn't track your `node_modules/` directory
- If you are developing a Django application then you shouldn't track your `db.sqlite3` file

There are many other examples.

So if you run the command `git add .` then what you really need is for Git to stage all your changed files *except* for the ones you told it to ignore.

## Telling Git what to ignore

You can configure this behaviour by creating a `.gitignore` file in your repo.

When you create a `.gitignore` file then Git will always check that file when you run `git add .` and it will skip over whatever you tell it to. 

## Let's make our own .gitignore file 

Make a new directory called `ignore_me` and put some stuff in it. This can be anything at all - you can make some plain text files, html files, or even add pictures. So long as you put at least one file in your `ignore_me` directory, we are good to go.

Now, check your `git status`. It will say something like this:

```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ignore_me/

nothing added to commit but untracked files present (use "git add" to track)
```

If you were to use `git add .` now, then your `ignore_me` directory and everything in it would be staged for the next commit.

Now, make a new file called `.gitignore`. Put it in the root of your project (in the same directory as your README.md file).

Edit your `.gitignore` file so it looks like this:

```
ignore_me/
```

This tells Git that you don't want to add anything from your `ignore_me` directory.

Run `git status` again. The output will look like this:

```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

nothing added to commit but untracked files present (use "git add" to track)
```

As you can see, the `.gitignore` file is ready to be staged for commit, but Git is ignoring your `ignore_me` directory.

Now commit and push your changes:

```
git add .
git commit -m "added gitignore file"
git push
```

Take a look at your repo on Github and make sure it all makes sense.

## Demo video 

[Here](https://www.youtube.com/watch?v=4ppjylNwACg) is a video that demonstrates the above.

## Syntax

The gitignore file has it's own specific syntax. You can read about it [here](https://www.atlassian.com/git/tutorials/saving-changes/gitignore).

There is no need to memorize this stuff, just try your best to understand what the different patterns allow. 

## What to ignore

[Here](https://github.com/github/gitignore) is a repo that contains a lot of `.gitignore` files. You can use this as a reference whenever you create a new project.

Take a moment to look at a few files there. Try to find gitignore files that are related to something you work with, for example,  you might want to look at the Python or Node files.