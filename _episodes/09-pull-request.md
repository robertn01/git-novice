---
title: Forks and Pull Requests
teaching: 15
exercises: 15
questions:
- "How do I contribute to repositories I have not been given permission
to modify?"
objectives:
- "Fork a public repository"
- "Create a pull request to the original repository"
keypoints:
- "Any public repository on GitHub can be forked and modified."
- "If you make changes to a forked repository, you can request that the
maintainer of the original repository merges your changes into theirs."
---

There are no shortage of projects on GitHub, and you will not be able
 to modify those repositories unless the owner gives you permission.
 Usually, owners do not like to give permission to strangers, so instead
 rely on selectively pulling commits from a **forked** version of their
 primary repository.

## Creating a fork

To create a fork if your partner's repository, go to their GitHub page,
select the repository, and click on the 'fork' button:

![Forking repo (Step 1)](../fig/github-fork-01.png)

&nbsp;

Now clone the repository normally

~~~
$ git clone https://your-fork-of-your-partners-repo
~~~
{: .bash}

Make changes to the files in this repository the same way you would in
 any other. This is now **your** copy of the code, to do whatever you
 like with (within the bounds of the license agreement, as will be
 discussed later). 


## Contributing to a repo via pull request

Add another conversion tool to the growing list of functions in
 conversions.py

~~~
# My Conversion Tools

def dollars2cents(dollars):
    cents = dollars * 100
    return cents

...

def mole2atoms(mol):
    atoms = mole * 6.02e23
    return atoms
~~~
{: .python}

Create a commit, and push it to GitHub.

~~~
$ git add conversion.py
$ git commit -m "Add mole to atoms converter function"
$ git push
~~~
{: .bash}

You could now email the maintainer of the original repository to tell
 them about the cool new function you've written, and they could use
 the unique hash identifier of your commit to pull those changes into
 their own code base, but GitHub makes the process much easier with
 **Pull Requests**.

![Forking repo (Step 1)](../fig/github-fork-02.png)

&nbsp;

Compare the changes you want to add to your pull request and send it off

![Forking repo (Step 1)](../fig/github-fork-03.png)

&nbsp;

![Forking repo (Step 1)](../fig/github-fork-04.png)

&nbsp;

## Accepting a pull request

The maintainer will most likely get an email about the new pull request,
 but if they don't, it will be visible to them next time the log into
 GitHub:

![Forking repo (Step 1)](../fig/github-fork-05.png)

&nbsp;

Accepting the request is as simple as hitting the green button, **BUT BE
 CAREFUL!**. Always look at the cimmit history, and check what changes
 are included in the pull request. You don't want the merge to break
 your code. Check the '`Commits`' and '`Files changed`' tabs to be sure.

![Forking repo (Step 1)](../fig/github-fork-06.png)

&nbsp;


> ## Practice makes perfect
>
> Fork your partner's repository and submit a pull request.
> 
> Also accept the pull request your partner has submitted.
{: .challenge}

> ## Be wary of the big green button
>
> Try to think of some reasons you may want to reject a pull request.
{: .challenge}

> ## Fork a public repo
>
> Browse the [GitHub Showcase](https://github.com/showcases) and try
> to find a repository that you think you might find useful (or that you 
> may want to contribute to!). Fork it!
{: .challenge}

