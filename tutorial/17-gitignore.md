# Gitignore

If you work on a serious project, then you are very likely to have a bunch of files in your local project directory that you don't want Git to track. 

You only want to track actual code that you wrote yourself. You don't want to store things that were automatically downloaded, auto-generated files, secrets,  sqlite test databases, or many other things. 

Here are some specific examples of things you wouldn't want to track:

- If you are running a Python project then you shouldn't track anything in any directory called `__pycache__/`
- If you are using node then you shouldn't track your `node_modules/` directory
- If you are developing a Django application then you shouldn't track your `db.sqlite3` file

There are many other examples.

So if you run the command `git add .` then what you really need is for Git to stage all your changed files *except* for the ones you want it to ignore.

You can configure this behaviour by creating a `.gitignore` file in your repo.

When you create a .gitignore file then Git will always check that file when you run `git add .` and it will skip over whatever you tell it to. 

[Here](https://github.com/github/gitignore) is a repo that contains a lot of `.gitignore` files. You can use this as a reference whenever you create a new project.

## Let's make our own .gitignore file 

Make a new directory called `ignore_me` and put some stuff in it. This can be anything at all, you can make some html files, or even pictures. So long as you put at least one file in there, we are good to go.

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
