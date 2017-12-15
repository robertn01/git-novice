---
title: Automated Version Control
teaching: 5
exercises: 0
questions:
- "What is version control and why should I use it?"
objectives:
- "Understand the benefits of an automated version control system."
- "Understand the basics of how Git works."
keypoints:
- "Version control is like an unlimited 'undo'."
- "Version control also allows many people to work in parallel."
---

We'll start by exploring how version control can be used
to keep track of what one person did and when.
Even if you aren't collaborating with other people,
automated version control is much better than this situation:

[![Piled Higher and Deeper by Jorge Cham, http://www.phdcomics.com/comics/archive_print.php?comicid=1531](../fig/phd101212s.png)](http://www.phdcomics.com)

"Piled Higher and Deeper" by Jorge Cham, http://www.phdcomics.com

We've all been in this situation before: it seems ridiculous to have
multiple nearly-identical versions of the same document. Some word
processors let us deal with this a little better, such as Microsoft
Word's [Track Changes](https://support.office.com/en-us/article/Track-changes-in-Word-197ba630-0f5f-4a8e-9a77-3712475e806a) or Google Docs' [version
history](https://support.google.com/docs/answer/190843?hl=en).

Version control systems start with a base version of the document and
then save just the changes you made at each step of the way. You can
think of it as a tape: if you rewind the tape and start at the base
document, then you can play back each change and end up with your
latest version.

![Changes Are Saved Sequentially](../fig/play-changes.svg)

Once you think of changes as separate from the document itself, you
can then think about "playing back" different sets of changes onto the
base document and getting different versions of the document. For
example, two users can make independent sets of changes based on the
same document.

![Different Versions Can be Saved](../fig/versions.svg)

If there aren't conflicts, you can even play two sets of changes onto the same base document.

![Multiple Versions Can be Merged](../fig/merge.svg)

A version control system is a tool that keeps track of these changes for us and
helps us version and merge our files. It allows you to
decide which changes make up the next version, called a
[commit]({{ page.root }}/reference/#commit), and keeps useful metadata about them. The
complete history of commits for a particular project and their metadata make up
a [repository]({{ page.root }}/reference/#repository). Repositories can be kept in sync
across different computers facilitating collaboration among different people.

> ## The Long History of Version Control Systems
>
> Automated version control systems are nothing new.
> Tools like RCS, CVS, or Subversion have been around since the early 1980s and are used by many large companies.
> However, many of these are now becoming considered as legacy systems due to various limitations in their capabilities.
> In particular, the more modern systems, such as Git and [Mercurial](http://swcarpentry.github.io/hg-novice/)
> are *distributed*, meaning that they do not need a centralized server to host the repository.
> These modern systems also include powerful merging tools that make it possible for multiple authors to work within
> the same files concurrently.
> 
{: .callout}

> ## Understanding the Core Concepts
> There are two primary types of version control: Centralized and distributed. Centralized version control involves people 
> taking turns writing to one central repository; distributed version control (like Git) allows people to make their own
> branches and work on them separately, then reintegrate the pieces that should join the master branch.
> 
> [A Visual Guide to Version Control](https://betterexplained.com/articles/a-visual-guide-to-version-control/) provides an 
> excellent overview of centralized version control. The code examples it uses are based on Subversion, but the concepts are common
> to multiple platforms.
> 
> [Intro to Distributed Version Control](https://betterexplained.com/articles/intro-to-distributed-version-control-illustrated/) 
> helps clarify the distinctions between centralized and distributed systems. The example code here uses Mercurial, but again, the
> general concepts of distributed version control are covered.
>
> [Aha Moments when Learning Git](https://betterexplained.com/articles/aha-moments-when-learning-git/) is the third in the series, and 
> reviews Git's unique distinctions among version control systems and helpful ways of understanding what Git's unique features do.
{: .callout}

> ## Paper Writing
>
> *   Imagine you drafted an excellent paragraph for a paper you are writing, but later ruin it. How would you retrieve
>     the *excellent* version of your conclusion? Is it even possible?
>
> *   Imagine you have 5 co-authors. How would you manage the changes and comments they make to your paper?
>     If you use LibreOffice Writer or Microsoft Word, what happens if you accept changes made using the
>     `Track Changes` option? Do you have a history of those changes?
{: .challenge}
