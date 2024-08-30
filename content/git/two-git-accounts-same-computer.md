+++
title = 'Two Git Accounts Same Computer'
date = 2024-08-30T14:56:19+02:00
draft = true
+++

## Access two different git accounts from a single computer

Git uses the SSH keys to identify the account that you connects with. If you
want to access two different git accounts, you need a way to specify different
ssh keys linked to different ssh accounts.

A typical example is accessing a work and a home account from the same computer.

Git config can be used for this purpose.

### Generate a new ssh-key

Make sure you change the filename to differentiate it from the existing key

```sh
C:\Users\xxxxxxxxxx\Downloads\mynotes>ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\xxxxxxxxxx/.ssh/id_rsa): C:\Users\xxxxxxxxxx/.ssh/id_perso
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\xxxxxxxxxx/.ssh/id_perso.
Your public key has been saved in C:\Users\xxxxxxxxxx/.ssh/id_perso.pub.
```

### Add your new public key to the other github account

Authorize the newly generated `C:\Users\xxxxxxxxxx/.ssh/id_perso.pub` key to your github account.

### Edit `~/.ssh/config` file

In the ssh config file, create a new host pointing to github.com but with the new key.

```
Host github.com-perso
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_perso
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
```

### Access repo using alternate account

you can now access any github.com repository using the alternative key, by simply changing its hostname to 
the one you set in the config file.

```
git clone git@github.com-perso:oboudry/kube-and-co.git
```
