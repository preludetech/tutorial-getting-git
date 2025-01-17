# What happens when you delete a file?

If you delete a file by mistake, then you can use Git to recover it. Try this out:

1. Create a new file called `delete_this.md` and put some random text inside it. 
2. Save the file
3. Commit the file to the repo

```
git add .
git commit -m "added file to be deleted"
```

4. Now delete your `delete_this.md` file 
5. Check your `git status`.  The output should look like this:

```
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    delete_this.md

no changes added to commit (use "git add" and/or "git commit -a")
```

6. Again, commit your changes and push:

```
git add .
git commit -m "deleted the file again"
```

## View the deleted file 

You can use `git log` to see the commit where your file was added:

```
commit 6d49536aef90d0cac14b0738749fe470edea41be (HEAD -> main)
Author: Sheena <me@email.com>
Date:   Tue Jan 14 14:13:46 2025 +0200

    deleted the file again

commit d7071a14bcabfcf9f0c7ab9e9838a55118141c29
Author: Sheena <me@email.com>
Date:   Tue Jan 14 14:12:15 2025 +0200

    added file to be deleted
```

You can now use `checkout` to look at what was in the file before it was deleted.

## Restoring the deleted file

Checkout your `main` branch, then use the following command: 

```
git checkout YOUR_COMMIT_HASH -- delete_this.md
```

Note, you'll need to use your own commit hash in the command for this to work. 

On my computer, this is the command:

```
git checkout d7071a14bcabfcf9f0c7ab9e9838a55118141c29 -- delete_this.md
```

Now your `delete_this.md` file will be visible in your project directory. Go and look at the file, it will look like it did before you deleted it.

Run `git status` and make sure you understand what it says.

## Security implications

Beginner developers sometimes make the mistake of committing secret files to their repos. For example `my_secret_key.json` or `password.txt` or similar. They often add the file to their repo, commit some changes, push those changes, and then panic and delete the files and make another commit.

But it is important to know that Git allows any deleted file to be recovered. 

If you ever commit a secret to your repo and push your changes, then anyone who has access to your repo will have access to your secrets! 

If you are working with a public repo hosted on Github then this mistake will broadcast your secrets to the entire Internet! 

As a rule: **NEVER EVER COMMIT SECRETS** unless you are fine with people having access to those secrets. 

## Video 

[Here](https://www.youtube.com/watch?v=bNCRjMIyJyA) is a video that demonstrates the above. It also explains the security implications.