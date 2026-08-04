# Addendum: New Computer Checklist

Pay attention to the following when you are about to:
1. Get a new computer
2. Reinstall your computer's OS

## 1. Make sure you have your GPG secret keys
On Windows, open **Kleopatra**, right-click your key (should be in bold) and select **Backup Secret Keys**. Enter your passphrase when prompted. Save the file in a safe place.

On Linux, find your Key ID by running `gpg --list-secret-keys --keyid-format long`, then run, replacing the text in brackets (including the brackets itself): `gpg --armor --export-secret-keys (Key ID) > private-key.asc`. Save the `private-key.asc` in a safe place.

## 2. On reinstall, make sure you have no pending changes
On reinstallation, Git might complain about a missing user account. Make sure you have no pending changes locally, because you need to delete the whole folder and re-clone if Git complains.

## 3. Make sure you remember your credentials
You're going to need them later. Make sure to try to log in to the git repo successfully.