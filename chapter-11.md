# Chapter 11: Create toys for Jessie’s friends in different branches

![Lucy and Thomas. Jessie's friends](./images/chapter-11.jpeg)

Woof-woof! Yes, Jessie? Oh, who is it? Woof-woof-woof! Ah, it’s your friends? Woof. Hi friends, it’s me, reader and Boopi; nice to meet you. Woof-woof! Jessie said that her friends saw her playing with a tennis ball and wanted toys to play with them too. What a great idea. It would be nice to make some more toys for friends, what do you think, reader and Boopi? 

Alright

Let’s create a rubber bone and flying disc for them. But before we start creating instruction files, let’s think about how we could do this. The easiest way would be to create two separate files for each toy, then provide instructions and commit two files together. Usually, putting different things inside a single commit is not a good practice. You can think of a commit as one atomic change. It makes our Git history clear and our commits independent of each other. So, if we start to follow these recommendations, we would create two different files and put each of those files into a separate commit. Much better. Each commit will contain unique atomic changes that can be easily read and created by Boopi.

But let’s think if we had more than two files. Suppose Jessie comes not with two of her friends but a hundred. We would need to create a hundred files and make each commit for them. It would create a mess in our folder. It would be painful to navigate between tons of untracked files and jump between them if needed. As you may have noticed, I’m taking you to a new feature in Git called branches.

So, what branches are? You can think of branches like a separate “universe” in your folder. You can create “universes”, jump between them and remove them if you want. Each of those “universes” has different folders, files, and commits. It sounds a lot more complicated than it really is. So, let’s create our first “universe” a.k.a branch.

I expect your console to be open inside your folder and wait for new commands to execute.

To create a new branch, we need to use `git branch` command with the name.

```
git branch rubber-bone
```

After running this command, Git must create a new branch in your folder. You may notice that no messages appeared in the console. It’s correct. We have just created a branch named `rubber-bone`. To confirm that we can run another command

```
git branch --list
```

It should list all existing branches in your project.

```
master
rubber-bone
```

You may wonder why `git branch --list` returned two branches instead of one? Good question. The `master` (or `main`, `thunk`) is the standard branch that is created along with the initialization of the project. Remember we started our project with `git init` command? At that moment, Git created a default branch called `master`. Moreover, when we created the tennis ball and made a commit, that commit was added to the `master` branch. I didn’t mention it earlier because it wasn’t necessary to know. Now, when we created a new branch, we are still on the `master` branch. We can verify it by running this command

```
git branch --show-current
```

It should print `master`. By default, when you create a branch, Git does not automatically switch to it. Instead, it creates it in the background and lets you switch to it later.

To switch to a newly created branch, we need to run one more command and provide the name of the desired branch. In our case, it should be `rubber-bone`

```
git checkout rubber-bone
```

After running this command you may notice a message in a console

```
Switched to branch 'rubber-bone'
```

It means that we have successfully switched to a new branch. Let’s verify it by running an already known command.

```
git branch --show-current
```

If we did everything correctly, this should show the `rubber-bone` name in the console.

After creating a new branch and switching to it, we can finally create a file and provide instructions inside it.

Let’s create a file called `rubber-bone.txt`

Open the file and write the following.

```
Step 1. Create a rubber
Step 2. Shape into a bone
Step 3. Color is red
```

Save the file and close it

Good. Now we have a new untracked file. Let’s make a commit

As you remember, before making a commit, we need to specify what files will be included inside the commit. To do this, we will use the already known command `git add`

```
git add rubber-bone.txt
```

After running `git status` we can verify that our `rubber-bone.txt` has been added to the staged area.

The final step that we need to do is to create a commit.

Previously, when we created a commit for `tennis-ball.txt`, we used `git commit` command without attributes. It opened the editor where we could specify the commit message. There is a shorter way to provide a commit message without opening any text editor. 

Let’s see how we can achieve this.

```
git commit -m "Add a file with instructions on how to create a rubber bone"
```

As you can see, we have added the `-m` attribute with our commit name enclosed in double quotes.

Okay, we created a file with instructions and made a commit. Why doesn’t Boopi create an item?

Remember that I said that creating a new branch creates a new “universe” where our files and folders will live? That is exactly what happened. Boopi remained in the previous branch `master`, but we are on the `rubber-bone` branch now. It means that Boopi doesn’t have access to the files and folders that were created on the different branches. How we can pass these files, or in our case, a file to the Boopi?

Good question.

To move the file to the `master` branch, we need to merge two branches into one. In other words, you can think of it as merging two universes. Everything that exists in one universe will collide with another universe. But instead of creating a new universe, it continues to exist in one of those universes. How can we decide what universe will preserve changes of both? It depends on what universe we are pouring changes into. It may sound complicated, but in reality, it is nothing more than just saying, “You must merge into me.”

Let’s do this.

Before merging our “universes” let’s verify that our commit exists by running `git log` command in our `rubber-bone` branch.

```
hint: git branch -m 
commit 9a7a6d46785732d976813088c55e080db3948166 (HEAD -> rubber-bone)
Author: Roman Mahotskyi 
Date: Tue Jul 12 02:33:17 2022  +0300

Add a file with instructions on how to create a rubber bone

commit a81dce30f016ee639b4ec62dbfb5c25655697f13 (master)
Author: Roman Mahotskyi 
Date: Tue Jul 12 02:32:16 2022 +0300

Add a file with instructions on how to create a tennis ball
```

Hah. Have you noticed that `git log` printed two commits instead of one? It printed `“Add a file with instructions on how to create a tennis ball”` as well as our commit with a rubber bone. But how is it possible? We are on the `rubber-bone` branch, and can still see commits from another “universe”? 

Yes.

I didn’t mention this before because it would make it harder to describe the branches. But in general, there is nothing special. Whenever you create a new branch in your project, the newly created branch will be based on the current state of the active branch. It means that on the moment when we used a `git branch rubber-bone` Git created a new branch with all commits of the `master` branch and “put it” into a newly created branch - `rubber-bone`. 

Therefore, when you run the `git log` command, you see the commits from the current branch and previous commits of the branch that you were based on. If we could visualize this, it would look like the following picture.

![Two lines which represent branches: master and rubber-bone](./images/chapter-11-branching.jpeg)

I hope it makes sense to you now.

So far, we created a single commit on the `rubber-bone` branch with instructions on how to create a rubber bone toy. But it doesn’t help Jessie’s friends to start to play with toys yet. Let’s take a few more steps in this direction and create a missing flying disc.

At this moment, we have an unmerged branch with a rubber bone toy, we need to create another branch and create a flying disc there.

Let’s do this but with fewer explanations.

Let’s switch back to the `master` branch (without merging).

```
git checkout master
```

Run `git log` and verify that the commit from the `rubber-bone` branch didn’t leak to the `master` branch.

Good. The `git log` command should show the only commit with a tennis ball.

Let’s create a new branch called `flying-disk` based on the `master`

```
git branch flying-disc
```

And switch to the branch

```
git checkout flying-disc
```

Let’s verify that we’re on the new branch

```
git branch --show-active
```

It should print the `flying-disc`

If we run the `git log`, it also should show the commit with the tennis ball because, as I said earlier, newly created branches are always based on the state of the currently active branch. In our case, we based on the `master` branch where a commit with a tennis ball was already created.

Let’s create a new file called `flying-disc.txt` and add instructions inside it.

Open the file and provide the following instructions.

```
Step 1. Create a circular object
Step 2. Make it thin
Step 3. Color it blue
```

Save changes and close the file.

Let’s make a commit with this file

```
git add flying-disc.txt
git commit -m "Add a file with instructions on how to create a rubber bone." 
```

Good. We just created another commit of the instructions for the flying disc. Let’s verify that commit was added to the history by running `git log` command.

```
git log
```

Hold on. It shows the incorrect message, `“Add a file with instructions on how to create a rubber bone.”`, but we provided instructions on creating a flying disc.

What can we do? Is there any command that can help us to modify existing commits? Of course, there is.

Git provides us a possibility to amend existing commits. If we accidentally committed a wrong file, or we forget to add something to the commit, or we made a mistake in the name of the commit, all of these problems Git allows us to fix.

There are many approaches to modifying the existing commit, but we will use one of them.

Inside your console, write the following.

```
git commit --amend
```

It must open the text editor with the commit message of the latest commit.

```
Add a file with instructions on how to create a rubber-bone

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Tue Jul 12 18:52:01 2022 +0300
#
# On branch flying-disc
# Changes to be committed:
#       new file:   flying-disc.txt
```

It is exactly what we needed. Our latest commit on the `flying-disc` branch contains the commit with the wrong title description.

In the opened text editor, let’s change the commit message to `“Add instructions on how to create a flying disc”`. All we need to do is to replace `“rubber bone”` with a `“flying disc”`.

Save the file and close it.

If we have done everything correctly, Git should replace the old wrong commit message with a new one.

We can verify it by running `git log -1`

```
git log -1
```

Yes, our commit message has the correct description.

```
commit 5f21d4e852c19a65b9ebcce8e1761f84248b2778 (HEAD -> flying-disc)
Author: Roman Mahotskyi 
Date: Tue Jul 12 18:52:01 2022 +0300

Add a file with instructions on how to create a rubber-bone
```

Good job. We just fixed an incorrect commit message and finally can merge our instructions from both branches into the `master`.

You must remember that merging is colliding two “universes”. To collide the `master` branch with two other branches, we need to go back to the `master` branch and specify what branch we want to “collide into us”.

Let’s back to the `master` branch

```
git checkout master
```

The final step is to ask Git to merge (collide) another branch into the current. We can achieve this by running the next command.

```
git merge rubber-bone
```

Nice. Look at Boopi. It crafts a rubber bone! Good job, reader!

Let’s see what happened with our commit history.

```
git log
```

As you can see it shows us two commits. The first commit was created on the `master` and the second one on `rubber-bone` branch (from bottom to top). In the end, they were merged and stored on the `master` branch.

```
commit 6661ee1676f17f3a7e89ef41b6ae21d36d5fdf52 (HEAD -> master, rubber-bone)
Author: Roman Mahotskyi 
Date: Tue Jul 12 18:57:19 2022 +0300

Add a file with instructions on how to create a rubber bone

commit b15d1b743fcde3c1fcd26880c7159451f2c2eb3e
Author: Roman Mahotskyi 
Date: Tue Jul 12 18:57:00 2022 +0300

Add a file with instructions on how to create a tennis ball
```

You can open a folder and verify that the `rubber-bone.txt` file has been added to the folder.

Nice! We successfully merged our first branch!

Woof-woof! Yes, Jessie? Woof-woof! Ah, how could we forget? We didn’t merge the toy for another Jessie’s friend — a flying disc! Let’s do the same steps that we did with the `rubber-bone` branch.

To merge the remaining branch, we can run the following command

```
git merge flying-disc
```

At this moment, it should open a text editor with the default merge commit message. 

```
Merge branch 'flying-disc'
# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```

You can either change the message or leave it as is. In this case, we leave it as it is because it accurately describes what we are doing.

You may ask why Git didn’t ask us to provide a commit message when we merged the `rubber-bone` branch? Are there any differences in these branches (`rubber-bone` vs `flying-disc`)? No, two branches are equal in a way we created them and merged. The difference is only in the order of their merging. 

Before Git merged `rubber-bone` into `master` it investigated the history of commits of two branches. If the history of these branches is linear, that is, the master didn’t receive any commits after the `rubber-bone` branch was created, then merging such branches does not raise any issues in Git. Such merging technique is called - fast-forwarding. It’s a fancy word to describe that the history after the merge remains linear. But, when we tried to merge a `flying-disc` into `master` it opened an editor with a default merge commit message. After providing a merge commit message and closing the editor a technical commit should have been created. This technical commit is called - a merge commit. It explicitly shows us in the Git history (`git log`) that merge has happened in this place. When a technical commit is created in history, our history is no longer linear, because there is more to it than just our commits.

Even if this description was not enough to understand the difference, I recommend you not spend much time on it. Because neither fast-forwarding nor additional merge commit doesn’t really matter when you learn Git. Git has a lot of settings and nuances that help us to work more efficiently, but this efficiency is not a goal of this book. Let’s go back to crafting things!

Look at Boopi! It creates a flying disc!

Woof-woof!

Nice! We merged another branch into our `master`. Now our history of the `master` branch should consist of commits from two other branches.

Since everyone received the toys and was happy, we can do the last but not the least thing - remove unused branches.

Usually, branches have a limited lifetime. They make sense only during the development process. Once you’ve finished working on a branch (as we did) and merged it into another branch, it rarely remains useful the rest of the time. It is a good practice to remove them.

To not guess what branch was already merged into the current active branch we can use another useful Git command

```
git branch --merged
```

It should show the list of all branches that were already merged into the current one.

> NOTE: It includes the currently active branch (it is marked with an asterisk `*`). Don’t delete it by accident.


After reviewing the list of merged branches, we can remove them.

```
git branch -d rubber-bone
```

It should remove the `rubber-bone` branch, and

```
git branch -d flying-disc
```

It should remove the `flying-disc` branch.

Good job. Now we don’t have “zombie” branches on our computers. We can verify it by running

```
git branch --list
```

As you can see, it again shows only the `master` branch.

Woof-woof! Yes, Jessie, I see! You are all happy to play with your toys! Say thanks to the reader and Boopi without them this would not be possible! You can keep having fun with newly created toys, but we need to keep learning Git! 

Let’s move on to the next challenge!
