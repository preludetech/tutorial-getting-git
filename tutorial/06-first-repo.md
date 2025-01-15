# Making your first Git repo 

We have covered a lot of ground already, at this point you should:

- have a basic idea of how the Git graph structure works
- have a basic theoretical idea of what a `commit` is and what it means to `checkout` 
- have git installed 
- be familiar with the basic Bash commands used for navigating around a filesystem 

If you aren't comfortable with any of that stuff, please go back and revisit it! And remember that questions are welcome! 

Learn to ask good questions! It's a super-power! 

## Your project 

For the rest of this workshop, you will be using Git to track changes on a project. You'll be making a very simple personal website. You'll even host it on the web! 

Don't worry, you don't need to know anything about web development to follow along. We'll be keeping the web stuff really basic and showing you what to do every step of the way.

## Video 

If you are struggling to follow along with the instructions here, [this video](https://www.youtube.com/watch?v=7TprabACC6Q) shows you exactly what to do.

## Stay organised!

As you move forward in your software development journey, you will be writing a lot of code for a lot of different projects. It's important to stay organised! 

Make sure each project has it's own directory.

And make sure your project directories are in a sensible location.

Here is how I organise my projects:

- In my home directory, I have a directory named `workspace`
- My `workspace` directory contains all my projects, each project has a separate directory 

So if I want to navigate to any project, I can say: `cd ~/workspace/project_name`. 

## Let's make a repository

Create a new directory for your website, let's call it `personal_website`. Then `cd` into the new directory.

On my system I would do it like so:

```
cd ~/workspace
mkdir personal_website
cd personal_website
```

Next up, we need to tell Git that we'll be using this directory as a repository (repo for short).

```
git init
```

You'll see a whole lot of text printed out. You are welcome to read it, but don't worry about it for now.

Now let's take a look at what is in the directory. If you use the `ls` command then the directory will look empty. But Git did make some changes. Git created a hidden directory. 

Use `ls -a` to see what Git created. It created a directory called `.git`.

The `.git` folder is a perfectly normal directory. This is where Git stores information about your repo. It'll keep track of your commits here. 

## Making a change

Next up, let's create a file:

Create a file called `README.md`. You can do this with Bash, or you can use any text or code editor. Just make sure that you save the file inside your project directory (`personal_website`).

Put the following text inside your README file and save it:

```
# Personal website 

This website is being created as part of a [Prelude](https://prelude.tech/) Getting Git workshop.
```

## Git status 

The `git status` command can be used at any time. It will give you a short summary of the status of your repo. Try it now. 

You'll see something like this:

```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

We'll be using `git status` a lot during this tutorial. Always read the output really carefully! Some of it wont make all the sense just yet, but it will become familiar as we move forward.

## Track changes

Git is cool because it doesn't jump to conclusions about what it should do. You get to choose what to commit and when.

Making a commit is a 2 step process:

1. Decide what files you want to include in the commit (staging)
2. Create the commit 

To stage a file, use the `git add` command.

```
# you can stage specific files like so:
# git add /path/to/file

# In our case we can do this: 

git add README.md 

# You can also stage ALL changed files like so:

git add . 
```

Once you have staged your changes, use `git status` again. Can you spot what changed?

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

## Commit your staged files

Here is a command you can use to create your first commit:

```
git commit -m "created readme"
```

This tells Git to take the changes you have staged and remember about them. It also adds a message to the commit, "created readme". It is VERY useful to be descriptive when creating commits because it's useful to see a log of what you have achieved. It's also helpful if you ever need to `checkout` a commit.

Try type in `git status` again and see what it looks like now.

## Let's make more changes 

Now create another file in the root of your project. Let's call it `index.html`

Put the following text inside your index.html file and save it:

```
<!DOCTYPE html>
<html>

<head>
    <title>Personal website</title>
</head>

<body>
    <h1>My Website</h1>
    <p>This website is being created as part of a <a href="https://prelude.tech">Prelude</a> Getting Git workshop.</p>
</body>

</html>
```

## Create another commit 

Now make another commit with your changes. Try to remember what `git status`, `git add` and `git commit` do and how to use them. 

Make sure you give your new commit a meaningful message, for example `Created index page`.

## Personalise your index page

If you open your `index.html` page in your web browser (Firefox, Chrome or whatever you are using), then you'll see that it is a working web page. 

Try change some of the text in the page. Instead of saying "My Website", you could put your own name. Or you could change the title of the page. Just make some small changes. 

Now try this command:

```
git diff
```

This will let you see what has changed since the last commit. 

Then create another commit. Give it a nice message, for example "Personalised index page"

You should now have 3 commits.

## Viewing the log 

Type in the following command:

```
git log
```

This will show you a list of all the commits you've made, there should be 3. 

You can press `Q` to get your terminal back to normal.

My Git log looks like this:

```
commit 5a39678344011133ce255be732c56ee2ccf53f90 (HEAD -> master)
Author: Sheena <sheena@myemail.com>
Date:   Sat Jan 4 09:56:49 2025 +0200

    Personalised index page

commit 5fb2a12f54dd56f35b2583e8c4f9c672295dc5b1
Author: Sheena <sheena@myemail.com>
Date:   Sat Jan 4 09:51:39 2025 +0200

    Created index page

commit 972e328490def2f9ea9f5aebbd51b7514340586f
Author: Sheena <sheena@myemail.com>
Date:   Sat Jan 4 09:13:51 2025 +0200

    created readme
```

For each commit, you can see:

- the commit hash (eg: `972e328490def2f9ea9f5aebbd51b7514340586f`)
- who created the commit
- when it was created
- the commit message 

## Viewing a commit's details

Each commit has a unique hash. You can think of a hash as a special address. The hashes for your commits will be different to mine. 

If you want to interact with a commit in any way, then you will need to refer to it by its commit hash. 

For example, let's say you wanted to see what changes were made by the commit with the message "Created index page". 

```
commit 5fb2a12f54dd56f35b2583e8c4f9c672295dc5b1   # < The commit hash is here 
Author: Sheena <sheena@myemail.com>
Date:   Sat Jan 4 09:51:39 2025 +0200

    Created index page
```

Now I can use `git show` to see what happened in that commit:

```
git show 5fb2a12f54dd56f35b2583e8c4f9c672295dc5b1
```

Try it for yourself! But make sure you use hashes from your own git log!

Read through the entire output from the `git show` command

## Reflog 

Another way to view the git log is using the `git reflog` command. Try it out!

Mine looks like: 

```
5a39678 (HEAD -> master) HEAD@{0}: commit: Personalised index page
5fb2a12 HEAD@{1}: commit: Created index page
972e328 HEAD@{2}: commit (initial): created readme
```

You'll notice that the hashes are a lot shorter. Eg: `5fb2a12` instead of `5fb2a12f54dd56f35b2583e8c4f9c672295dc5b1`. 

Does `git show` work with the shorter hashes? Try it out and see for yourself. Eg:

```
git show 5fb2a12
```

## Checkout 

Use the `git checkout` command to make your files look like they did at a specific point in time. This is like time travel.

Let's say I want to see what my index page looked like before I personalised it. I would need to checkout the commit with the message "Created index page".

```
5a39678 (HEAD -> master) HEAD@{0}: commit: Personalised index page
5fb2a12 HEAD@{1}: commit: Created index page  # <<<<<  This commit
972e328 HEAD@{2}: commit (initial): created readme
```

So my checkout command will be:

```
git checkout 5fb2a12
```

Note: You will need to use your own commit hash here.

Go ahead and `checkout` your own "Created index page" commit. Take a look at your `index.html` file. Can you see what changed? 

Now try `git log` and `git reflog` again. There are fewer commits showing up! 

Try `git status` as well. What do you notice?

Now `checkout` your initial commit. Your `index.html` file got deleted! 

Now let's restore everything to the latest version. Use this command:

```
git checkout master
```

Again, look at your files and your `git log`. You should now have everything restored to the latest version.

## Solidify your knowledge 

We went through a whole lot of commands in this section. There is a lot to remember and understand. 

If you want to remember and master this stuff then it would be useful for you to take a few minutes to write down some of what you learned.

On a sheet of paper (or in a text editor), write down all the git commands you just learned. See if you can explain what they do in your own words.

If you try your best to remember the commands then that will help you remember them in future. So try your best to remember. 

If you can explain the commands in your own words then that will help you to build stronger mental frameworks so that you will understand new concepts faster.

### Commands covered in this section

Here are all the commands covered in this section. Were you able to remember them all?

```
commit 
add 
status
log
reflog
show 
diff
init
```
