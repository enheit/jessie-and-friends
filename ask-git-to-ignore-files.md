# Ask Boopi to ignore files

Impressions: 5/5

Note:

 - It seems like nothing to change

---

In the previous chapter we created a file called `banana.txt` and provided incorrect instruction on how to craft a thing. In the end, we broke Boopi and had to fix him. To prevent such cases in the future we can use another feature that Git provides to us.

But before I name this feature, let's think about how we can tell Boopi not to read unknown files without upcoming feature. 

The first thing that comes to my mind is to create the file but not include it in the commit. In other words, don't use the `git add` command on such files that may broke Boopi. But if we had more than one file, say twenty or forty files. They will mess up the output of the `git status` command and make noise like unused untracked files.

The second thing we could do is create a separate branch where we put all the files that might break Boopy. But what if some of those files would be needed in the current branch? Not all files need to be committed to Git, but they can also be useful to us. For example, a file with passwords. It would be unnecessary to put file with sensetive information into the Git history. Boopi can create a thing that will have your password written on it. Not what you expect, right?

As you can see, all of the above solutions can work with a little tweaking, but they were not designed to solve such problems.

Woof-woof! Ah-ha! Jessie asked me to finally name the feature and stop beating around the bush.

So, the `.gitignore` is a special file in which we can specify which files will not be tracked by Git and accidentally committed by us, even though we run `git add .` (to include all files). If the file is not added to the commit, then Boopi will not be able to craft it and accidentally break. This is exactly what we want to achieve.

> NOTE: Please don't forget to ad the `.` (dot) at the start of the file (e.g. `.gitignore`). It is required.

Usually, `.gitignore` file contains a list of other files and folders that are excluded from the tracking area of Git. If you create a file with the name which is listed in this `.gitignore` this file will not be visible for `git status` or `git add` commands. It would be the same if you said: "Hey Git, everything that is called like this and that is ignored".

Let's create this file with the name `.gitignore` inside our folder and open it.

Inside opened `.gitignore` file we will list all files that we want to ignore in the future

```
passwords.txt
bad-instructions.txt
```

Save and close the file.

Starting from this point we asked Git not to track files that were listed in the `.gitignore` file (e.g. `password.txt` and `bad-instructions.txt`), even though we write `git add .` or `git status` commands.

Let's verify my words and create one of those files beside recently created `.gitignore` file.

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

From now on, if you are going to create any technical file (or folder) that should not be included in future commits, you can adjust the `.gitignore` file as you want. But do not forget to commit the `.gitignore` file after each update. By the way, the `.gitignore` file starts working from the moment it is created, and not from the moment it is committed, but it is still recommended to commit it.

Woof-woof-woof! Ah-ha! Jessie thanked you for helping us prevent future breakdowns of Boopi.

[Image where Jessie licks Boopi]

Woof-woof!

Jessie said Boopi's birthday is coming soon, let's surprise him in the next chapter!

