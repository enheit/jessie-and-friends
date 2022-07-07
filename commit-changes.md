Commit changes

In the previous chapter, we added `tennis-ball.txt` file to the staged area, thus saying that we are ready to commit it.

To make a commit, we need to use the already known `git commit` command. Previously, we tried to make a commit, but we didn't select any file and Git showed us an error message. Now, we have one file selected, and let's see what happens next.

```
git commit
```

After running these command the default editor should be opened with this content

```

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   newfile.txt
#
# Changes not staged for commit:
#       modified:   newfile.txt
#
```

If you read those text you will notice that git commit contains the information of the current status of the project and the message above

```
 Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
```

It means that we need to provide a review of what we have done. Usually, one line of description is enough.

So, let's put the cursor on the first line and write the description.

NOTE: Before adding any information I should mention that usually Git uses Vim as a default editor. You would ask me why I have to make attention on it. Because Vim has special unique features. One of those features that you are not able to write text directly. By default, when you open Vim, it goes with `Normal` mode where each key has special meaning. `w` jumps to the start of the word, `e` jumps to the end of the word and `i' is turns `Insert mode`. Insert mode where each key becomes a regular key as we would expect. So let's press it. The `--INSERT--` word should be shown at the left bottom of the screen. After adding the text message below, you need to press `:` and write `wq` (w - write, q - quite) to save changes. 

```
Add file with instructions of how to create a tennis ball
```

After writing the commit message close the editor. If a commit was created, the following message should be shown in the console

```
[master (root-commit) e6d979b] Add file with instructions of how to create a tennis ball
 1 file changed, 1 insertion(+)
 create mode 100644 tennis-ball.txt
```

It confirms that new commmit was created.

Note: You see that we write it like "add.." not "added…". In general, Git users give a name to a commit in the imperative form to describe what this commit does. For instance, (this commit) "Add new line", (this commit) "Remove the line" or (this commit) "Modify the line". But this is a convention only. You can provide any title you want.

Good. After success, commit git started stores the files that were included in commit inside his own "internals". In our case this is the only `tennis-ball.txt` file.

Oh my gosh… What's going on… Boopi starting to craft something. Woof-woof! Look at Boopi! Woof-Woof! This is a tennis ball! Thank you, Boopi, and Thank you, reader! Now Jessie has a new tennis ball!

Do you like it Jessie? Woof! Aliright!

Let's make a quick recap of what we have learned.

We learned that to start to use git commands inside our folder, we had to intitialize Git first, by usng `git init` command. It created a hidden `.git` folder inside our project folder where Git stores project files and their changes inside it. By default, Git doesn't add these files to the `.git` folder automatically. We need explicitly add them by using `git commit`. Before creating a commit we have to decide what files will be included in the commit and select them by using `git add` command. After we added this file to the staged area. Git created a snapshot of this file and it's internals and does not allow to change it. If we make some changes to our file we need manually to add them by repeating `git add` command. If changes that were made after `git add` has to be removed we can use `git reset` command. And finally when files are ready to be commited we can use `git commit` command which will open a default editor to provide a description of the commit. After creating a message and closing the editor the commit will be added to the Git and our files will be tracked by Git. Even if we remove some internals of the file or remove it at all Git will notice those changes and let us know if we run `git status` command.


