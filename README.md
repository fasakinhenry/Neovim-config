# Neovim-config
My personal Setup files for Neoconfig

How to install and setup neovim with awesome plugins

Welcome to my blog. If you are readng this article from me then you are in luck. In this article I am going to walk you through a step by step approach to setup Neovim from scratch with some awesome features.

This tutorial applies to both linux users and Windows users. I mean the bosses Mac users can also take a peep it should work for you guys too. I don't really know 😂😜. In simple terms the process we are going to be adopting in this tutorial is a Linux process, therefore if you are on windows you will have to install WSL. If you are a windows user you must install WSL before taking this tutorial. (That should be my first warning of the day, innit? Expect more😂😂😎)

The end result of our configuration in this article has the following features:

- Easy file browsing with GUI 👍
- capability to open node tree( I mean file tree on the side)
- Error line and a status bar
- accessibility to a tagbar (magic triggered by F8🤯)
- Code completion for different languages(one of the most important😎, I bet yyou have that not. I mean a normal powerful code editor should have that).
- Different colorscheme.
- Shortcut integration for multiline commenting


# Installation of Neovim

You can skip this part if you have not installed Neovim. As a linux user you should have that not because it is a must have but I mean it is super cool. Neovim can be installed on different Linux distributions (Ubuntu, Debian etc)

Moving on, let's go through the steps involved.

- Access your terminal 👀 (on windows if you are using WSL you can also search "ubuntu" if ubuntu was installed)
- Optionally you can run:
sudo apt update
- Thereafter run the command:
sudo apt install neovim
- Once the installation is finished you can just type nvim to  confirm the installation or go on to test with a new file directly by typing:
nvim test.txt

# custom configuration

It's go time! Let's get to the icing on the cake🙌🚀

- check if you have any previous configuration by typing "ls -la in the terminal". if you can't find the .config directory then you will have to create one using the code:
mkdir .config
 
- Also enter the .config directory(Please don't neglect the "." before the config. It shows that it is a hidden directory and also helps the configuration to target the certain directory). Use the command below to navigate into the .config directory:
cd .config/

- Make another directory called nvim in the .config directory.

```
mkdir nvim
```

- Enter the created directory.

```
cd nvim
```
- Create a new file called "init.vim". This is more like our configuration file.

```
nvim init.vim
```
# writing codes to configure each functionality

It's going to be a long one but is it worth it?🥴🧐🤐🤨 Give me the benefit of the doubt.

in the init.vim write the following codes:

```
:set number
:set relativenumber
```

hit escape and write :wq to save the progress of the configuration.

retype "nvim init.vim" to see the changes. That's how we roll😎.

Access this link to get all the init.vim for the whole process to make this easier.

```
https://github.com/fasakinhenry/Neovim-config/blob/master/init.vim
```
Just copy and paste the contents into your init.vim or you just follow through this article.

Back to the conversation here. Add more codes to the "init.vim" file.

```
:set autoindent
:set tabstop=4
:set shiftwidth=4
:set smarttab
:set softtabstop=4
:set mouse=a
```
hint: when you want to copy these codes directly just copy the codes above. Then in your "init.vim" file. press 'Esc' followed by command :set paste. Then you hold 'shift' and right click your mouse to paste😴🥱😓 too long🥴

# Adding plugins 🚀

We have to install a tool that allows us to install plugins. Yes we really need that. You can just search "vim-plug" to learn more. No much hassles I will show you the full tip here.

Access the link below:

https://github.com/junegunn/vim-plug

scroll down in the Readme of that repository to the Neovim section to copy the code there. it's too much stress? here is the code: (Warning first: second warning😂😂😂. Be careful when copying linux codes especially ones with sh and curl. But you can trust me innit?)

```
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```
In case you get an error curl is not installed, you can run the following code in your terminal:

```
sudo apt install curl
```
All these codes will be run inside the .config/nvim folder take note.

To initiate the plugins add the following codes to your init.vim file.

```
call plug#begin()
call plug#end()
```

All the codes for our plugin call would be between the codes above.Basically, the format for calling a plugin is generally to write:

plug 'link to the plugin page(github repository)'

# My custom plugins

- Airline plugin
This plugin shows a nice status bar in your nvim IDE

```
Plug 'https://github.com/vim-airline/vim-airline'
```

Note: you will need git to run this plugin so you have to install git by running:

```
sudo apt install git
```

Go back to your init.vim file "nvim init.vim" and press 'Esc' and write :PlugInstall to install the vim plugin.

Note: You may see that there are some broken icons you will have to install some special fonts on windows. 

- Nerdtree
This plugin allows us to have a visible file tree like VSCODE file sidebar🙌.

```
Plug 'https://github.com/preservim/nerdtree'
```

Install it again by opening "init.vim" file and pressing 'ESC' and type :PlugInstall. Take note of this part. This is how you will be installing all the plugins.

Run this plugin by hitting 'Esc' and typing :NERDTreeFocus to see the effect.

In the case that you see some broken symbols in the file tree on windows. you can type these following codes in your "init.vim" folder.

```
let g:NERDTreeDirArrowExpandable="+"
let g:NERDTreeDirArrowCollapsible="~"
```

I made this simpler also. Instead of having to write the command :NERDTreeFocus every time and so on. Just write these codes in your "init.vim" file

```
nnoremap <C-f> : NERDTreeFocus<CR>
nnoremap <C-n> : NERDTree<CR>
nnoremap <C-t> : NERDTreeToggle<CR>
```

With that setup, you can easily toggle the nerd tree(file tree GUI) with 'CTRL + t'.

- Commenting using gcc and gc

```
Plug 'https://github.com/tpope/vim-commentary'
```

- Surrounding ysw)

