---
title: Tracking Changes
teaching: 20
exercises: 10
questions:
- "How do I record changes in Git?"
- "How do I check the status of my version control repository?"
- "How do I record notes about what changes I made and why?"
objectives:
- "Go through the modify-add-commit cycle for one or more files."
- "Explain where information is stored at each stage of Git commit workflow."
keypoints:
- "`git status` shows the status of a repository."
- "Files can be stored in a project's working directory (which users see), the staging area (where the next commit is being built up) and the local repository (where commits are permanently recorded)."
- "`git add` puts files in the staging area."
- "`git commit` saves the staged content as a new commit in the local repository."
- "Always write a log message when committing changes."
---

(Lecture break: I'll do a talk-through of the general concepts behind Git-style version control before we come back to hands-on work here.)

First, let's make sure we're all in the subdirectory we want to work in:

~~~
$ pwd
~~~
{: .bash}

You should be in the subdirectory where you cloned your Git project.

Next let's create a file called `ToDo.txt` that contains some notes
about the conversion tools we want to make. (We'll use `nano` to edit the file,
but you can use whatever editor you like.)

~~~
$ nano ToDo.txt
~~~
{: .bash}

Type the text below into the `ToDo.txt` file. Remember to save and exit you can type `CTRL + O` (then enter) followed by `CTRL + X`.

~~~
Conversion functions needed:

- Dollars to Cents
- Gallons to Liters
- Hours to Minutes
~~~
{: .output}

`ToDo.txt` now contains several lines, which we can see by running:

~~~
$ ls
~~~
{: .bash}

~~~
README.md	ToDo.txt
~~~
{: .output}

~~~
$ cat ToDo.txt
~~~
{: .bash}

~~~
Conversion functions needed:

- Dollars to Cents
- Gallons to Liters
- Hours to Minutes
~~~
{: .output}

If we check the status of our project again,
Git tells us that it's noticed the new file:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master

Initial commit

Untracked files:
   (use "git add <file>..." to include in what will be committed)

	ToDo.txt
nothing added to commit but untracked files present (use "git add" to track)
~~~
{: .output}

The "untracked files" message means that there's a file in the directory
that Git isn't keeping track of.
We can tell Git to track a file using `git add`:

~~~
$ git add ToDo.txt
~~~
{: .bash}

and then check that the right thing happened:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   ToDo.txt

~~~
{: .output}

Git now knows that it's supposed to keep track of `ToDo.txt`,
but it hasn't recorded these changes as a commit yet.
To get it to do that,
we need to run one more command:

~~~
$ git commit -m "Start notes on conversion tools"
~~~
{: .bash}

~~~
[master (root-commit) f22b25e] Start notes on conversion tools
 1 file changed, 5 insertion(+)
 create mode 100644 ToDo.txt
~~~
{: .output}

When we run `git commit`, Git takes everything we have told it to
 save by using `git add` and stores a copy permanently inside the
  special `.git` directory. This permanent copy is called a '`commit`'
 (or '`revision`') and its short identifier is `f22b25e`
 (Your commit will have another identifier of similar length.)

We use the '`-m`' flag (for "message") to record a short, descriptive,
 and specific comment that will help us remember what we did and why.
 If we just run `git commit` without the `-m` option, Git will launch
 `nano` (or whatever other editor we configured as `core.editor`)
 so that we can write a longer message.

[Good commit messages][commit-messages] start with a brief
 (<50 characters) summary of changes made in the commit.  If you want
 to go into more detail, add a blank line between the summary line and
 your additional notes.

If we run `git status` now:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
~~~
{: .output}

it tells us that our local repository is now differing from the
origin (the repository from which we cloned this one, i.e. the original repository in Github)
by one commit.

It also tells us that we can use the `git push` command to send our commit to the original repo in 
Github to synchronize these two repositories.

If we want to know what we've done recently,
we can ask Git to show us the project's history using `git log`:

~~~
$ git log
~~~
{: .bash}

~~~
commit f22b25e3233b4645dabd0d81e651fe074bd8e73b
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Thu Aug 22 09:51:46 2013 -0400

    Start notes on conversion tools
~~~
{: .output}

`git log` lists all commits  made to a repository in reverse
 chronological order. The listing for each commit includes
 the commit's full identifier (which starts with the same characters as
 the short identifier printed by the `git commit` command earlier),
 the commit's author, when it was created, and the log message Git was
 given when the commit was created.

