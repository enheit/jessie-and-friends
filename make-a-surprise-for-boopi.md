# Make a surprise for Boopi

Impressions: 5/5

Note:

---

[Image of Jessie with conus on top of her head]

Woof-woof. Yes, Jessie? Woof-woof. I remember, Jessie, that Boopi has a birthday today. Are you thinking about what I am? Let's make a gift for Boopi!

Woof! Exactly! We can create a big cake for him. But wait. 

How we can prepare instructions for the cake and without ruining the surprise.

Woof-woof! Good point, Jessie, we can create a cake in another branch. Let's do this.

So, let's create a new branch called "cake" where we prepare instructions on how to bake it!

```
git checkout -b cake
```

We have not used this shorter form of creating a branch before. Let's understand what it does. Actually, this command consist of two parts: create a new branch and switch to it. 

It would be the same as if we could create a branch and make it active in two separate steps.

```
git branch cake
git checkout cake
```

Now that this is clear, let's get back to our cake.

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

Woof-woof! Yes, Jessy? WOOF-WOOF-WOOF!!! It can't be! One of Jessie's friends falls into the water, and we need to help him. But we need a lifebuoy! Where do we get it? Woof-woof. Of course! Boopi can craft it for us. Let's craft it!

But wait, we're creating a cake for Boopi. If we switch to the `master` branch, all the files with instructions that we created so far will be moved to the `master` branch. In the best case, Boopi will know that we are preparing a surprise, and in the worst case this will create confusion along with the problems that we have right now! Do we have any commands in Git that could help us solve this problem? 

Woof-woof! That's right, Jesse. 

Of course, we have! We can use the `git stash` command.

Let's use it!

Before we use this command, you can think of stashing as a process of moving modified or untracked files out of the project into a place where Git can hold them for a while. This place is not visible neither for us nor for Boopi. In the end, we will be able to get those files back when we need them. This option suits us! What we need to do?

Nothing much. We need to write the following command in already opened console

```
git stash —include-untracked
```

Usually, we can use `git stash` without `--include-untracked` option. But as far we didn't add our files to the staged area (that is, didn't use `git add` on them) yet, we need to provide an additional option that asks Git to hide even files that Git doesn't didn't care about.

Check your folder. The `jam.txt` and `doubt.txt` files should have disappeared. It means that you successfully stashed them. We will return them soon, but firstly let's rescue Jessie's friend!

Now we need to create a new branch called `lifebuoy`. But remember that we need to take into account which branch we are branching off from. In this case, it doesn't matter, but in most cases, we want to branch from the branch we want to apply changes to later.

Let's switch back to the `master` branch and create a new branch based on it.

```
git checkout master
git checkout -b lifebuoy
```

Let's verify that we're on a new branch by writing. 

```
git branch —show-current
````

It should print `lifebuoy`

If everything is correct, we can create a file, `lifebouy.txt`.

Open this file and provide instructions.

```
Step 1. Create a circle with a radius of 10 cm
Step 2. Paint it in orange and white colors
Step 3. Add rope around the circle
```

Save the file and close it.

Our instructions are ready! Let's create a commit and give it to Boopi as soon as possible

```
git add lifebouy.txt
git commit -m "Add lifebouy.txt"
```

Nice! Let's move back to `master` and merge it

```
git checkout master
git merge lifebuoy
```

The `git merge` command tells Git to take all the unique commits from the "lifeline" branch and copy them to the `master` branch if there are no conflicts.

Oh, look at Boopi! Woof-woof! Yes, good job Boopi! Jessie, show us where we need to go. Let's gooo!

[Image of running Jessie and Boopi to the Jessie's friend with lifebuoy]

I see him, throw it there Boopi! Take a `lifebyoy` friend!

[Image of rescuing the dog where he is in water]

Good job, Boopi and good job everyone! Here we go! What is your name, little fluffy? Woof-woof. Ah, Thomas, nice to meet you. This is reader, Boopi and Me. Nice to meet you. Next time be careful please! 

While Jessie and Boopi continue to sit with wet Thomas we can go back and finish our surprise for Boopi. But shhh! Boopi suspects nothing!

Let's quietly switch back to the branch `cake`

```
git checkout cake
```

At this moment, files should not exist here, that's correct because we asked Git to stash them!

Ahem. Why am I still whispering!

We can actually check if our files are still in the stash by running

```
git stash list
```

It should show a single record with our files. 

```
stash@{0}: WIP on master: db42838 Add README.md // TODO: Replace this example with a real one
```

Instead of showing our files it shows the record which holds our files.

Let's bring our files back by using 

```
git stash pop
```

This command will take the latest record from the stash and apply it (or in other words returns your stashed files back). In general, we can stash as many times as we want. All our files will be stored in the stack structure. Where the latest stashed files will be stored on the top of it. If we want to bring it back we can either specify a id of the record or take the latest one from the stash. As far we stashed only once and our record is the only record on the stack we could simply use `git stash pop`.

```
git stash pop
```

Let's write `git status` and ensure that Git returned our files.

```
git status
```

Yes, it shows that `jam.txt` and `dough.txt` are untracked files as we had before. 

```
On branch cake

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	dough.txt
  jam.txt 
  

nothing added to commit but untracked files present (use "git add" to track)
```

Okay, our two of three files are ready. Let's create the missing part of the cake by creating a `cherry.txt` file and providing instructions inside it

Open the newly created file `cherry.txt` and provide instrucitons inside it

```
Step 1. Create a cherry
```

Save the file and close it.

As a result, we should have three files: `jam.txt`, `dough.txt` and `cherry.txt`. Let's add them to the staged area and create a commit

```
git add .
```

This is another shortened version of how to add files to the staged area. The `.` (dot) means add all files to the staged area. We could achieve the same result by manually specifying each file (e.g. `git add jam.txt dough.txt cherry.txt`), but it doesn't change the point.

The last thing that we need to do is to create a commit with all three files. We usually create commits with a short title, but today is Boopi's special day, let's add congratulations to him.

By running the following command

```
git commit
```

Git should open your already familiar window inside your default editor

On the first line, we will put a title

```
Surprise
```

We will skip the second line, and on the third we will put our congratulations for Boopi

```
Happy birthday! We hope all your birthday wishes and dreams come true

Sincerely,
Jessie, Thomas, Reader, Athor and others
```

The full commit message should look like this

```
Surprise
                
Happy birthday! We hope all your birthday wishes and dreams come true

Sincerely,
Jessie, Thomas, Reader, Athor and others
```

Okay, save changes and close the file.

Let's switch back to `master`

```
git checkout master
```

Woof-woof. I know, I know Jessie. We're back...

Dear Boopi,

birthdays are a new start, a fresh beginning and a time to pursue new endeavors with new goals. Move forward with confidence and courage. You are a very special person. May today and all of your days be amazing!

Reader, do the last thing that you have to do.

```
git merge cake
```

HAPPY BIRTHDAY!

[Image of Boopi holding a cake and Jessie jumping arround and confetti]


