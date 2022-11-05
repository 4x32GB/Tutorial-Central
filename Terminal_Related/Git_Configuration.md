<h1 style="color:#FF8C00">Git Configuration</h1>

Using Git with Visual Studio Code can often become bothersome due to features becoming deprecated. I'm going to do my best to cover all the things you can do to make your experience with GitHub, Git, and Visual Studio Code (VS Code) a lot more enjoyable.

## Table of Contents

[Creating Your Personal Access Token](#creating-your-personal-access-token)

[Authorizing GitHub](#authorizing-github)

[Caching Your Personal Access Token](#caching-your-personal-access-token)

[Addressing Issues Caching the Personal Access Token](#addressing-issues-with-caching-the-personal-access-token)

[Sources](#sources)

## Creating Your Personal Access Token

<img src="https://imgur.com/LITPGcD.png" alt="Personal access token page" height=400 width=400>

With the deprecation of password authentication, the usage of the PAT or Personal Access Token is the preferred way to interact with GitHub remotely. The process to create the PAT is fairly straight forward, but the steps to make sure you are no longer prompted for a password are a bit complicated.

Office documentation relating to the creation of the personal access token can be found under the [sources](#sources) section at the bottom of this write-up!

## Authorizing GitHub

Authorizing Git with your GitHub credentials is very important, but I found that this process doesn't always store the credentials the way we may want. This will accomplish removing the hassle of always needing to enter your username and password, but it will always ask for a personal access token. This isn't such a big deal if you utilize a password manager, or you just don't mind having to do so, but to save time, we'll eventually cache that token.

Step 1. Install the GitHub CLI

```bash
sudo nala install gh -y
```
> **_NOTE:_** I use nala as my package manager, but if you use apt, dnf, or yay you will do whatever is the equivalent. The APT equivalent is exactly as above since nala is just a fork of APT.

## Caching Your Personal Access Token

To stop the incessant prompt for a password relating to your personal access token, we're going to need to cache the token. This can be done a few ways and it's officially covered by GitHub as well. As always I've linked the article under the [sources](#sources) section for further education.

I'm a big fan of documentation so for assistance I will usually peer into official documents to help me further understand a topic. At the bottom of this write-up are the [sources](#sources) used and their respective links.

Step 1. Make a hidden file for your token

```bash
touch ~/.token
```

Step 2. Make the GitHub credential store look at that file anytime it needs credentials

```bash
git config --global credential.helper --file=~/.token
```
> **_Side Note:_** You can place the file wherever you want but always make sure the file is hidden

Step 3. Make a *Git Push* attempt to your repo (You will be asked for your token the first time)

Step 4. Make another *Git Push* attempt, but this time you will notice that it goes through without any prompt! 

**SUCCESS!!**

## Addressing Issues with Caching the Personal Access Token

Often times your credentials just will not store for whatever reason, whether it be because a file is not being created or the access to not permitted for Git. By running the command below, your credentials should then be stored after the PAT is asked for.

```bash
git config --global credential.helper cache
```

A good indication of your credentials being stored is if you check the .gitconfig file using the command below. You will notice that the cache value is set to the 'credential.helper' variable.

```bash
git config --global -l
```
![Global Git Config Terminal Prompt](https://imgur.com/ZfTYc6m.png)

## Sources:

Git Credential Store Documentation: [https://git-scm.com/docs/git-credential-store](https://git-scm.com/docs/git-credential-store)

Cache GitHub Credentials in Git: [https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git)

Creating a Personal Access Token: [https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)