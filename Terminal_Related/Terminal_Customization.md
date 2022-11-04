<h1 style="color:#FF8C00">🎃 Terminal Customization</h1>

![Testing](https://i.imgur.com/YRRZIh9.png)

## Table of Contents
[Installation Instructions](#installation-instructions)

## Installation Instructions

### Starship

Step 1. Install Starship from the terminal

```Bash
curl -sS https://starship.rs/install.sh | sh
```

Step 2. Setup Bash to initialize with Starship

```Bash
eval "$(starship init Bash)"
```

Step 3. Install Nerd Font

1. Navigate to the [Nerd Fonts](https://www.nerdfonts.com/font-downloads) website
2. Download your selected font
2. Create a directory for fonts in HOME
    ```Bash
    sudo mkdir ~/.fonts
    ```
4. Unzip the fonts zipped folder (this will unzip into the Downloads folder)
    ```Bash
    unzip <filename> 
    ```
5. Copy the contents into the .fonts folder (this will move _every_ file in the Downloads folder so use with caution)
    ```Bash
    mv * ~/.fonts
    ```
6. Refresh the cache and install all fonts
    ```Bash
    fc-cache -vf ~/.fonts
    ```

7. Start configuring Starship by navigating to [Starships website](https://starship.rs/guide/) and play around
8. If you want a quick start to see if you like it or not, you can download a complete starship.toml file from my [gists](https://gist.github.com/4x32GB/6be49ac127b60019e4d617617c74fc84)
***Fair warning: My prompt is highly customized and has several features I love that you may not!***