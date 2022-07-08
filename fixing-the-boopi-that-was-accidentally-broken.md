# Fixing the Boopi that was accidentally broken

Impressions: 4.9/5

Note:

 - Maybe, replace the name of banana.txt file with something else. Something like `bad-instructions.txt`

---

As we remember, every time a commit appears in the history on the `master` branch, it signals Boopi to start to craft things. But what if we accidentally commit the file that does not contain instructions for Boopi. Will Boopi understand how to handle it on his own? Or will hi break? Let's figure out what happens. 

Let's create a file called `banana.txt` and put something inside that Boopi does not know. 

Let's open an `apple.txt` file and write the following.

```
Step -1: abcdefg
```

Save the file and close it.

As you can see, we created a step with a negative number (-1), and also added Latin characters, which makes no sense for Boopi. At least we can assume that this characters are something that Boopi will not understand.

Now, let's commit this file.

```
git add banana.txt
git commit -m "Add banana.txt"
```

Commit was created. Let's see what happened with Boopi

Boopi, can you hear us? If yes, give us a sign!

Woof-woof!

Oops, looks like we broke Boopi

[Image of broken Boopi after executing invalid instructions]

As you may have noticed, we did it on purpose. I would never ask you to do something that would totally broke Boopi or anyone else. So let's think about what we can do to bring Boopi back to "life".

How can we undo the instructions that we gave to Boopi? The simplest solution would be to remove the file that we committed. That is, remove the file in our folder and create a new commit (e.g. "Remove banana.txt file"). 

Instead of doing it manually, Git has a special command that can do it for us. The name of the command is `git revert`. 

Whenever you make a commit that doesn't work as expected, you can use a special `git revert <commit_hash>` command to roll back those changes. As you can see, it requires the hash of the commit. We can find this hash inside Git logs by running `git log` command. As far as we want to undo the lastest commit in our history, we can specify an additional `-1` parameter with `git log` command to prevent printing all the existing commits on the branch (except the latest one). Let's write it

```
git log -1
```

It should print the description of the lastest commit in our Git history

```
commit e6d979b1498e7d27cba0780e23c7bfbeca84790e (HEAD -> master)
Author: Roman Mahotskyi <roman.mahotskyi@gmail.com>
Date:   Tue Jul 5 19:14:41 2022 +0300

    Add apple.txt
```

Let's copy the hash on the first line of the log message. Yes, all these numbers and characters combined into a sequence of symbols is called a hash.

Now, we can write a revert command with already copied hash of the latest commit. (I remind you that this "latest commit" broked Boopi)

```
git revert e6d979b1498e7d27cba0780e23c7bfbeca84790e
```

It should open an editor with a default commit message. 

```
Revert "Add apple.txt"

This reverts commit e6d979b1498e7d27cba0780e23c7bfbeca84790e.
```

If you want, you can change this commit message and its description or leave it as is.

After saving changes and closing the editor, Git must automatically revert recently added commit. Or, in other words, Git must remove the `banana.txt` file with incorrect instructions.

We can verify this by opening the folder of our project.

It looks like the file with the bad instruction no longer exists. 

If you run a `git log -2` command again, you should notice that the commit where we have added an `banana.txt` file still exists in a history as well as a new commit with the message `Revert "Add banana.txt"`.

I know it's not what you expected. You might expect the `Add banan.txt` commit to disappear from the Git history. Or in other words, the history will be cleared of unnecessary commit. In our case that commit that broked Boopi.

But let's see what actually happened

Whenever you revert changes instead of re-writing the history and removing the existing commits, Git creates a new commit with mirrored changes. In our case, in that commit, we created a single file called `banana.txt` and added it to the commit. After running `git revert` Git removed this file for us and created a new commit with changes. If we didn't create the file but only made some changes to it, Git would remove those changes and create a new commit without removing a file.

I hope that it makes sense right now and you will be able to roll back any changes that could hurt your code base.

Woof-woof! Yes, it seems like Boopi is working again! Are you alright Boopi? 

Boop-boop!

Alright!

[Image with happy and workign Boopi again]

Let's move on to the next chapter where we will learn how not to break Boopi with files that were not made for him.
