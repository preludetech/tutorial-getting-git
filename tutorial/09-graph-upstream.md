# Understanding "remote origin"

When working with Git, you're often writing and committing code locally on your computer. But Git becomes truly powerful when you use it to collaborate with others or back up your work by connecting your local repository to a remote repository — a version of your repository hosted on a server, like GitHub, GitLab, or Bitbucket.

In the last section we connected to Github, and we used the command `git remote add origin ...` in order to configure our local repo so that it could push code to Github. 

Let's take a moment to understand what happened there. It's important to work to understand every line of code and every command you write! 

## What is a "Remote" in Git?

A remote is simply a reference to a repository that exists somewhere else, typically online. A remote repo doesn't have to be on Github. It can be:

- on a different Git service, eg: GitLab or BitBucket 
- on a separate computer or server you have access to. Some organisations will have their own way of storing code
- a different location on your own computer (although this usually isn't something people do)

By connecting your local Git repository to a remote, you can:

- Push your changes to the remote repository, so others can access them.
- Pull changes from the remote repository, so you can get updates others have made.

Think of it like syncing files between your computer and a cloud storage service. 

Multiple people working on the same project can have their own local Git repos on their own computers. All these repos can have the same "remote". Team mates keep their code in sync by interacting with the remote: One team member can `push` their latest code, and then another team mate can `pull` the code into their own local repo. 

Note: We haven't covered `git pull` yet, we'll do that in a future section.

## What Does the Command `git remote add origin ...` Do?

The command `git remote add origin <URL>` has three main parts:

1. `git remote add`: This tells Git that you're adding a new remote.

2. `origin`: This is the name you're giving to the remote repository. `origin` is not a special keyword but a widely used convention in Git. It makes it easy for you (and others) to know that this is the primary remote repository for your project. You could call your remote anything, but `origin` is like naming your home folder "Home" — it's just a common practice that simplifies communication.

3. `<URL>`: This is the address of the remote repository, such as https://github.com/username/repo.git. It tells Git where to find the remote.

A git repo can have multiple remotes, but you'll usually just have one. When you add a remote then it's like adding an address to an address book.

If you say `git remote add remote_name https://something.git` then you are telling your Git repo that whenever you say `remote_name` then you mean `https://something.git`.

Here are some commands you are likely to find useful in the future. Try these out:

```
git remote -v  # This lists all your remotes

git remote remove origin # this removes your remote! Don't worry, you can put it back :) 

git remote --help # remember that you can always use --help to see what options are available to you!
```


