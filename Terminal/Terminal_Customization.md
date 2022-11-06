# Terminal Customization

<details>
    <summary>Table of Contents</summary

[About This Project]()

[Starship Install](#starship-install)

[Starship Uninstall](#starship-uninstall)

[Custom Starship Configuration](#custom-starship-terminal-toml-file)

[Oh-My-Posh Install](#oh-my-posh-install)

* [Homebrew Install](#install-homebrew)

[Oh-My-Posh Uninstall](#oh-my-posh-uninstall)

* [Homebrew Uninstall](#uninstall-homebrew)

[Oh-My-Posh Custom Theme Configuration](#oh-my-posh-custom-theme-configuration)

[Oh-My-Posh Custom Themes](#oh-my-posh-custom-themes)

[License]()
        
[Acknowledgments]()

</details>
        
## About This Project
        
**_Beaut-ifying_** the terminal, no matter which shell you use, is not a new concept, but it has gotten better over the years. This project is not a project per se, but it's a collection of notes formatted in the vision that it's a guide to complete the setup of _your_ terminal. I've always had difficulties figuring out how to write notes for myself, but never had issues teaching other people about said thing. I hope it serves you well and you can feel confident in creating your own, custom, terminal.
       
## Starship Install

Step 1. Install Starship from the terminal

```Bash
curl -sS https://starship.rs/install.sh | sh
```

Step 2. Create Starship.toml file & .config if it does not exist already

```bash
mkdir -p ~/.config && touch ~/.config/starship.toml
```

Step 3. Setup Bash to initialize with Starship

```Bash
sudo nano ~/.config/starship.toml

# Add the following line to the end of the file
↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓

eval "$(starship init bash)"
```
>**_NOTE:_** Make sure you type 'bash' and not 'Bash' since technically 'Bash' is not a shell

Step 4. Install Nerd Font

* Navigate to the [Nerd Fonts](https://www.nerdfonts.com/font-downloads) website

* Download your selected font

* Create a directory for fonts in Home

    ```Bash
    sudo mkdir ~/.fonts
    ```
* Unzip the fonts zipped folder (this will unzip into the Downloads folder)

    ```Bash
    unzip <filename> 
    ```
* Copy the contents into the .fonts folder (this will move _every_ file in the Downloads folder so use with caution)

    ```Bash
    mv * ~/.fonts
    ```

* Refresh the cache and install all fonts

    ```Bash
    fc-cache -vf ~/.fonts
    ```

* Start configuring Starship by navigating to [Starship's website](https://starship.rs/guide/) and play around

* If you want a quick-start to see if you like it or not, you can copy it from the below code-block.

> **_Fair warning:_** My prompt is highly customized and has several features I love that you may not!

## Starship Uninstall

Uninstalling Starship is even easier than it was to install it. Similar to the install process and the one-liner used, all we need to do to uninstall Starship is run the below command (on Linux):

```bash
sudo sh -c 'rm "$(command -v 'starship')"'
```

This will remove the Starship binary from your machine, and you could even run your distro's form of 'autoremove' to remove any dependencies it may have had:

```bash
sudo dnf autoremove
```

### Custom Starship Terminal TOML File

[➡ Download Starship.toml Here ⬅](https://gist.github.com/4x32GB/6be49ac127b60019e4d617617c74fc84/archive/4f541ee0bf1e5a7a5939c1535f6b76667febfb59.zip)


<details>
    <summary>Starship Config Contents</summary>

```toml
    format = """
    [](#FF19B6)\
    $username\
    $hostname\
    [](bg:#DA627D fg:#FF19B6)\
    $directory\
    [](fg:#DA627D bg:#FCA17D)\
    $git_branch\
    $git_status\
    [](fg:#FCA17D bg:#86BBD8)\
    $c\
    $elixir\
    $elm\
    $golang\
    $haskell\
    $java\
    $julia\
    $nodejs\
    $nim\
    $package\
    $python\
    $rust\
    $scala\
    [](fg:#86BBD8 bg:#06969A)\
    $docker_context\
    [](fg:#06969A bg:#D9001D)\
    [ ](fg:#D9001D)\
    $line_break\
    [](#66324E)\
    $memory_usage\
    [ ](fg:#66324E)\
    $line_break\
    [](#D9001D)\
    $time\
    [ ](fg:#D9001D)\
    $line_break\
    >_  (fg:#FA11F2)\
    """

    # Disable the blank line at the start of the prompt
    add_newline = false


    # You can also replace your username with a neat symbol like  to save some space
    [username]```bash
    format = """
    [](#FF19B6)\
    $username\
    $hostname\
    [](bg:#DA627D fg:#FF19B6)\
    $directory\
    [](fg:#DA627D bg:#FCA17D)\
    $git_branch\
    $git_status\
    [](fg:#FCA17D bg:#86BBD8)\
    $c\
    $elixir\
    $elm\
    $golang\
    $haskell\
    $java\
    $julia\
    $nodejs\
    $nim\
    $package\
    $python\
    $rust\
    $scala\
    [](fg:#86BBD8 bg:#06969A)\
    $docker_context\
    [](fg:#06969A bg:#D9001D)\
    [ ](fg:#D9001D)\
    $line_break\
    [](#66324E)\
    $memory_usage\
    [ ](fg:#66324E)\
    $line_break\
    [](#D9001D)\
    $time\
    style = "bg:#DA627D"
    format = "[ $path ]($style)"
    truncation_length = 3
    truncation_symbol = "…/"

    [line_break]
    disabled = false

    [memory_usage]
    disabled = false
    threshold = -1
    format ='[ ${ram} @ ${ram_pct}]($style)'
    style = "bg:#66324E"


    [time]
    disabled = false
    use_12hr = true
    time_format = "%A %B %d %Y @ %r"
    style = "bg:#D9001D"
    format = '[ $time ]($style)'


    # Here is how you can shorten some long paths by text replacement
    # similar to mapped_locations in Oh My Posh:
    [directory.substitutions]
    "Documents" = " "
    "Downloads" = " "
    "Music" = " "
    "Pictures" = " "
    # Keep in mind that the order matters. For example:
    # "Important Documents" = "  "
    # will not be replaced, because "Documents" was already substituted before.
    # So either put "Important Documents" before "Documents" or use the substituted version:
    # "Important  " = "  "

    [c]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [docker_context]
    symbol = " "
    style = "bg:#06969A"
    format = '[ $symbol $context ]($style) $path'

    [elixir]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [elm]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [git_branch]
    symbol = " "
    style = "bg:#FCA17D"
    format = '[ $symbol $branch ]($style)'

    [git_status]
    style = "bg:#FCA17D"
    format = '[$all_status$ahead_behind ]($style)'

    [golang]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [haskell]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [java]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [julia]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [nodejs]
    symbol = ""
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [nim]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [package]
    symbol = " "

    [python]
    symbol = " "

    [rust]
    symbol = ""
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'

    [scala]
    symbol = " "
    style = "bg:#86BBD8"
    format = '[ $symbol ($version) ]($style)'
```

</details>

---

<figure>
    <img src="https://i.imgur.com/oCjJvPB.png" alt="oh-my-posh terminal" height=600>
    <figcaption style="text-align:center;">Oh-My-Posh w/ Quick-Term Theme</figcaption>
</figure>

## Oh-My-Posh Install

Similar to the installation instructions for Starship, I will primarily be covering the process on Linux distributions. If you already have Oh-My-Posh installed on Windows, you can check out my [Microsoft PowerShell Profile Gist](https://gist.github.com/4x32GB/d94e1475587d100d336b79aa4187246c). _Credit: Scott Hanselman_

Installing Oh-My-Posh is actually extremely using, albeit, you do need to install another package manager to be able to install it. In the section below, I cover how to install _Homebrew_, but once you finish that step, pop back up here and running the following two commands:

```
brew install jandedobbeleer/oh-my-posh/oh-my-posh
```

```bash
brew update && brew upgrade oh-my-posh
```

> ### Install Homebrew
> 
> Homebrew is essentially another package manager, but much like something similar to RPM Fusion. Homebrew allows you to install packages that would not > normally be provided with your distribution or install of MacOS. Installing Homebrew is a fairly straight-forward process, but much like anything with > Linux, things can get complicated fast.
> 
> ```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
> ```
> 
> Don't want to have to actually do anything?
> 
> ```bash
> NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/> > install.sh)"
> ```
> 
> After installing Homebrew, we'll then want to make sure that we add Homebrew to not only our _PATH_ but also to our bash shell profile. Since I am on > Fedora, it would be adding it to ~/.bash_profile
> 
> ```bash
> test -d ~/.linuxbrew && eval "$(~/.linuxbrew/bin/brew shellenv)"
> test -d /home/linuxbrew/.linuxbrew && eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
> test -r ~/.bash_profile && echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.bash_profile
> echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.profile
> ```
## Oh-My-Posh Uninstall

> ### Uninstall Homebrew
> 
> ```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
> ```
> 
> Don't want to have to actually do anything?
> 
> ```bash
> NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/> > uninstall.sh)"
> ```

## Oh-My-Posh Custom Theme Configuration

Below is a few themes that I have customized to my liking, so feel free to copy the contents and paste into their respective theme file. Make sure you change the theme that will be initialized. For example, the below code snippet is at the end of my **_.bashrc_** file to initialize the Quick-Term theme:

```bash
eval "$(oh-my-posh init bash --config $(brew --prefix oh-my-posh)/themes/quick-term.omp.json)"
```

To reload your profile to see changes immediately instead of closing your terminal and re-launching, run the following command:

```bash
eval "$(oh-my-posh init bash --config $(brew --prefix oh-my-posh)/themes/quick-term.omp.json)"
```

## Oh-My-Posh Custom Themes

<details>
    <summary>Wholespace</summary>

```json
    {
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "blocks": [
    {
      "alignment": "left",
      "segments": [
        {
          "background": "#FEF5ED",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "properties": {
            "macos": "\uf179 ",
            "ubuntu": "\uf31b ",
            "windows": " "
          },
          "style": "diamond",
          "template": "{{ .UserName }} on {{ .HostName }} \uf817 {{ if .WSL }}WSL at {{ end }}{{.Icon}}",
          "trailing_diamond": "<transparent,#FEF5ED>\ue0b2</>",
          "type": "os"
        },
        {
          "background": "#FEF5ED",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "properties": {
            "time_format": "January 2, 2006 @ 3:04:05 PM"
          },
          "style": "diamond",
          "template": " \u2665 {{ .CurrentDate | date .Format }} ",
          "trailing_diamond": "<transparent,#FEF5ED>\ue0b2</>",
          "type": "time"
        },
        {
          "background": "#516BEB",
          "foreground": "#ffffff",
          "leading_diamond": "\ue0b2",
          "style": "diamond",
          "template": "\uf85a CPU: {{ round .PhysicalPercentUsed .Precision }}% | ",
          "type": "sysinfo"
        },
        {
          "background": "#516BEB",
          "foreground": "#ffffff",
          "style": "diamond",
          "template": "RAM: {{ (div ((sub .PhysicalTotalMemory .PhysicalFreeMemory)|float64) 1000000000.0) }}/{{ (div .PhysicalTotalMemory 1068786176.0) }}GB \uf85a ",
          "trailing_diamond": "<transparent,#516BEB>\ue0b2</>",
          "type": "sysinfo"
        },
        {
          "background": "#575656",
          "foreground": "#d6deeb",
          "leading_diamond": "\ue0b2",
          "properties": {
            "style": "roundrock",
            "threshold": 0
          },
          "style": "diamond",
          "template": " {{ .FormattedMs }} ",
          "trailing_diamond": "\ue0b0",
          "type": "executiontime"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "right",
      "segments": [
        {
          "background": "#ffffff",
          "foreground": "#000000",
          "leading_diamond": "\ue0b2",
          "properties": {
            "fetch_package_manager": true,
            "npm_icon": " <#cc3a3a>\ue5fa</> ",
            "yarn_icon": " <#348cba>\uf61a</>"
          },
          "style": "diamond",
          "template": "\ue718 {{ if .PackageManagerIcon }}{{ .PackageManagerIcon }} {{ end }}{{ .Full }}",
          "trailing_diamond": "<transparent,#ffffff>\ue0b2</>",
          "type": "node"
        },
        {
          "background": "#17D7A0",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "properties": {
            "branch_icon": "\ue725 ",
            "fetch_stash_count": true,
            "fetch_status": true,
            "fetch_upstream_icon": true,
            "fetch_worktree_count": true
          },
          "style": "diamond",
          "template": " {{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \uf692 {{ .StashCount }}{{ end }} ",
          "trailing_diamond": "\ue0b0",
          "type": "git"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "foreground": "#ffafd2",
          "properties": {
            "folder_icon": "\uf07b",
            "home_icon": "home",
            "style": "agnoster_full"
          },
          "style": "diamond",
          "template": " \ue5ff {{ .Path }} ",
          "type": "path"
        },
        {
          "foreground": "#00ff15",
          "foreground_templates": ["{{ if gt .Code 0 }}#ff0000{{ end }}"],
          "properties": {
            "always_enabled": true
          },
          "style": "plain",
          "template": " \uf7d4 ",
          "type": "exit"
        }
      ],
      "type": "prompt"
    }
  ],
  "console_title_template": "{{ .Folder }}",
  "transient_prompt": {
    "background": "transparent",
    "foreground": "#FEF5ED",
    "template": "\ue285 "
  },
  "version": 2
}
```

</details>
