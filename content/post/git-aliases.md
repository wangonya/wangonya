---
title: Speeding up your gitflow with aliases
date: 2018-12-20
description: Shortening those common git commands just a little bit to make your workflow that much faster
featuredImage: /img/gitalias.jpg
categories: [git, devtips]
---
Sometimes it gets boring to have to write those long git commands over and over again, 
and if you've read [this post](https://github.com/andela/bestpractices/wiki/Eliminate-Stupid-Mental-Effort-(ESME)) 
on Andela best practices, you already know that one of the attributes that makes a programmer great is _laziness_.

In an effort to improve my laziness, I put together these aliases on the git commands I use most to speed up my 
gitflow. If you're on a mac or a linux machine, you can set them up in your `.bashrc` or `.bash_profile`. A basic familiarity 
with the terminal is assumed so I won't go into how to do that 😊. Feel free to reach out to me though if you're having problems.

### Initialising a new git repository
```bash
alias gi = 'git init'
```
So that instead of doing `git init` you just do `gi`

### Checking the status of files
```bash
alias gs = 'git status'
```
So that instead of doing `git status` you just do `gs`

### Adding files to the staging area
```bash
alias ga = 'git add'
```
So that instead of doing `git add file` you just do `ga file`

### Committing your changes
```bash
alias gcm = 'git checkout -m'
```
So that instead of doing `git checkout -m "commit message"` you just do `gcm "commit message"`

### Pushing your changes to a remote origin
```bash
alias gpso = 'git push origin'
```
So that instead of doing `git push origin develop` you just do `gpso develop`

### Pulling changes from a remote origin
```bash
alias gplo = 'git pull origin'
```
So that instead of doing `git pull origin develop` you just do `gplo develop`

### Checking your branches
```bash
alias gb = 'git branch'
```
So that instead of doing `git branch` you just do `gb`

### Switching branches
```bash
alias gc = 'git checkout'
```
So that instead of doing `git checkout master` you just do `gc master`

### Creating a new branch and switching to it
```bash
alias gcb = 'git checkout -b'
```
So that instead of doing `git checkout -b ft-branch` you just do `gcb ft-branch`

### Renaming a branch
```bash
#if you are on the branch you want to rename
alias gcm = 'git branch -m'
```
So that instead of doing `git branch -m bg-branch` you just do `gcm bg-branch`

### Merging a branch
```bash
alias gm = 'git merge'
```
So that instead of doing `git merge bg-branch` you just do `gm bg-branch`

### Deleting a branch
```bash
alias gbd = 'git branch -d' #use -D for a forced delete
```
So that instead of doing `git branch -d ft-branch` you just do `gbd ft-branch`

These are just a few of the ones I most commonly use. There's a whole lot of other commands that you may use from time 
to time, and you can always come back to your aliases and add them. 

If you add all the above aliases to your `.bashrc` or `.bash_profile` (or `.zshrc` if you're using Zsh), this is how it 
should look:
```bash
# .bashrc or .bash_profile or .zshrc
# git aliases
alias gi = 'git init'
alias gs = 'git status'
alias ga = 'git add'
alias gcm = 'git checkout -m'
alias gpso = 'git push origin'
alias gplo = 'git pull origin'
alias gb = 'git branch'
alias gc = 'git checkout'
alias gcb = 'git checkout -b'
alias gcm = 'git branch -m'
alias gm = 'git merge'
alias gbd = 'git branch -d' #use -D for a forced delete
```

![the source](/img/source.png)