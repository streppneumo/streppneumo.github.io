---
layout: default
title:  Git Workflow
---

# Managing your code with Git

Starting this year, we will use a slightly different workflow for managing our code with Git.  Instead of everyone contributing to the same repository, each team member will "fork" the main repository (streppneumo/isp) and commit to their local copy.

You will be responsible for keeping your fork up to date (syncing) and letting Paul know when you have changes that are ready for incorporation into the main repository (pull requesting).

To setup your new fork:

1. Delete the old isp directory from your computer.  If you have any unsynced changes, let Paul know.  You will not be able to push changes to the streppneumo/isp repository anymore.  (Your write permissions have been removed.)

2. Follow the instructions on [https://help.github.com/articles/fork-a-repo](https://help.github.com/articles/fork-a-repo) to fork the streppneumo/isp repository into your GitHub account.

# Fetching changes from ```streppneumo/isp```

## Initial setup (do once)

To fetch changes from the main repository and add them to your fork, you need to use the Git command line program, called ```git```.

First very that ```git``` is installed.  Open a terminal (Applications -> Other -> Terminal on a Mac) and type

	$ which git

You don't need to type the dollar sign; one should appear when the terminal is ready.  Press return, and you should see the following line:

	$ which git
	/usr/bin/git

If you do, ```git``` is installed and ready to use.

Next, move into the directory containing your fork of the ```isp``` site.  Use the ```cd``` (change directory) command to specify the path.  My directory is stored in (Dropbox -> bc -> isp), so I would type

	$ cd ~/Dropbox/bc/isp

The tilde ```~``` is the location of your home directory on a Mac.  You can check that you're in the right place with the ```ls``` command which lists the files in the current directory.

	$ ls
	CellScribe	__init__.py	biocyc		docs		model

We need to tell Git that your repository was forked from the "upstream" repository ```streppneumo/isp```.  First, let's see what Git already knows about its ancestry.

	$ git remote -v
	origin	http://github.com/pauljensen/isp (fetch)
	origin	http://github.com/pauljensen/isp (push)

Git knows that my local copy was cloned from the origin ```pauljensen/isp``` on the GitHub site.  We need to add the upstream repository with the following command

	$ git remote add upstream https://github.com/streppneumo/isp.git

Now Git knows where the upstream repository is:

	$ git remote -v
	origin	http://github.com/pauljensen/isp (fetch)
	origin	http://github.com/pauljensen/isp (push)
	upstream	https://github.com/streppneumo/isp.git (fetch)
	upstream	https://github.com/streppneumo/isp.git (push)

## Fetching from upstream (do often)

Let's grab the changes from ```streppneumo/isp``` and pull them into our clone:

	$ git fetch upstream

Git will grab all the new changes and put them in your repository.  To avoid clobbering all your unmerged code, Git creates a separate *branch* and stores the changes there.  As a final step, we need to go back to our master branch (where your code was) and merge the new changes from ```streppneumo/isp```.

	$ git checkout master
	$ git merge upstream/master

If you have any conflicts, they need to be resolved manually.  Otherwise, you can commit the merge to your fork and continue working.


