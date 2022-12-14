# Git Configuration

Using Git with Visual Studio Code can often become bothersome due to features becoming deprecated. I'm going to do my best to cover all the things you can do to make your experience with GitHub, Git, and Visual Studio Code (VS Code) a lot more enjoyable.

## Table of Contents

[Installing Git](#installing-git)

[Initial Configuration](#initial-configuration)

[Creating Your Personal Access Token](#creating-your-personal-access-token)

[Authorizing GitHub](#authorizing-github)

[Caching Your Personal Access Token](#caching-your-personal-access-token)

[Addressing Issues Caching the Personal Access Token](#addressing-issues-with-caching-the-personal-access-token)

[Sources](#sources)

## Installing Git

To begin our source control journey, we'll first need to start off by installing the most important component, Git. Although Git and GitHub share the same portion of a name, 'Git', they're actually entirely different tools. GitHub is dependent upon Git, but Git could live without GitHub since you could do everything locally and never upload it to the cloud.

With my daily driver being Linux, I will only provide detailed instructions for it, but Windows and MacOS are just as straight-forward.

First we'll need to navigate to Git's download page located [here](https://www.git-scm.com/downloads). 

![Git Download Page](https://i.imgur.com/mmtvKxT.png)

Go ahead and download your specific executable depending on OS. For my Linux homies, you'll do everything through the terminal as usual. For **Example**, I daily drive Fedora, so I would use the below command, just use your distro-alternative.

```bash
sudo dnf install git
```

As with anything freshly installed on Linux, you'll want to update and upgrade to grab any dependencies not available in the original package.

```bash
sudo dnf upgrade -y
```

That's really about it for the installation of Git, since it's basically a command-line utility, you won't see a GUI (unless you want the GUI client).

## Initial Configuration

Once Git is installed, we'll need to run through a few initial configurations to make sure we can interact with our repositories. I'm assuming that anyone reading this is using Git for their repos that are hosted on GitHub.

Git Configuration Checklist:

- [x] Required: Set Git Email
    ```git
    git config --global user.email "jakemontgom67@hotmail.com"
    ```

- [x] Required: Set Git Name
    ```git
    git config --global user.name "Jake Montgomery"
    ```

- [ ] Optional: Change Branch Name
    ```git
    git config --global init.defaultBranch main
    ```

## Creating Your Personal Access Token

<img src="https://imgur.com/LITPGcD.png" alt="Personal access token page" height=400 width=400>

With the deprecation of password authentication, the usage of the PAT or Personal Access Token is the preferred way to interact with GitHub remotely. The process to create the PAT is fairly straight forward, but the steps to make sure you are no longer prompted for a password are a bit complicated.

Office documentation relating to the creation of the personal access token can be found under the [sources](#sources) section at the bottom of this write-up!

## Authorizing GitHub

Authorizing Git with your GitHub credentials is very important, but I found that this process doesn't always store the credentials the way we may want. This will accomplish removing the hassle of always needing to enter your username and password, but it will always ask for a personal access token. This isn't such a big deal if you utilize a password manager, or you just don't mind having to do so, but to save time, we'll eventually cache that token.

Step 1. Install the GitHub CLI

```bash
sudo dnf install gh -y
```

> **_NOTE:_** I use dnf as my package manager since I am a Fedora user, but the command to install a package is similar across _most_ distros. For example, to install GitHub CLI on Pop!_OS (Debian), you would run the command 'sudo apt install gh'.

## Caching Your Personal Access Token

To stop the incessant prompt for a password relating to your personal access token, we're going to need to cache the token. This can be done a few ways and it's officially covered by GitHub as well. As always I've linked the article under the [sources](#sources) section for further education.

I'm a big fan of documentation so for assistance I will usually peer into official documents to help me further understand a topic. At the bottom of this write-up are the [sources](#sources) used and their respective links.

Step 1. Make a hidden file for your token

```bash
touch ~/.token
```

Step 2. Make the GitHub credential store look at that file anytime it needs credentials

```git
git config --global credential.helper --file=~/.token
```

> **_Side Note:_** You can place the file wherever you want but always make sure the file is hidden

Step 3. Make a *Git Push* attempt to your repo (You will be asked for your token the first time)

Step 4. Make another *Git Push* attempt, but this time you will notice that it goes through without any prompt! 

## Addressing Issues with Caching the Personal Access Token

Often times your credentials just will not store for whatever reason, whether it be because a file is not being created or the access to not permitted for Git. By running the command below, your credentials should then be stored after the PAT is asked for.

```git
git config --global credential.helper cache
```

A good indication of your credentials being stored is if you check the .gitconfig file using the command below. You will notice that the cache value is set to the 'credential.helper' variable.

```git
git config --global -l
```

Alternative:

```git
git config --list
```

![Global Git Config Terminal Prompt](https://imgur.com/ZfTYc6m.png)

## Extras

Install Git-Extras to Utilize Additional Modules

```bash
sudo [package manager] install git-extras
```

Ignoring That One Pesky File

```git
git-ignore --global [filename]
```

>**_Global Reasoning:_** I tend to use the --global flag due to all of my projects being a solo process and having everything set on a user basis instead of working directory.

Disable Git Ignored File Messaged

```git
git config advice.addIgnoredFile false
```

Generating an SSH Key

```bash
ssh-keygen -t [key-type] -C "youremail@provider.com"
```

>**_NOTE:_** By default, ssh keys are stored in the following location > '~/.ssh' if you forget where the key was saved. All key types are stored here no matter if rca, ed25519, DSA, etc..

## Looking for Help?

There are 3 different ways (technically 4) you can get help with a specific command or just Git in general:

**Option #1**

```git
git <verb> --help
```

```git
git pull --help
```

**Option #2**

```git
git help <verb>
```

```git
git help pull
```


**Option #3**

```git
man git <verb>
```

```git
man git pull
```

**Option #4**

Alternatively, if you aren't interested in digging through the manual relating to a single verb, you could use the simple *-h* flag to get a more basic rundown.

```git
git push -h
```

Output:

    git pull -h
    usage: git pull [<options>] [<repository> [<refspec>...]]

        -v, --verbose         be more verbose
        -q, --quiet           be more quiet
        --progress            force progress reporting
        --recurse-submodules[=<on-demand>]
                            control for recursive fetching of submodules

    Options related to merging
        -r, --rebase[=(false|true|merges|interactive)]
                            incorporate changes by rebasing rather than merging
        -n                    do not show a diffstat at the end of the merge
        --stat                show a diffstat at the end of the merge
        --log[=<n>]           add (at most <n>) entries from shortlog to merge commit message
        --signoff[=...]       add a Signed-off-by trailer
        --squash              create a single commit instead of doing a merge
        --commit              perform a commit if the merge succeeds (default)
        --edit                edit message before committing
        --cleanup <mode>      how to strip spaces and #comments from message
        --ff                  allow fast-forward
        --ff-only             abort if fast-forward is not possible
        --verify              control use of pre-merge-commit and commit-msg hooks
        --verify-signatures   verify that the named commit has a valid GPG signature
        --autostash           automatically stash/stash pop before and after
        -s, --strategy <strategy>
                            merge strategy to use
        -X, --strategy-option <option=value>
                            option for selected merge strategy
        -S, --gpg-sign[=<key-id>]
                            GPG sign commit
        --allow-unrelated-histories
                            allow merging unrelated histories

    Options related to fetching
        --all                 fetch from all remotes
        -a, --append          append to .git/FETCH_HEAD instead of overwriting
        --upload-pack <path>  path to upload pack on remote end
        -f, --force           force overwrite of local branch
        -t, --tags            fetch all tags and associated objects
        -p, --prune           prune remote-tracking branches no longer on remote
        -j, --jobs[=<n>]      number of submodules pulled in parallel
        --dry-run             dry run
        -k, --keep            keep downloaded pack
        --depth <depth>       deepen history of shallow clone
        --shallow-since <time>
                            deepen history of shallow repository based on time
        --shallow-exclude <revision>
                            deepen history of shallow clone, excluding rev
        --deepen <n>          deepen history of shallow clone
        --unshallow           convert to a complete repository
        --update-shallow      accept refs that update .git/shallow
        --refmap <refmap>     specify fetch refmap
        -o, --server-option <server-specific>
                            option to transmit
        -4, --ipv4            use IPv4 addresses only
        -6, --ipv6            use IPv6 addresses only
        --negotiation-tip <revision>
                            report that we have only objects reachable from this object
        --show-forced-updates
                            check for forced-updates on all updated branches
        --set-upstream        set upstream for git pull/fetch

## Sources:

Git Credential Store Documentation: [https://git-scm.com/docs/git-credential-store](https://git-scm.com/docs/git-credential-store)

Cache GitHub Credentials in Git: [https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git)

Creating a Personal Access Token: [https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

<a href="#git-configuration" style="color:orange;text-decoration:none">??? To Top ???</a>
