# Ask Boopi to ignore files

Impressions: 4.5/5

Note:

 - It seems like nothing to change

---

In the previous chapter we created a file called `banana.txt` and provided incorrect instruction on how to craft a thing. In the end, we broke Boopi and had to fix him. To prevent such cases in the future we can use another feature that Git provides to us.

But before I name this feature, let's think about how we can tell Boopi not to read unknown files. 

One option is to create the file but not include it in the commit. In other words, don't use the `git add` command on such files. But if we had more than one file, say twenty or forty files. They will create a mess inside our `git status` command. They will be listed as untracked and will make noise in the output.

Another option would be to create a separate branch that puts all such files there. But what if some of the files are needed in the current branch? Not all files need to be stored in Git, but these files can also be useful to us. For example a file with passwords or something else.

As you can see, all of the above solutions may work, but they were not designed to solve such problems.

Woof-woof! Yes, Jessie! This feature called `.gitignore` file.

The `.gitignore` file is a special file in which we can specify which files are not to track and not to add to the commit, even though we run `git add .` (include all files). If the file is not added to the commit, then Boopi will not be able to craft it and accidentally break. This is exactly what we want to achieve.

> NOTE: Please don't forget to ad the `.` (dot) at the start of the file (e.g. `.gitignore`). It is required.

Usually, `.gitignore` file contains a list of other files and folders that are excluded from the tracking area of Git. If you create a file with the name which is listed in this `.gitignore` this file will not be visible for `git status` or `git add` command. It would be the same if you said: "Hey Git, everything that is called like this and that is ignored".

Let's create this file with the name `.gitignore` inside our folder and open it.

Inside opened `.gitignore` file we will list all files that we want to ignore in the future

```
passwords.txt
bad-instruction.txt
```

Save and close the file.

Starting from this point we asked Git not to track files that were listed in the `.gitignore` file, even though we write `git add .` or `git status`

Let's verify my words and create one of the files listed in `.gitignore` file.

We can create a `password.txt` file. Open the file and provide some fake passwords inside.

```
Password 123
```

Save and close the file.

This file is created in our folder and visible to us. But this file is not "visible" for Git. Let's run `git status` and verify that Git doesn't say that we have a new untracked file called `apple.txt`.

```
git status
```

It should print

```
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.gitignore

nothing added to commit but untracked files present (use "git add" to track)
```

As you can see, `git status` doesn't say that we created a `password.txt` file. It only shows that new `.gitignore` file was added to the folder. As far `.gitignore` is a special file that Git and Boopi know how to handle we can make a commit with this file. Yes, it is good practice (or required) to commit `.gitignore` file.

Let's add this file to the staged area and create a commit message like the following

```
git add .gitignore
git commit -m "Add special .gitignore file to the project"
```

From now on, if you are going to create any technical file (or folder) that should not be included in future commits, we can adjust the `.gitignore` file as we want. But do not forget to commit the `.gitignore` file after each update, although the `.gitignore` file starts working from the moment it is created, and not from the moment it is committed, it is still good practice.

Woof-woof-woof! Ah-ha! Jessie thanked you for helping us prevent future breakdowns of Boopi.

[Image where Jessie licks Boopi]

I remember Boopi's birthday is coming soon, let's prepare him a cake in the next chapter!

