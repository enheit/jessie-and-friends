# Intializing the Git inside the folder

Impressions: 3/5

Note:
 - Add more interaction with Jessie
 - Provide screenshots of initialized git as well as folder structure with hidden `.git` folder. It must improve understanding of what is going on.
---

When all the bureaucratic steps are done, we can finally initialize the Git inside our folder. To initialize Git inside our folder and make aware of our project, we need to run the next command.

```
git init
```

After running this command, Git should print hint messages to the console that propose you adjust the default configurations. We are not interested in changing anything, so we can skip it for now.

Let's check our folder. Has something changed? 

Yes, there are some changes in our folder, but they are not visible to us. After running the previous `git init` command, Git created a hidden folder called `.git` inside our folder, which will be storing all the information of our project, all created, renamed, and removed files as well as changes inside its files.

But if your OS doesn't show hidden files, the only file that should exist in your folder is `tennis-ball.txt` that we created previously, which contains instructions for Boopi. Speaking of Boopi, can he make us a tennis ball already?

Not yet!

Having initialized Git in our folder, we only said that in the future, we will use some Git commands inside this folder. By default, Git won't do anything unless we ask it to. That is, if we don't ask Git to pass the Boopi instructions, it won't do it itself.

So let's ask Git to pass instructions to Boopi

