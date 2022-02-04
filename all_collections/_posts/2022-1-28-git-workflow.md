---
layout: post
title: Status Update - Git Workflow
date: 2022-1-28
tag: Jekyll
author: Aquila Macedo
categories: ["Jekyll"]
image: "https://pixabay.com/get/g184cecb17952a1066d32a84bcbb6128901e27196c7f61e7575e920df0e22e2705527599b772a000ff19dd1b7d1a2b7de40c0c29279023a85e4cc2a8b160738046e1023ea6755089345d84ba394b99250_1280.jpg"
---

# What is git?

![Octocat](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png)

Git is a very powerful non-centralized versioning tool that allows developers to work collaboratively with each other, developed by Linus Torvalds, the Linux operating system kernel creator.

# Git Workflow

Let's suppose that we are working on a project and we have forked it in our repository, from that moment we clone this new repository in our work environment.


```git
git clone <repo url> 
```

### Git Remote

By cloning this repository it is possible to start the changes assuming that the git workflow is based on the branches because it is in the branches that the changes that are implemented regularly occur. We start on the master branch of our repository, knowing that it is necessary to make sure that the master branch will always be synchronized with the upstream (a remote connection that usually refers to the master branch of the original repository in which the fork was made).

You can list the remote connections you have with the other repositories, including the URL of each connection, using the following command:

```git
git remote -v 
``` 

Afterward use the pull pointing to where you want to synchronize, in this example it will be a remote master branch, so the following command will be used:

```git
git pull upstream master
```

After ensuring that the master is synchronized, we create a new branch to start the implementations/changes, using:

```git
git checkout -b <branch_name> 
```

### Git Rebase

Now let's suppose that after creating the new branch, a new commit appears on the master, so the question is: how do we update the new branch in such a way that its commits are the last ones?

In the image below we have two "timelines" the bottom line is equivalent to the new branch and in it, we have a commit called "Add Text", in the interval of the creation of the new branch a new commit appeared in the master called "Add Title", or whether the new branch is out of date.

![Octocat](/photos/1_remote.png)

You can solve this problem using the following command inside the new branch:

```git
git rebase master
```

This operation takes the commits of the new branch and stores them in a temporary area, while the new branch line is adjusted with the master branch line as in the image below.

![Octocat](/photos/2_remote.png)

After aligning the new branch line with the master, the new branch commits are reallocated again, but the hashes of those commits are changed, which can be dangerous if you are working on shared branches.

![Octocat](/photos/3_remote.png)

In this way, the rebase allows the use of the Fast-Forward merge, and now the new branch points to the last commit of the master.

## References

1. [Git Documentation](https://git-scm.com/)
2. [gitkraken](https://www.gitkraken.com/learn/git/git-remote/)
