---
title: "Installation_lazyvim_guide"
date: 2024-08-26
categories:
  - base_tech
tags:
  - vimtoide
---
1. Reference:

   - [Zero2IDE_guide_video](https://www.youtube.com/watch?v=N93cTbtLCIM)

2. Install the right version of <u>Nvim v0.10.0</u> via [Github download link ](https://github.com/neovim/neovim/releases/tag/v0.10.0) on my home-ubuntu-pro

   ```shell
   # download the tar.gz
   wget https://github.com/neovim/neovim/releases/download/v0.10.0/nvim-linux64.tar.gz
   
   # untar of it
   tar zxvf nvim-linux64.tar.gz
   
   # intall the gcc\clang
   sudo apt install fuse
   sudo apt install gcc
   sudo apt install clang
   
   # add nvim to system PATH(key step)
   vim ~/.zshrc
   export PATH=$PATH:/home/jimmy/nvim-linux64/bin
   source ~/.zshrckey step
   
   # comfirm the version of nvim
   nvim --version
   NVIM v0.10.0
   Build type: Release
   LuaJIT 2.1.1713484068
   Run "nvim -V1 -v" for more info
   ```


2. check the SHA256 value

   ```shell
   # sha256 value check(for v0.10.0)
   sha256sum nvim-linux64.tar.gz
   be1f0988d0de71c375982b87b86cd28d2bab35ece8285abe3b0aac57604dfc5a  nvim-linux64.tar.gz
   ```

3. uninstall the current version of nvim

   ```shell
   rm -rf ~/.config/nvim
   # if install by apt
   sudo apt remove neovim
   sudo apt purge neovim
   sudo apt autoremove
   # confirm it removed from ubuntu
   nvim --version
   Command 'nvim' not found, but can be installed with:
   sudo snap install nvim    # version v0.10.0, or
   sudo apt  install neovim  # version 0.6.1-3
   See 'snap info nvim' for additional versions.
   ```

4. Installation of [lazyvim](http://www.lazyvim.org/installation)

   ```shell
   # Make a backup of your current Neovim files:
   # required
   mv ~/.config/nvim{,.bak}
   
   # optional but recommended
   mv ~/.local/share/nvim{,.bak}
   mv ~/.local/state/nvim{,.bak}
   mv ~/.cache/nvim{,.bak}
   
   # Clone the starter
   git clone https://github.com/LazyVim/starter ~/.config/nvim
   
   # Remove the .git folder, so you can add it to your own repo later
   rm -rf ~/.config/nvim/.git
   
   # Start to see the magic
   nvim
   ```

5. check the health of nvim

```shell
# use :checkhealth to check if there are some error of nvim,I found lack of luarocks
  sudo apt update\nsudo apt install build-essential libreadline-dev unzip
  sudo apt install lua5.3 luarocks
  
# put the luarocks into PATH
vim ~/.zshrc
export PATH=$PATH:/usr/local/bin
source ~/.zshrc

# check if all is correct
luarocks --version

╭─ ~/.config                                                jimmy@myubuntu2204 21:32:01
╰─❯ luarocks --version
/usr/bin/luarocks 3.8.0
LuaRocks main command-line interface
```


