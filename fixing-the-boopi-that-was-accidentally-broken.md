Fixing the Boopi that was accidentally broken

As we remember, every time a commit appears in the history on the `master` branch, it signals Boopi to start to craft things. But what if we accidentally commit the file that does not contain instructions for Boopi. Let's figure out what happens. 

Let's create a file called `apple.txt` and put something inside that Boopi does not know. 

Let's open an `apple.txt` file and write the following.

```
Step -1: abcdefg
```

Save the file and close it.

Now, let's commit this file.

```
git add apple.txt
git commit -m "Add apple.txt"
```

Oops, look at Boopi. It seems like we broke him again. 

[Image of broken Boopi after executing invalid instructions]

How can we undo the instructions that we gave to Boopi? The simplest solution would be to remove the file that we committed. That is, remove the file in our folder and create a new commit (e.g. "Remove apple.txt file). 

Instead of doing it manually, Git has a special command that can do it for us. The name of the command is `git revert`. 

Whenever you make a commit that doesn't work as expected, you can use `git revert <commit_hash>` to roll back those changes. As you can see, it requires the hash of the commit. We can find this hash inside Git logs by running `git log` command. As far as we want to undo the lastest commit in our history, we can specify an additional `-1` parameter with `git log` command. Let's write it

```
git log -1
```

It should print the description of the lastest commit in our Git history (of the active branch)

```
commit e6d979b1498e7d27cba0780e23c7bfbeca84790e (HEAD -> master)
Author: Roman Mahotskyi <roman.mahotskyi@gmail.com>
Date:   Tue Jul 5 19:14:41 2022 +0300

    Add apple.txt
```

Let's copy the long hash on the first line of the log message. Now we can write revert command and provide this commit hash

```
git revert e6d979b1498e7d27cba0780e23c7bfbeca84790e
```

It should open an editor with a default commit message. 

```
Revert "Add apple.txt"

This reverts commit e6d979b1498e7d27cba0780e23c7bfbeca84790e.
```

If you want, you can change this commit message and its description or leave it as is.

After closing the editor with a commit message, Git must revert recently added changes for us. In our case, he should remove the `apple.txt` file.

Now open our folder and verify that `apple.txt` was removed from the folder. It looks like the file with the bad instruction no longer exists. But what actually happened?

If you run a `git log -2` command again, you should notice that the commit where we have added an `apple.txt` file still exists in a history as well as a new commit with the message `Revert "Add apple.txt"`.

I know this is not what you expected.

Whenever you revert changes instead of re-writing the history and removing the existing commits, Git creates a new commit with mirrored changes. In our case, in that commit, we created a single file called `apple.txt` and added it to the commit. After running `git revert` Git removed this file for us and created a new commit with changes. If we didn't create the file but only made some changes to it, Git would remove those changes and create a new commit only with those removed changes.

Woof-woof! Yes, it seems like Boopi is working again! Are you alright? Boop-boop!

[Image with happy and workign Boopi again]
