Make a surprise for Boopi

[Image of Jessie with conus on top of her head]

Woof-woof. Yes, Jessie? Woof-woof. Ah, How could I forget! Jessie said that Boopi has a birthday today, let's make a gift for him. We can create a big cake for him. To make a surprise for Boopi, we will create a cake in another branch.

So, let's create a new branch called "cake" where we prepare instructions on how to bake it!

```
git checkout -b cake
```

This is a shortcut for creating a new branch and making it active (selected). It would be the same as if we could create a branch and make it active in two separate steps.

```
git branch cake
git checkout cake
```

Our cake will consist of several parts: dough, jam, and cherry on top of it. Let's create files for each of these parts and write instructions for them.

First off, we will provide instructions for the dough. Let's create a file with the name `dough.txt`.

Open this file and provide instructions inside.

```
Step 1. Knead the dough
Step 2. Wait until the dough rises
Step 3. Bake until delicious
```

Save the file and close it.

Secondly, create another file called `jam.txt`

Open this file and provide instructions inside.

```
Step 1. Crush ripe cherries
Step 2. Add sugar
Step 3. Stir
```

Save the file and close it.

So, next...

Woof-woof! Yes, Jessy? Woof-woof-woof. It can't be! One of Jessie's friends falls into the water, and we need to help him. But we need a lifebuoy! Where do we get it? Woof-woof. Of course! Boopi can craft it for us. Let's craft it!

But wait, we're creating a cake for Boopi. If we switch to the `master` branch, all the files with instructions that we created so far will be moved to the `master` branch. This will create confusion along with the problems that we have right now! Do we have any commands in Git that could help us solve this problem? Woof-woof! That's right, Jesse. Of course, we have! We can use the `git stash` command.

Let's use it!

Before we use this command, you can think of stashing as a process of moving modified or untracked files out of your project into a place where Git can hold them for a while. In the end, you will be able to get those files back when you need them. This is just what we need right now

```
git stash —include-untracked
```

Please note that we used `—include-untracked` flag. This flag is required in our case because we only created files and didn't ask Git to track our files by `git add` command. Thus, to ask Git to take care of files it doesn't really care about, we must explicitly set this property. If we added those files to the staged area with `git add`, we could omit this flag.

Check your folder. The `jam.txt` and `doubt.txt` files should have disappeared. You successfully stashed them. We will return them soon, but firstly let's rescue Jessie's friend!

Now we need to create a new branch called `lifebuoy`. But remember that we need to take into account which branch we are branching off from. In this case, it doesn't matter, but in most cases, we want to branch from the branch we want to apply changes to later.

Let's switch to the `master` branch and create a new branch based on it.

```
git checkout master
git checkout -b lifebuoy
```

Let's verify that we're on a new branch by writing. 

```
git branch —show-current
````

It should print `lifebuoy`

Good. Let's create a file, `lifebouy.txt`.

Open it and provide instructions.

```
Step 1. Create a circle with a radius of 20 cm
Step 2. Paint it in orange and white colors
Step 3. Add rope around the circle
```

Save the file and close it.

Let's create a commit

```
git add lifebouy.txt
git commit -m "Add lifebouy.txt"
```

At this point, we could push this branch to the remote. Then create a pull request, verify that everything is correct, and commit them. Or, if there were any errors in it, we could add a new commit with fixes. Then review it again and only then confirm and merge. But now we do not have time for this, we must help Jessie's friend as soon as possible. Let's just go back to the `master` branch.

```
git checkout master
```

and merge our `lifebuoy` into it

```
git merge lifebuoy
```

The `git merge` command tells Git to take all the unique commits from the "lifeline" branch and copy them to the `master` branch if there are no conflicts.

Oh, look at Boopi! Woof-woof! Yes, good job Boopi! Jessie, show us where we need to go. Let's gooo!

[Image of running Jessie and Boopi to the Jessie's friend with lifebuoy]

I see him, throw it there Boopi! Take a `lifebyoy` friend!

[Image of rescuing the dog where he is in water]

Good job, Boopi! Here we go! What is your name, little fluffy? Woof-woof. Ah, Bobi, nice to meet you. It's reader, boopi and Me. Next time be careful  please! 

While Jessie and Boopi sitting with Bobi we can take the last step and finish our cake.

Let's switch back to the branch `cake`

```
git checkout cake
```

At this moment, files should not exist here, that's correct because we asked Git to stash them!

We can actually check if our files are still in the stash by running

```
git stash —list
```

It should show a single record with our files. Instead of showing our files it shows the record which holds our files.

Let's bring our files back by using 

```
git stash pop
```

This command will take the latest record from the stash and apply it (or in other words returns your stashed files back). In general, we can stash as many times as we want. All our files will be stored in the stack structure. Where the latest stash stores on the top. If we want to bring it back we can either specify a id of the record or take the latest one from the stash. As far we stashed only once and our record is the only record on the stack we could simply use `git stash pop`.

Let's write `git status` and ensure that Git returned our files.

```
git status
```

Yes, it shows that `jam.txt` and `dough.txt` are untracked files as we had before. 

So, let's create the missing part of the cake by creating a `cherry.txt` file and providing instructions inside it

Open the file and provide instrucitons

```
Step 1. Create a cherry
```

Save the file and close it.

At this moment, we have three files: `jam.txt`, `dough.txt` and `cherry.txt`. Let's add them to the staged area and commit them

```
git add .
```

Note: We could specify each files explicitly by listing them like `git add dough.txt cherry.txt jam.txt` but we took a shorter version. Where . (dot) means all untracked and modified files.


The last thing that we can do is to create a commit. Usually we create commits with a single title, but we would like to add congratulations for Boopi.

git commit 

It should open your already familiar window inside your default editor.

By convention, Git expects the first line to be used as the title, and all other lines starting from the third as the description. An empty line between the title and description is required to distinguish between them.

Let's give it a title on the first line. 

"Surprise" 

and after skipping the empty line, write our congratulations

Happy birthday Boopi! Be cool as always!

Sincerely,
Jessie, Author and Reader

Okay, save changes and close the file.

Let's switch back to `master` and merge this branch into it.

```
git checkout master
```

Woof-woof. I know, I know Jessie. We're back. Hold on. Dear Boopi, we know you so long, and also we know that you have a birthday today. So, we prepared a surprise for you. 

Reader, do the last thing that you have to do.

```
git merge cake.
``

This, tsss. HAPPY BIRTHDAY!

[Image of Boopi holding a cake and Jessie jumping arround and confetti]


