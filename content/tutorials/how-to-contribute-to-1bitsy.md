---
lastmod: 2016-09-04
date: 2016-09-04
linktitle: How to contribute
menu:
  main:
    parent: tutorials
next: /tutorials/installing-on-mac/
prev: /tutorials/github-pages-blog/
title: How to contribute to 1Bitsy
weight: 10
---

## Introduction

1Bitsy is an open source hardware and software project and lives by the work of
its
[contributors](https://github.com/1bitsy/1bitsy-examples/graphs/contributors).
Help to make 1Bitsy even more awesome. There are plenty of [open
issues](https://github.com/1bitsy/1bitsy-examples/issues) on GitHub and we need
your help.

This tutorial is intended for people who are new to Git, GitHub or open source
projects in general. It should help to overcome most of the barriers that
newcomers encounter. It describes step by step what you need to do.

For any kind of questions please take a look at our
[forum](https://discuss.1bitsy.org/).

## Create an account on GitHub

If you're going to contribute code, you'll need to have an account on GitHub. Go
to [www.github.com/join](https://github.com/join) and set up a personal account.

## Install Git on your system

You will need to install Git. This tutorial assumes basic knowledge about Git.
Refer to this excellent [Git book](https://git-scm.com/) if you are not sure
where to begin. The used terminology will be explained with annotations.

Git is a [version control system](https://en.wikipedia.org/wiki/Version_control)
to track the changes of source code. Hugo depends on smaller third-party
packages that are used to extend the functionality. We use them because we don't
want to reinvent the wheel.

Go ships with a sub-command called `get` that will download these packages for
us when we setup our working environment. The source code of the packages is
tracked with Git. `get` will interact with the Git servers of the package
hosters in order to fetch all dependencies.

Move back to the terminal and check if Git is already installed. Type in `git
version` and press enter. You can skip the rest of this section if the command
returned a version number. Otherwise [download](https://git-scm.com/downloads)
the lastest version of Git and follow this [installation
guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Finally, check again with `git version` if Git was installed successfully.

### Git Graphical Front Ends

There are several [GUI clients](https://git-scm.com/downloads/guis) that help
you to operate Git. Not all are available for all operating systems and maybe
differ in their usage. Thus, so we will use the command line since the commands
are everywhere the same.

## Set up your working copy

The working copy is set up locally on your computer. It's what you'll edit,
compile, and end up pushing back to GitHub. The main steps are cloning the
repository and creating your fork as a remote.

### Clone the repository

You should now copy the 1Bitsy repository of your choosing to your computer.
You'll hear this called "clone the repo". GitHub's [help
pages](https://help.github.com/articles/cloning-a-repository/) give us a short
explanation:

> When you create a repository on GitHub, it exists as a remote repository. You
can create a local clone of your repository on your computer and sync between
the two locations.

We're going to clone the [master 1bitsy-examples
repository](https://github.com/1bitsy/1bitsy-examples). That seems
counter-intuitive, since you won't have commit rights on it. But it's required
for the workflow. You'll work on a copy of the master and push your changes to
your own repository on GitHub.

So, let's clone that master repository:

```sh
git clone git@github.com/1bitsy/1bitsy-examples
```

### Fork the repository

If you're not fimiliar with this term, GitHub's [help
pages](https://help.github.com/articles/fork-a-repo/) provide again a simple
explanation:

> A fork is a copy of a repository. Forking a repository allows you to freely
experiment with changes without affecting the original project.

#### Fork by hand

Open the [1bitsy examples repository](https://github.com/1bitsy/1bitsy-examples) on Github
and click on the "Fork" button in the top right.

![Fork button](/img/tutorials/how-to-contribute-to-1bitsy/forking-a-repository.png)

Now open your fork repository on GitHub and copy the remote url of your fork.
You can choose between HTTPS and SSH as protocol that Git should use for the
following operations. HTTPS works always [if you're not
sure](https://help.github.com/articles/which-remote-url-should-i-use/).

![Copy remote url](/img/tutorials/how-to-contribute-to-1bitsy/copy-remote-url.png)

Switch back to the terminal and move into the directory of the cloned master
repository from the last step.

### Contributing to the documentation

Perhaps you want to start contributing to the docs. You can find the
documentation and the 1bitsy website sources within the 1bitsy-website
repository.

The website is built using [Hugo](http://gohugo.io). You can start Hugo's
built-in server via `hugo server`. Browse the documentation by entering
[http://localhost:1313](http://localhost:1313) in the address bar of your
browser. The server automatically updates the page if you change its content.
