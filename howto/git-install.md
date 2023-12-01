---
title: "How To: Git Installation"
layout: post
---

Moving on to a new computer and confused as to how to install Git stuff? Well, here it is.

Now, on the [Git Configuration How-To](/howto/git.html), there are prerequisites to do before moving on to configuration, that is:
1. [Git](https://git-scm.com/downloads)
2. [Gpg4Win](https://www.gpg4win.org/) for Windows users, or simply `gpg` for Linux users
3. [Git LFS](https://git-lfs.com/) for LFS
4. A Git client of your choice

This How-To will assist in installing each component. But first, download them by clicking on the link above.

{: .info }
These instructions assume you're running Windows. On Ubuntu, it's as simple as a single `apt install git gpg git-lfs` command. Heck, a lot of the times, these are **already installed** on Linux!

# Installing Git

After downloading the file, open it. There will be a lot of steps on a Git install. Fortunately for us, the default option is fairly sensible enough that it doesn't need changing, and you can just press **Next** on each of them. However, there are some that needs checking or changing:
1. On **Choosing the default editor used by Git**, change this to an editor that is not:
    - Vim,
    - Notepad, or
    - Wordpad

{: .warning }
Before installing Git, make sure you install your editor of choice first. For Git, **Visual Studio Code** is recommended.

2. On **Adjusting the name of the initial branch in new repositories**, select **Override the default branch name for new repositories**, and type `master` on the provided box

{: .warning }
Do not choose **Let Git decide**, even if the branch is currently still `master`, as this will change without notice.

3. On **Choose a credential helper**, make sure that **Git Credential Manager Core** is selected (should be by default)

# Installing Gpg4Win

Gpg4Win has a straightforward install, just click **Next** on each and every one.

Make sure that, in **Choose Install Location**, remember where you install it since it will be used on configuration.

On the final screen, if you want to configure Git right after, keep **Run Kleopatra** checked. Otherwise, you may leave it unchecked.

# Installing Git LFS

Git LFS install is also straightforward, just click **Next** on each and every one.

After installation is completed, open a Terminal (Powershell, Windows Terminal, etc) and type `git lfs install`. If your installation is successful, the command should output `Git LFS initialized`

# Installing a Git Client

Well, this depends on the client of choice, but since everyone's liking Sourcetree these days, let's install it. Download it [here.](https://www.sourcetreeapp.com/) and open it.

1. On **Registration**, click **Skip**
2. On **Install Tools**, make sure that on the **Git** section, it discovered your system-wide Git. If you encountered a checkbox, make sure it's checked, then continue anyways.
3. On **Preferences**, type in your name and email *exactly* as the name and email you'll use for Git - this must match the name and email on Github/Gitea.

You should then be brought to an empty tab.

## Switch to System Git

If you encountered a checkbox on Step 2 above, or if when following the [Git Configuration How-To](/howto/git.html) you encountered the `No secret key` error, it might be because Sourcetree is using its *own* client and not the system-wide client.

To change this, open **Tools > Options**, then **Git**, and scroll down. The **System** button should be disabled and the **Embedded** button should be clickable, indicating that Sourcetree is using system-wide git. If this is not the case, you can click the **System** button to switch it.

{: .info }
It should switch automatically. If a dialogue appeared asking on where Git is, that means you have not installed Git yet.

# Afterwards

After installation completed, you can move on to [Git Configuration How-To](/howto/git.html)