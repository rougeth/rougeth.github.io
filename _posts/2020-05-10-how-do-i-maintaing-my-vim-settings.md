---
layout: post
title: How do I maintaing my Vim settings
language: en
translation: /blog/como-mantenho-minhas-configuracoes-do-vim
date: 2020-05-10 15:21 +0100
---
My first contact with the text editor Vim was when I've just started college, in a Math class almost 10 years ago. Before the class started, a classmate, Dirley, that I didn't meet yet, was sitting in the front rows with his laptop open working on some project.

Black screen divided in half, at one side texts with coloured fonts and the other lines and more lines scrolling across the screen. Whenever Dirley pressed some keys, everything moved and changed. He was in the Matrix! If he offered me a red pill, I'd accept without thinking twice!

And this is how I got to know Vim. As soon as I started learning about it, I got impressed by how beloved that text editor was and the size of its community—millions of plugins, themes, shortcuts and settings. Suddenly, I was part of it. Countless hours spent trying ~~to exit vim~~ new plugins, changing settings, getting new colour schemes, and starting over again because it stopped working.

Until one day I decided to learn for real what I could and wanted to change inside Vim. Since then, for at least 6 years ago, I mostly use the setting structure, changing just a few things over the years.

In this blog post, I won't talk about which setting or plugin you must use, but how to organize it for the long term use and how to not get lost while trying new things.

## Divide and conquer

The `.vimrc` is the file that Vim searches for user configurations. In my case, I divided it into 4 different files, making the `.vimrc` just as an aggregator. The idea of this structure came from my dear friend [Humberto](https://humberto.io/), who taught me a lot about Vim.

```vim
" Vim Settings
source ~/.vim/config.vim

" Plugins I use
source ~/.vim/plugins.vim

" Plugin settings
source ~/.vim/plugin_config.vim

" Shortcuts
source ~/.vim/shortcuts.vim
```

## Vim settings

Every configuration we can change on Vim, except for shortcuts, goes to config.vim file. As a guide to choosing what and how to configure the edit, I used a lot [Vim's official documentation](https://vimhelp.org/), in particular the [options section](https://vimhelp.org/options.txt.html#options.txt). You can read the documentation at the [vimhelp.org](https://vimhelp.org) website, but if you access it from inside Vim, here it goes some tips:

- `:help` to access the home page;
- `:options` sends you to the options section;
- To go directly to a specific section, put the cursor above its name and press `CTRL-]`;
- To go back where you were, press `CTRL-O`.

One of the configurations I like the most, is to be able to open a file on Vim with the cursor in the same place it was when I close the file for the last time:

```vim
au BufReadPost * if line("'\"") > 0|if line("'\"") <= line("$")|exe("norm '\"")|else|exe "norm $"|endif|endif
```

Check out the rest of my setting at [config.vim](https://github.com/rougeth/dotvim/blob/master/config.vim).

## Plugins

I listed every plugin in the `plugins.vim` file and I installed them using `vim-plug`. Until version 8, released in 2016, Vim required a plugin, like vim-plug, to install other plugins. Since `vim-plug` always worked with me, I didn't migrate to the native option.

The 3 plugins I like the most are:
- [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim): Allows you to search for files in the directory Vim was opened. It's fast and without a doubt the one I use the most.
- [NERDTree](https://github.com/preservim/nerdtree): It's like the Finder from MacOS or Explorer from Windows. I use it a lot when I don't know well the structure of the project I'm working.
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter): Tells you which lines were added, changed or removed according to Git.

Example of how to use `vim-plug` to install the 3 plugins above:

```vim
" Activate vim-plug
call plug#begin()

Plug 'scrooloose/nerdtree'
Plug 'kien/ctrlp.vim'
Plug 'airblade/vim-gitgutter'

" You can install any plugin directly from Github:
" Plug 'profile/plugin'

" All plugins must be listed between the `plug#begin()` and `plug#end()`
call plug#end()
```

## Plugins settings

Each plugin has a set of configurations you can change, e.g. shortcuts to open `ctrl.vim` and `NERDTree`. At that time, I chose to break the plugin settings into a different file, `plugin_config.vim`. I'd do it differently today. Since I don't use many plugins, a single file to install and configure them would be enough.

## Shortcuts

The last time the `shortcuts.vim` file was modified was 5 years ago, when I reorganized the repository. I limited myself to just a few changes, since Vim's shortcuts make you productive, despite being hard to learn. Besides that, not being creative on shortcuts helps you whenever you have to use Vim in a computer without your configurations, like when accessing a remote server or pairing with someone else computer.

The shortcut I use the most is `jj`, that I mapped to `ESC` key, so, when I type `jj`, Vim understand as the ESC key:

```vim
imap jj <esc>
```

---

Every file I talked about can be found on [this repository](https://github.com/rougeth/dotvim). You can follow the README.me instructions to install them or you fork it and add your settings.

![Meme Fork All The Things](/assets/fork-all-the-things.jpg)

Remember, to exit Vim: `:q`

**o/**
