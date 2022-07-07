Same things from different universes

In the previous chapter, we created two toys for Jessie's friends. Each of these toys was created and committed to a separate branch. In order for commits with instructions for toys to appear in the `master` branch, we had to merge each branch into `master`. So, Boopi was able to create toys for these cuties.

But what if we could create instructions for the same toy in parallel and merge them together? What would happen? What would happen if things from two universes appeared in one? Let's figure it out!

To do this experiment, we will create an apple for Boopi in two separate branches.

Woof-woof!

I know Jessie, Boopi doesn't like apples. But let's create them anyway.

[Image with the strange face of boopi and Jessie looking on each other]

Firstly off, we have to be on the `master` branch. Secondly, we will create a new branch called `red-apple` and jump into it.

```
git branch red-apple
git checkout red-apple
```

Let's create a file and call it `apple.txt`

Open the file and put the following instruction inside it.

```
Step 1. Create a red apple
```

Save the file and close it.

At this moment, we should be on the `red-apple` branch with one new (untracked) file called `apple.txt`.

Let's commit `apple.txt` file with instructions inside of it

```
git add apple.txt
git commit -m "Add file with instructions of how to create a red apple"
```

Good. At this point, we created a file with instructions and committed it to the `red-apple` branch.

Let's switch to the `master` branch and do the same things.

```
git checkout master
```

After switching to the `master` branch, let's create an `apple.txt` file and pass those instructions inside it

```
Step 1. Create a green apple
```

Save the file and close it.

Woof-woof! 

Yes, Jessie, I know. We have just created an apple in a different color than the one we created in the `red-apple` branch. But I will explain it later. For now, let's continue and commit the file.

Let's create a commit on the `master` branch and add an `apple.txt` file to it.

```
git add apple.txt
git commit -m "Add file with instructions of how to create a green apple"
```

We done! Now we should have a new commit on the `master` branch. Before we merge `red-apple` branch into it, let's try to predict what might happen:

1. The `apple.txt` file from `red-apple` branch will replace `apple.txt` file in the `master` branch (current).
2. The `apple.txt` file on the `master` branch will not be replaced and remains untouched.
3. The `apple.txt` file will contain instructions from both branches (e.g. they will be merged)
4. Black hole

None of the above options are correct. Let's figure out what will happen

Woof-woof! I know Jessie, you know what will happen, but let our reader go through this on his own.

As far as we are already on the `master` branch, let's merge the `red-apple` branch into it.

```
git merge red-apple
```

[Jessie narrowed her eyes]

Oh, no! What just happened?

Let's see what the console message says.

```
Auto-merging apple.txt
CONFLICT (add/add): Merge conflict in apple.txt
Automatic merge failed; fix conflicts and then commit the result.
```

You may notice the word in capital letters - `CONFLICT`. It is exactly what happened - a merge conflict. Merge conflicts are the most common problem of newbies who start to work with Git. But don't be scared. Jessie and I will try to explain when they happen and how to resolve them.

Yes, Jessie? Woof-woof! Alright!

If you run the `git status` command and investigate the result message, you may notice that Git says that you have "unmerged paths", and under "Unmerged paths:" message, there is an `apple.txt` file marked as "both added". 

````
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
both added: apple.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

It is exactly what happened. Two branches were trying to add an `apple.txt` file, but there are conflicts inside this file. If we open the file with your favorite editor, you may notice that the file contains something more than the instructions of both files.

```
<<<<<<< HEAD
Step 1. Create a green apple
=======
Step 1. Create a red apple
>>>>>>> red-apple
```

The first lines says that everything starting from `<<<<<<< HEAD` till `=======` belongs to one file, and everything after `=======` and until `>>>>>>> red-apple` belongs to the another one.


But what does all this mean? This means that during the merge process, when Git tried to automatically merge files (that is exactly what happens under the hood when we write a `git merge` command) and their internals from different branches, it could not decide on its own which change to apply.

When Git does not know what changes to apply, he asks a developer to help him. So now, you as a developer must help him to make a decision. It is easier than you may think.

All we need to do is to leave those changes that we're interested in. If we created two apples with different colors, we must decide what apple in what color to leave. Also, instead of creating a single apple, we could create two apples on two different steps, for instance

```
Step 1. Create a green apple
Step 2. Create a red apple
```

As you can see, there are many options of what to do with the conflicts, and only a developer may know what exactly to do. So instead of creating two apple let's leave a single instruction with a green apple, for example

```
Step 1. Create a green apple
```

Save changes and close the file.

If we go back and find the message that was shown in the console after CONFLICT arised, you may notice the instructions

```
...; fix conflicts and then commit the result.
```

We fixed conflicts. The last step that we need to do is to create a commit

Let's add an `apple.txt` file to the staged area

```
git add apple.txt
```

and make a commit

```
git commit
```

It should open a default editor with a predefined message.

```
Merge branch 'red-apple'
```

We can leave it as is and close the file.

Well done! You solved your first conflict!

Look at Boopi! Ah-ha! 

[Image of Boopi crafting an apple]

As you remember, don't forget to remove branches that you will not use anymore. It is a good practice to keep your repository in a clean state.

```
git branch -d red-apple
```

We passed the scariest part for newbies, and it was fun, wasn't it? 

Woof-woof!

Let’s continue








