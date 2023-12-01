---
title: "How To: Git Configuration"
layout: post
---

All repo in Incidia has a rather troublesome requirement: all commits must be signed with GPG, and all commits to the default branch (master/develop) must be made by a Pull/Merge Request. This document aims to help in setting both of these up, after this has been asked many times.

# GPG Setup: Initial Setup

Before you begin, make sure you have the following already installed. Installing and configuring these is out of scope for this How To.
1. [Git](https://git-scm.com/downloads)
2. [Gpg4Win](https://www.gpg4win.org/) for Windows users, or simply `gpg` for Linux users
3. [Git LFS](https://git-lfs.com/) for LFS
4. A Git client of your choice for Windows Users - feel free to not install this if you're comfortable with command line.

{: .warning }
A lot of Git Clients (Sourcetree, GitKraken, etc) has their own Git already included. **DO NOT USE THEIR GIT** as you won't be able to use gpg to sign your commits!

## GPG Setup: Windows Users

First, find your gpg.exe location that you installed when you install Gpg4Win. By default this is on `C:\Program Files (x86)\GnuPG\bin\gpg.exe`.

With all of the above already installed, open **Kleopatra** and ensure you have a key in bold that matches your git name and email. The bold key means that you own the **secret** to that key, and thus able to sign things with it.

If nothing match, you'll need to create one. But assuming you have a match, make sure to note its **Key ID**, without any spaces.

{: .info }
You can also find your Key ID on the terminal - follow the direction below on GPG Setup for Linux Users if you wanted to do so.

Now open a terminal (Powershell, Git Bash, etc) and type in these commands, replacing the text in brackets (including the brackets itself):

`git config --global gpg.program "(path to gpg.exe)"`

`git config --global commit.signingkey (Key ID)`

`git config --global commit.gpgsign true`

{: .info }
This will apply gpg signing to **every repository that you deal with on that particular computer**, including non-Incidia repositories. This is not a problem as long as you use the same name and email on every repository on that computer. If you only want to apply this on one particular repository - which does mean you'll have to repeat these steps for each repository, change `--global` to `--local`

You are now ready to commit.

## GPG Setup: Linux (Ubuntu) Users

The steps are exactly the same as Windows, but to look for the Key ID, you'll need to run

`gpg --list-secret-keys --keyid-format long`

Find your name and email. The output will look similar to this:

```
sec   rsa4096/DC57B25E5064B3AA 2022-08-03 [SC]
      96AFCA68CD8DBF15C86E114CDC57B25E5064B3AA
uid                 [ ultimate] Alex Jones <alex@jones.com>
ssb   rsa4096/DC57B25E5064B3AB 2022-08-28 [E]
```

The Key ID is on the first line, after `sec rsa4096/` in the example, so in the example, the Key ID is `DC57B25E5064B3AA`

{: .info }
You can also do this on Windows. Makes it easy to copy-paste.

To find gpg, you can run `which gpg`

# Pre-Commit Preparations

Before you make your changes, make sure that:
1. You are on the default branch (master/develop)
2. Your local copy of the default branch is up to date
3. You have no changes detected yet - if you do, discard them

Now, with all 3 requirements satisfied, make a new branch. the name of the branch can be anything, but it's recommended to use your name, along with the main changes, in lowercase [kebab-case](https://www.theserverside.com/definition/Kebab-case), where spaces are replaced with dashes (-). Example: `reza-logo`

# Commit!

In the new branch, make your changes and commit them. If you have done the above, a window asking for a password for your gpg secret will appear. If this dialogue did not appear, your gpg configuration is incorrect and you'll need to redo the above again. After you submitted the password, the commit should be successful.

When the commit succeeded, it's time to push it to the repository.

{: .info }
Some Git client has the option to `Commit and push`, or has an option `Push immediately to (branch)`, allowing you to commit and push in one go. You might want to use this option instead.

# Pull Request

Assuming the push succeeded, now you need to Create a Pull/Merge Request (PR/MR). 

{: .info }
Github and Gitea = Pull Request (PR), Gitlab = Merge Request (MR). Both are the exact same, just a terminology difference. The following instructions would use Pull Request (PR), but note that the two are the same.

Open the repository in Github/Gitea, then go to `Pull Request > Create a pull request`. On the next screen, change the `compare` branch to your newly created branch, and leave `base` as is. 

{: .info }
In Github, if you have just pushed a new branch, Github will offer you an option to create a PR from the newly pushed branch. Assuming that branch is yours, you can immediately click `Create a pull request` there, which does the above automatically.

Verify the commits that appear, then click `Create pull request`. On the screen that appear, select `mmgfrcs` on the **Reviewers** and **Assignees** option, give it a title and a description, then click `Create pull request` again.

{: .info }
You can create a PR before you actually want to merge it - useful to check that your changes will not affect other parts of the repository that you did not touch. To do this, click the arrow next to the `Create pull request` button, then select `Create draft pull request` instead. When you're ready to merge the branch, click `Ready for Review`

Now to wait for the review. There are 2 outcomes for the review.

## Approved

Nothing needs to be done. The PR will be merged soon. When? No one knows, but your job is done the minute your work is approved.

On PR with multiple approvals, your job is done the minute everyone approves.

## Changes Requested

The PR contain things that need to be changed. Make the requested changes, then click `Re-request review` beside the Reviewer's name (in this case `mmgfrcs` but it might not be on multiple reviewer scenario) to request another review.

# Post-Merge

After your PR is merged, your changes will arrive on the default branch. Locally, switch to the default branch, then delete your created branch.

{: .info }
You don't actually need to delete your branch locally; You can just merge the default branch with yours. Merging, however, runs a risk of a wipeout - as has happened before, so be careful when merging!