```
Plug 'https://github.com/tpope/vim-surround'
```

- CSS Color preview

```
Plug 'https://github.com/ap/vim-css-color'
```
- Retro schemes
A list of schemes that you can add to beautify and colorize your code Editor

```
Plug 'https://github.com/rafi/awesome-vim-colorschemes'
```

To use this you just need to type this when using the editor:

```
:colorscheme <scheme>
```

for example

```
:colorscheme jellybeans
```

In order to avoid setting this for every file opened you can just add the code to the Neovim setup ( I mean the "init.vim" file add the code below)

```
:colorscheme jellybeans
```

Additionally you can add the code:

```
:set completeopt=preview
```

That code is useful for no preview.

- Developer Icons

```
Plug 'https://github.com/ryanoasis/vim-devicons'
```
- Vim terminal

```
Plug 'https://github.com/tc50cal/vim-terminal'
```

To access the terminal *run :TerminalSplit* bash

- Multiple cursors (ctrl + N)

```
Plug 'https://github.com/terryma/vim-multiple-cursors'
```

- Tagbar for code navigation

```
Plug 'https://github.com/preservim/tagbar'
```

Note: To use this package you need to install exuberant ctags. You can install it by running:

```
sudo apt install exuberant-ctags
```

To use this plugin just run the command :TagbarToggle and you will see the tagbar opened. You can also run it again to close the tagbar. Another bonus💪💪 is that you can map the tagbar toggling to a key(in our case f8) by adding this line to our "init.vim" file.

```
nmap <f8> :TagbarToggle<CR>
```

- Auto completion 😎🙌💪

This plugin allows for auto-completion of codes. It is a little bit tricky to install but it is cool. First, add the code completion plugin by adding the code below to the "init.vim" in between the plug#begin and plug#end like the others:

```
Plug 'https://github.com/neoclide/coc.nvim"
```

This plugin is only available for Neovim and it is very special.

You will get some problems when you install this (using :PlugInstall) because node may not be installed. Install node first.

```
sudo apt install nodejs

Install npm too.

sudo apt install npm
```
The problem here is that different languages have their own required modules to be installed so I may not talk about that here. Instead check this repository "https://github.com/neoclide/coc.nvim"

After that, navigate to the plugged directory(cd plugged/) enter the coc.nvim directory(cd coc.nvim), and then install yarn.

```
sudo npm install -g yarn
```

Also run:

```
yarn install
```

Call yarn build:

```
yarn build
```
Go back to the config directory (cd ..; cd ..)

The plugin works but the language completion has to be implemented. The best way to do this is for a language(for example, Python). You have to run this command when you open a .py file:

```
:CocInstall coc-python
```

For Python, you also have to install a language server using pip. If you don't have pip installed. Use:

```
sudo apt install python3-pip
```

Use pip to install jedi

```
pip3 install jedi
```

With this, you have an auto-completion set for Python checkout for your language.

After writing these plugins. Exit the init.vim and open it again you will have to now *run :PlugInstall* again

# Deleting unwanted plugins

In the case you want to delete a plugin that was already added all you have to do is to remove the line handling the plugin in the "init.vim" file. Thereafter, you need to run *:PlugClean*.😎😎

My name is Henry Fasakin and I am a devoted web developer and Product designer. You can follow me up using these links:

[X profile](https://x.com/henqsoft)
[Facebook](https://facebook.com/henry.fasakin.7)
[Linkedin](https://www.linkedin.com/in/fasakin-henry/)
