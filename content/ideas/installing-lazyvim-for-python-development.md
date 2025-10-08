<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


<h1 style="text-align: center;">SUMMARY</h1>

```bash
# This installation assumes your OS is Ubuntu 24.04 or latter
#
# Sources:
#     LazyVim - https://www.lazyvim.org/
#     Alacritty - https://alacritty.org/
#


# --------------------------- make a backup of your current nvim files ----------------------------

# required if you have nvim installed
mv ~/.config/nvim{,.bak}

# optional but recommended
mv ~/.local/share/nvim{,.bak}
mv ~/.local/state/nvim{,.bak}
mv ~/.cache/nvim{,.bak}

# --------------------- typical installation of alacritty, nvim, and lazyvim ----------------------

# update the packages on your system
sudo apt update && sudo apt upgrade

# include a gnome ready terminal
sudo apt install gnome-terminal

# install packages needed by alacritty
sudo apt install cmake g++ pkg-config libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3

# install the latest version of alacritty (lazyvim will be embedded in alacritty)
sudo snap install alacritty --classic

# install packages needed by nvim/lazyvim
sudo apt install wl-clipboard       # if your using X Window's Wayland protocol (other wise install 'xset')
sudo apt install ripgrep fzf        # ripgrep (executable is called `rg`) is need by lazyvim for telescope
sudo apt install git lazygit curl

# install the latest version of nvim
sudo snap install nvim --classic

# install lazyvim configuration files (this turns nvim into lazyvim)
git clone https://github.com/LazyVim/starter ~/.config/nvim
rm -rf ~/.config/nvim/.git          # remove the .git folder, so you can add it to your own repo later

# ------------------------------ initialize lazyvim by starting nvim ------------------------------

# execute nvim and it will become a lazyvim installation via the configuration you installed above
nvim

# after installation enter this nvim command, this will load all plugins and check if everything is working correctly
:LazyHealth

```


---------------


# CircuitPython Development Workflow with NeoVim/LazyVim
Using LazyVim for CircuitPython development gives you a modern, feature-rich editing experience,
but we must make NeoVim's language server aware of the specific CircuitPython libraries since they are not in the standard Python environment.
We must also assure that NeoVim/LazyVim honors CircuitPython's REPL strategy,
all the while keeping control of what coding is going to our development environment vs what is within the microcontroller.
A nice feature of the REPL is that CircuitPython detects when the files are changed/written on the board
and will automatically re-start your code.
This makes coding very fast because you save, and it re-runs.

A starter template for [LazyVim](https://github.com/LazyVim/LazyVim).
Refer to the [documentation](https://lazyvim.github.io/installation) to get started.

* [Zero to IDE with LazyVim](https://www.youtube.com/watch?v=N93cTbtLCIM)
* [Effective NeoVim Setup for Full-Stack Web Development in 2024](https://www.youtube.com/watch?v=V070Zmvx9AM)
* [LazyVim From Scratch To BEAST MODE](https://www.youtube.com/watch?v=evCmP4hH7ZU)
* [How I Setup Neovim To Make It AMAZING in 2024: The Ultimate Guide](https://www.youtube.com/watch?v=6pAG3BHurdM)
* [NeoVim with LazyVim: The most feature rich editor for programming](https://www.youtube.com/watch?v=lojAgyGnzc0&t=15s)
* [Switching To LazyVim](https://medium.com/unixification/switching-to-lazyvim-5d497c089c7b)


