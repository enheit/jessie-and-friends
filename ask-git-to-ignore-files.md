Ask Git to ignore files

But what to do if we want to create a file and not ask Boopi to craft it. We could create a new branch and create a file there, but after merging it back to the main branch, Boopi would craft it anyway. So, this is not the way to solve the problem. 

Woof-woof! Yes, Jessie. Good advice!

Jessie said there is a special file in which we can specify which files are not to track and not to add to the commit. If the file is not added to the commit, Boopi will not craft it. It is exactly what we want to achieve.

Jessie, do you remember the name of this "special" file?

Woof!

Ah, yea, this file is called `.gitognore`. Please notice that . (dot) at the start of the name is required.

Usually, `.gitignore` contains a list of files and folders that are excluded from the tracking area of Git. If you create a file with the name which is listed in this `.gitignore` this file will not be visible for `git status` or `git add` command.

Let's create this file with the name `.gitignore` inside our folder and open it.

Inside opened `.gitignore` file we will list all files that we want to ignore

```
apple.txt
banana.txt
```

Save and close the file.

By listing file names inside `.gitignore` we asked Git not to track those files, even though we write `git add .` or `git status`

Note: `git add .` is a shortcut to add all changed files to the staged area and after including them in the commit. In other words, instead of `git add apple.txt banana.txt watermelon.txt`, we can say `git add .` and all those files will be added without needing to specify them by one.

Let's save the file and create an `apple.txt` file. Open the file and provide some text inside.

```
I'm an apple.txt file
```

Save and close the file.

This file is created in our folder and visible to us. But this file is not "visible" for Git. Let's run `git status` and verify that Git doesn't say that we have a new untracked file called `apple.txt`.

```
git status
```

As you can see, `git status` doesn't say we created a new file. It means that `.gitignore` works as expected. So, in the future, if we want to ask Git not to track files, we can list them inside the `.gitingore` file. Furthermore, we can ask Git to ignore all files inside a specific folder, but this is not the goal of this chapter.


