# Prepare changes to be committed

Impressions: 2.5/5

Note:

 - There is a significant jump between the previous chapter and this one. Make it smooth at the beginning.
 - I have feeling that additional context of what commit is and when it is used must be added. 

---

To ask Git to track our file, we can run the next command.

```
git commit
```

Woof-woof! I know Jessie, it will not work, but let our reader understand why. 

Nothing wrong with this command but something is missing. Let's find it by reading the printed message in our console.

```
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	newfile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

If you read the message carefully, you should notice this sentence.

```
nothing added to commit but untracked files are present (use "git add" to track)
```

It says that to make our `git commit` command work, we need to specify what files will be included in this commit.

Well, going forward, a commit is a group of changes (files) that are stored somewhere inside Git. Simply saying, everything we add into a commit will be stored in Git and Git will take care of it (will track it)


So, let's add our `tennis-ball.txt` file into a commit.


```
git add tennis-ball.txt
```

As you can see, the `git add` command expects the file name that should be added to the commit. 

TIP: `git add` has much more power than specifying a single file name. It also can add multiple files by listing their names via comma or all files with extensions .txt by specifying a pattern (e.g. Git add *.txt)

Using the `git add` command, you asked Git to prepare this file to be ready to be committed, but not been committed yet.

Let's see what happened with our project after running `git add tennis-ball.txt`. We will use `git status`

```
git status
```

It should print something similar to your console.

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   tennis-ball.txt
```

Now Git says that there is a new file called `tennis-ball.txt` that will be committed.

After adding a `tennis-ball.txt` file into a staged area, Git makes a snapshot of our file and stores it as a copy in memory. If we make any changes to those files (that were added by using `git add` command and not committed yet), it will not automatically add changes to the snapshot, instead, it will show that some modifications exist and can be added to the commit if we want.

Let's try to achieve this by opening the `tennig-ball.txt` file and changing the diameter of the ball.

```
Step 1. Create a rubber ball with a diameter of 6.55 cm
Step 2. Color it green
Step 3. Add curved white lines
Step 4. Craft
```

We changed the diameter from 6.54 to 6.55. The changes are minor, but enough for Git to notice them.

Let's again run the status command and see what it shows to us

```
git status
```

The output should be similar to 

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   tennis-ball.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   tennis-ball.txt
```

As you can see, Git shows us that some changes will be committed as well as changes that are not staged for commit.

```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   tennis-ball.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   tennis-ball.txt
```

To see new changes that of increased diameter of the ball we can use another helpfull command called `git diff`. To run it, we need to specify the file on what we want to run this command

```
git diff tennis-ball.txt
```

It should print something like

```
diff --git a/ennis-file.txt b/ennis-file.txt
index 81d5611..3c89c6c 100644
--- a/tennis-file.txt
+++ b/ennis-file.txt
@@ -1 +1 @@
-Step 1. Create a rubber ball with a diameter of 6.54 cm
+Step 1. Create a rubber ball with a diameter of 6.55 cm
```

As you can see it shows the line that were modified and compare them line by line.

So, At this point we can do few more things. Either include our changes to the commit or discard them. In our case it is not big deal will diameter be 6.54 cm or 6.55 cm. But let's for education purposes discard our changes by running `git restore`

```
git restore tennis-ball.txt
```

It should remove our changes, that were made after adding `git add tennis-ball.txt`. That is, `modified: tennis-ball.txt` should disappear form the `git status` messaage.

Let's verify it by running `git status`

```
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   tennis-ball.txt
```

Good job. Modification dissaper. 

In the next section we will make a commit of our staged changes. Let's go!
