<h1 style="color:#FF8C00">Git Configuration</h1>

Using Git with Visual Studio Code can often become bothersome due to features becoming deprecated. I'm going to do my best to cover all the things you can do to make your experience with GitHub, Git, and Visual Studio Code (VS Code) a lot more enjoyable.

## Table of Contents

[Creating Your Personal Access Token](#creating-your-personal-access-token)

[Authorizing GitHub](#authorizing-github)

[Caching Your Personal Access Token](#caching-your-personal-access-token)

## Creating Your Personal Access Token

<img src="https://imgur.com/LITPGcD.png" alt="Personal access token page" height=400 width=400>

With the deprecation of password authentication, the usage of the PAT or Personal Access Token is the preferred way to interact with GitHub remotely. The process to create the PAT is fairly straight forward, but the steps to make sure you are no longer prompted for a password are a bit complicated.

Office documentation relating to the creation of the personal access token can be found under the [sources](#sources) section at the bottom of this write-up!

## Authorizing GitHub

## Caching Your Personal Access Token

To stop the incessant prompt for a password relating to your personal access token, we're going to need to cache the token. This can be done a few ways and it's officially covered by GitHub as well. As always I've linked the article under the [sources](#sources) section for further education.

I'm a big fan of documentation so for assistance I will usually peer into official documents to help me further understand a topic. At the bottom of this write-up are the [sources](#sources) used and their respective links.

Step 1. Make a hidden file for your token

```bash
    touch ~/token.txt
```

Step 2. Make the GitHub credential store look at that file anytime it needs credentials

```bash
git config credential.helper --file=~/Documents/.token.txt
```
***You can place the file wherever you want but always make sure the file is hidden***

Step 3. Make a *Git Push* attempt to your repo (You will be asked for your token the first time)

Step 4. Make another *Git Push* attempt, but this time you will notice that it goes through without any prompt! 

**SUCCESS!!**


### Sources:

Git Credential Store Documentation: [https://git-scm.com/docs/git-credential-store](https://git-scm.com/docs/git-credential-store)

Cache GitHub Credentials in Git: [https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git)

Creating a Personal Access Token: [https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)