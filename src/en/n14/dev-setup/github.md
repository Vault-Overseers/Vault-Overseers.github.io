# Github

## GitHub Website / Basics
GitHub is the platform we use for hosting our code in a repository (repo for short) and is used by nearly all servers / codebases in SS13 and 14. It allows new contributors to clone or fork our repository to make their own changes and modifications, then they can submit a pull request (or PR for short) to our repo to have their changes merged into the game. You'll want to create a GitHub account then head to [the nuclear-14 repository here](https://github.com/Vault-Overseers/nuclear-14) or whichever repository you want to work on and hit the "Fork" button near the top right, below the search bar. This will ask you a few things but you can ignore that and just hit the Create Fork button in green. This will add a fork of the repo to "Your repositories" which you can find by clicking on your avatar or username in the top right.

With GitHub we work on branches, this lets you work on multiple things at once without affecting each other and with better control. Your main branch is usually called "Master" and we keep this clean, that means we don't do any actual work on Master branch. Instead we create branches from it and work on those instead. On the website you can do this by clicking on Master under the repository name and a bar for "Find or Create branch" will appear. Ideally we don't work on the GitHub website as its clunky and not feature rich, so skip to the GitHub clients bit below for more information on branches.

The final thing to know about the GitHub website is once you've done some work on a branch and are ready to submit a pull request (PR) to have it merged with the game. For this you head to the [upstream repository here](https://github.com/Vault-Overseers/nuclear-14) (upstream meaning the main nuclear-14 repo). If you've recently pushed changes to from your local branch to your origin branch on the GitHub website then you'll see an orange banner across the top asking if you'd like to open a pull request. Hit this and fill out the template and submit it to be reviewed by the Nuclear 14 Maintainers. If you're reading this guide in order then head down to the GitHub Clients section to learn more about commits, origin, working trees and more.

## GitHub Clients
GitHub can be accessed through command line interface (CLI) by downloading Gitbash or through a client like Github Desktop, Kraken or SmartGit. We recommend [SmartGit](https://www.syntevo.com/smartgit/) (IF you have met their open source developer requirements of typically 100 commits to a project) as a user friendly yet powerful and free option for open source development like ours. It might look like a lot at first glance but we'll run through installation and what everything is, and it'll quickly become just like any other software you use.

## Github Desktop
This is not to be confused with the Github website or downloading Git. [Github Desktop](https://desktop.github.com/download/) is it's own program that can be used to clone repositories to your computer, create and change what branch you're working on and commit changes to branches.

For new contributors I 100% recommend this as its super simple and will do the job. You can then make changes to files locally, they will show up in the list of changed files, you then hit commit and put a message summarising what your changes are, then push your changes so they appear on your remote or origin repository on the website, ready to be PR'd.

Please keep changes consistent to the branch. Don't do random things all on the same branch unless its specifically a big bugfix PR or something and likewise try not to do single file commits or single change PRs unless they are absolutely necessary. Single file commits is why we don't like working on the Github website to edit files, as it will pollute the commit tree.

NOTE: If you have a changed file when you open it up for "Robust Toolbox" or similar, IGNORE IT and make sure to NEVER commit it. It will break your branch and need resetting.

This covers the basics of Git for SS14. There are more comprehensive Github guides elsewhere.