> ## Where Are My Changes?
>
> If we run `ls` at this point, we will still see just two files called `README.md` and `ToDo.txt`.
> That's because Git saves information about files' history
> in the special `.git` directory mentioned earlier
> so that our filesystem doesn't become cluttered
> (and so that we can't accidentally edit or delete an old version).
{: .callout}

Now suppose we add more information to the ToDo.txt file. Remember to save and exit the file in Nano by typing `CTRL + O` followed by `enter` and then `CTRL + X`.

~~~
$ nano ToDo.txt
~~~
{: .bash}

![Add extra lines to the existing file ToDo.txt](../fig/git-add-lines.png)

~~~
$ cat ToDo.txt
~~~
{: .bash}

~~~
Conversion functions needed:

- Dollars to Cents
- Gallons to Liters
- Hours to Minutes
- Feet to Inches
~~~
{: .output}

When we run `git status` now,
it tells us that a file it already knows about has been modified:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   ToDo.txt

no changes added to commit (use "git add" and/or "git commit -a")
~~~
{: .output}

The last line is the key phrase: "no changes added to commit".
 We have changed this file, but we haven't told Git we will want to
 save those changes (which we do with `git add`) nor have we saved
 them (which we do with `git commit`). So let's do that now. It is
 good practice to always review our changes before saving them. We do
 this using `git diff`. This shows us the differences between the
 current state of the file and the most recently saved version:

~~~
$ git diff
~~~
{: .bash}

~~~
diff --git a/ToDo.txt b/ToDo.txt
index 497e6b4..49e6774 100644
--- a/ToDo.txt
+++ b/ToDo.txt
@@ -3,4 +3,4 @@ Conversion functions needed:

 - Dollars to Cents
 - Gallons to Liters
 - Hours to Minutes
-
+- Feet to Inches

~~~
{: .output}

The output is cryptic because it is actually a series of computer
 readable commands describing how to reconstruct one file given the
 other. If we break it down into pieces:

1.  The first line tells us that Git is producing output similar to the
    Unix `diff` command comparing the old and new versions of the file.
2.  The second line tells exactly which versions of the file
    Git is comparing; `497e6b4` and `49e6774` are unique
    computer-generated labels for those versions.
3.  The third and fourth lines once again show the name of the file
    being changed.
4.  The remaining lines are the most interesting, they show us the
    actual differences and the lines on which they occur. In particular,
    the `+` marker in the first column shows where we added a line.

After reviewing our change, it's time to commit it:

~~~
$ git commit -m "Add another desirable conversion tool"
~~~
{: .bash}

~~~
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   ToDo.txt

no changes added to commit (use "git add" and/or "git commit -a")
~~~
{: .output}

Whoops:
Git won't commit because we didn't use `git add` first.
Let's fix that:

~~~
$ git add ToDo.txt
$ git commit -m "Add another desirable conversion tool"
~~~
{: .bash}

~~~
[master 34961b1] Add another desirable conversion tool
 1 file changed, 1 insertion(+)
~~~
{: .output}

Git insists that we add files to the set we want to commit
 before actually committing anything. This allows us to commit our
 changes in stages and capture changes in logical portions rather than
 only large batches. For example, suppose we're adding a few citations
 to our supervisor's work to our thesis. We might want to commit those
 additions, and the corresponding addition to the bibliography,
 but *not* commit the work we're doing on the conclusion
 (which we haven't finished yet).

To allow for this, Git has a special *staging area* where it keeps
 track of things that have been added to the current change set
 but not yet committed.

> ## Staging Area
>
> If you think of Git as taking snapshots of changes over the life of
> a project, `git add` specifies *what* will go in a snapshot
> (putting things in the staging area),
> and `git commit` then *actually takes* the snapshot, and
> makes a permanent record of it (as a commit).
> If you don't have anything staged when you type `git commit`,
> Git will prompt you to use `git commit -a` or `git commit --all`,
> which is kind of like gathering *everyone* for the picture!
> However, it's almost always better to
> explicitly add things to the staging area, because you might
> commit changes you forgot you made. (Going back to snapshots,
> you might get the extra with incomplete makeup walking on
> the stage for the snapshot because you used `-a`!)
> Try to stage things manually,
> or you might find yourself searching for "git undo commit" more
> than you would like!
{: .callout}

![The Git Staging Area](../fig/git-staging-area.svg)

Let's watch as our changes to a file move from our editor
to the staging area and into long-term storage.
First, we'll add another line to the file. Remember to save and exit the file in Nano by typing `CTRL + O` followed by `enter` and then `CTRL + X`.

~~~
$ nano ToDo.txt
~~~
{: .bash}

![Add extra lines to the existing file ToDo.txt](../fig/git-add-more-lines.png)

~~~
$ cat ToDo.txt
~~~
{: .bash}


~~~
Conversion functions needed:

- Dollars to Cents
- Gallons to Liters
- Hours to Minutes
- Feet to Inches
- Degrees to Radians
~~~
{: .output}

~~~
$ git diff
~~~
{: .bash}

~~~
diff --git a/ToDo.txt b/ToDo.txt
index 49e6774..7a10866 100644
--- a/ToDo.txt
+++ b/ToDo.txt
@@ -4,3 +4,4 @@ Conversion functions needed:
 - Gallons to Liters
 - Hours to Minutes
 - Feet to Inches
+-Degrees to Radians
~~~
{: .output}

So far, so good:
we've added one line to the end of the file
(shown with a `+` in the first column).
Now let's put that change in the staging area
and see what `git diff` reports:

~~~
$ git add ToDo.txt
$ git diff
~~~
{: .bash}

There is no output: as far as Git can tell,
there's no difference between what it's been asked to save permanently
and what's currently in the directory. However, if we do this:

~~~
$ git diff --staged
~~~
{: .bash}

~~~
diff --git a/ToDo.txt b/ToDo.txt
index 49e6774..7a10866 100644
--- a/ToDo.txt
+++ b/ToDo.txt
@@ -4,3 +4,4 @@ Conversion functions needed:
 - Gallons to Liters
 - Hours to Minutes
 - Feet to Inches
+-Degrees to Radians
~~~
{: .output}

it shows us the difference between
the last committed change
and what's in the staging area.
Let's save our changes:

~~~
$ git commit -m "Add the Degrees to Radians conversion"
~~~
{: .bash}

~~~
[master 005937f] Add the Degrees to Radians conversion
 1 file changed, 1 insertion(+)
~~~
{: .output}

check our status:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean

~~~
{: .output}

and look at the history of what we've done so far:

~~~
$ git log
~~~
{: .bash}

~~~
commit 005937fbe2a98fb83f0ade869025dc2636b4dad5
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Thu Aug 22 10:14:07 2013 -0400

    Add the Degrees to Radians conversion

commit 34961b159c27df3b475cfe4415d94a6d1fcd064d
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Thu Aug 22 10:07:21 2013 -0400

    Add another desirable conversion tool

commit f22b25e3233b4645dabd0d81e651fe074bd8e73b
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Thu Aug 22 09:51:46 2013 -0400

    Start notes on conversion tools
~~~
{: .output}

> ## Directories
>
> Two important facts you should know about directories in Git.
>
> 1. Git does not track directories on their own, only files within them.
> Try it for yourself:
>
> ~~~
> $ mkdir directory
> $ git status
> $ git add directory
> $ git status
> ~~~
> {: .bash}
> 
> Note, our newly created empty directory `directory` does not appear in
> the list of untracked files even if we explicitly add it (_via_ `git add`) to our
> repository. This is the reason why you will sometimes see `.gitkeep` files
> in otherwise empty directories. Unlike `.gitignore`, these files are not special
> and their sole purpose is to populate a directory so that Git adds it to
> the repository. In fact, you can name such files anything you like.
>
> {:start="2"}
> 2. If you create a directory in your Git repository and populate it with files,
> you can add all files in the directory at once by:
>
> ~~~
> git add <directory-with-files>
> ~~~
> {: .bash}
>
{: .callout}

To recap, when we want to add changes to our repository,
we first need to add the changed files to the staging area
(`git add`) and then commit the staged changes to the
repository (`git commit`):

![The Git Commit Workflow](../fig/git-committing.svg)

> ## Choosing a Commit Message
>
> Which of the following commit messages would be most appropriate for the
> last commit made to `ToDo.txt`?
>
> 1. "Changes"
> 2. "Added line '- Degrees to Radians' to ToDo.txt"
> 3. "Add Degrees to Radians conversion"
>
> > ## Solution
> > Answer 1 is not descriptive enough,
> > and answer 2 is too descriptive and redundant,
> > but answer 3 is good: short but descriptive.
> {: .solution}
{: .challenge}

> ## Committing Changes to Git
>
> Which command(s) below would save the changes of `myfile.txt`
> to my local Git repository?
>
> 1. `$ git commit -m "my recent changes"`
>
> 2. `$ git init myfile.txt`  
>    `$ git commit -m "my recent changes"`
>
> 3. `$ git add myfile.txt`  
>    `$ git commit -m "my recent changes"`
>
> 4. `$ git commit -m myfile.txt "my recent changes"`
>
> > ## Solution
> >
> > 1. Would only create a commit if files have already been staged.
> > 2. Would try to create a new repository.
> > 3. Is correct: first add the file to the staging area, then commit.
> > 4. Would try to commit a file "my recent changes" with the message myfile.txt.
> {: .solution}
{: .challenge}

[commit-messages]: http://chris.beams.io/posts/git-commit/
