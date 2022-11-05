<h1 style="color:#FF8C00">🎃 Terminal Customization</h1>

<img src="https://i.imgur.com/YRRZIh9.png" alt="Screenshot of customized terminal" height=600>

## Table of Contents
[Installation Instructions](#installation-instructions)

[Custom Starship Configuration](#custom-starship-terminal-toml-file)

## Installation Instructions

### Starship

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

***Fair warning: My prompt is highly customized and has several features I love that you may not!***

### Custom Starship Terminal TOML File

```bash
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
    [username]
    show_always = true
    style_user = "bg:#FF19B6"
    style_root = "bg:#FF19B6"
    format = '[ $user]($style)'

    # Display the hostname
    [hostname]
    ssh_only = false
    style = "bg:#FF19B6"
    format = '[@$hostname ]($style)'
    disabled = false

    [directory]
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