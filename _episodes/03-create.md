---
title: Creating a Repository
teaching: 10
exercises: 0
questions:
- "How can we create a new Git repository"
objectives:
- "Create a local Git repository."
keypoints:
- "GitHub makes creating a new repository very easy."
---

Once Git is configured, we can start using it. We are going to be looking
 at everything through the lens of [GitHub](https://github.com/), which
 is a highly popular online repository host that makes creating and
 managing repositories very easy. Be aware that everything we do
 on the website is also available from the command line, but we are going
 to gloss over most of those details during the workshop.


Open your web browser to [GitHub](https://github.com/) and log in (or
 create an account if necessary)
 
From your main dashboard, click on the little '+' drop-down menu and
 select 'New repository'
 
![Creating a Repository on GitHub (Step 1)](../fig/github-create-repo-01.png)

&nbsp;

Name your repository "[your name]-conversion" (replacing [your name]
 with your actual name), select "Public", check "Initialize this repository
 with a README", and click "Create Repository"

![Creating a Repository on GitHub (Step 2)](../fig/github-create-repo-02.png)

&nbsp;

Once the new repository is created, you will need to copy the URL displayed
 when you click on the 'Clone or download' button:

![Creating a Repository on GitHub (Step 3)](../fig/github-create-repo-03.png)

&nbsp;

Copy the URL provided and clone the repository onto your computer by
 running the following command (make sure to replace the url!):

~~~
$ git clone https://your_repository's_url
$ cd your_repository
$ ls -a
~~~
{: .bash}

We should see a pristine Git repository with a README file:

~~~
.	..	.git	README
~~~
{: .output}

Git stores information about the project in the special .git
 sub-directory. If we ever delete it, we will lose the project's history.

We can check that everything is set up correctly by asking Git to tell
 us the status of our project:

~~~
$ git status
~~~
{: .bash}

~~~
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
~~~
{: .output}
