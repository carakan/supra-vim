
(NEW) spf13-vim is a distribution of vim plugins and resources for Vim, Gvim and [MacVim].

It is a good starting point for anyone intending to use VIM for development running equally well on Windows, Linux, \*nix and Mac.

The distribution is completely customisable using a `~/.vimrc.local`, `~/.vimrc.bundles.local`, and `~/.vimrc.before.local` Vim RC files.

Unlike traditional VIM plugin structure, which similar to UNIX throws all files into common directories, making updating or disabling plugins a real mess, spf13-vim 3 uses the [Vundle] plugin management system to have a well organized vim directory (Similar to mac's app folders). Vundle also ensures that the latest versions of your plugins are installed and makes it easy to keep them up to date.

Great care has been taken to ensure that each plugin plays nicely with others, and optional configuration has been provided for what we believe is the most efficient use.

Lastly (and perhaps, most importantly) It is completely cross platform. It works well on Windows, Linux and OSX without any modifications or additional configurations. If you are using [MacVim] or Gvim additional features are enabled. So regardless of your environment just clone and run.

# Installation

Due by migrating to excellent Dein the installer and some of *Magic* plugins can't work fine:

## install of Dein
```
mkdir -p ~/.vim/bundle/repos/github.com/Shougo/dein.vim
git clone https://github.com/Shougo/dein.vim.git ~/.vim/bundle/repos/github.com/Shougo/dein.vim
```

#### Install [NeoVim]

use homebrew

```
brew install neovim
```

### Fork me on GitHub

I'm always happy to take pull requests from others. A good number of people are already [contributors] to [spf13-vim]. Go ahead and fork me.

# A highly optimized .vimrc config file

## Customization

Create `~/.vimrc.local` for any local
customizations.

For example, to override the default color schemes:

```bash
    echo colorscheme ir_black  >> ~/.vimrc.local
```

### Before File

Create a `~/.vimrc.before.local` file to define any customizations
that get loaded *before* the spf13-vim `.vimrc`.

For example, to prevent autocd into a file directory:
```bash
    echo let g:spf13_no_autochdir = 1 >> ~/.vimrc.before.local
```
For a list of available spf13-vim specific customization options, look at the `~/.vimrc.before` file.


### Fork Customization

There is an additional tier of customization available to those who want to maintain a
fork of spf13-vim specialized for a particular group. These users can create `.vimrc.fork`
and `.vimrc.bundles.fork` files in the root of their fork.  The load order for the configuration is:

1. `.vimrc.before` - spf13-vim before configuration
3. `.vimrc.before.local` - before user configuration
4. `.vimrc.bundles` - spf13-vim bundle configuration
6. `.vimrc.bundles.local` - local user bundle configuration
6. `.vimrc` - spf13-vim vim configuration
8. `.vimrc.local` - local user configuration

See `.vimrc.bundles` for specifics on what options can be set to override bundle configuration. See `.vimrc.before` for specifics
on what options can be overridden. 

Once you have this file in your repo, only the bundles you specified will be installed during the first installation of your fork.

You may also want to update your `README.markdown` file so that the `bootstrap.sh` link points to your repository and your `bootstrap.sh`
file to pull down your fork.

For an example of a fork of spf13-vim that provides customization in this manner see [taxilian's fork](https://github.com/taxilian/spf13-vim).

### Easily Editing Your Configuration

`<Leader>ev` opens a new tab containing the .vimrc configuration files listed above. This makes it easier to get an overview of your
configuration and make customizations.

`<Leader>sv` sources the .vimrc file, instantly applying your customizations to the currently running vim instance.

These two mappings can themselves be customized by setting the following in .vimrc.before.local:
```bash
let g:spf13_edit_config_mapping='<Leader>ev'
let g:spf13_apply_config_mapping='<Leader>sv'
```


## [NERDTree]

NERDTree is a file explorer plugin that provides "project drawer"
functionality to your vim editing.  You can learn more about it with
`:help NERDTree`.

**QuickStart** Launch using `<Leader>e`.

**Customizations**:

* Use `<C-E>` to toggle NERDTree
* Use `<leader>e` or `<leader>nt` to load NERDTreeFind which opens NERDTree where the current file is located.
* Hide clutter ('\.pyc', '\.git', '\.hg', '\.svn', '\.bzr')
* Treat NERDTree more like a panel than a split.

## [ctrlp]
Ctrlp replaces the Command-T plugin with a 100% viml plugin. It provides an intuitive and fast mechanism to load files from the file system (with regex and fuzzy find), from open buffers, and from recently used files.

**QuickStart** Launch using `<c-p>`.

## [Surround]

This plugin is a tool for dealing with pairs of "surroundings."  Examples
of surroundings include parentheses, quotes, and HTML tags.  They are
closely related to what Vim refers to as text-objects.  Provided
are mappings to allow for removing, changing, and adding surroundings.

Details follow on the exact semantics, but first, consider the following
examples.  An asterisk (*) is used to denote the cursor position.

      Old text                  Command     New text ~
      "Hello *world!"           ds"         Hello world!
      [123+4*56]/2              cs])        (123+456)/2
      "Look ma, I'm *HTML!"     cs"<q>      <q>Look ma, I'm HTML!</q>
      if *x>3 {                 ysW(        if ( x>3 ) {
      my $str = *whee!;         vllllS'     my $str = 'whee!';

For instance, if the cursor was inside `"foo bar"`, you could type
`cs"'` to convert the text to `'foo bar'`.

There's a lot more, check it out at `:help surround`

## [NERDCommenter]

NERDCommenter allows you to wrangle your code comments, regardless of
filetype. View `help :NERDCommenter` or checkout my post on [NERDCommenter](http://spf13.com/post/vim-plugins-nerd-commenter).

**QuickStart** Toggle comments using `<Leader>c<space>` in Visual or Normal mode.



## [AutoClose]

AutoClose does what you expect. It's simple, if you open a bracket, paren, brace, quote,
etc, it automatically closes it. It handles curlys correctly and doesn't get in the
way of double curlies for things like jinja and twig.

## [Fugitive]

Fugitive adds pervasive git support to git directories in vim. For more
information, use `:help fugitive`

Use `:Gstatus` to view `git status` and type `-` on any file to stage or
unstage it. Type `p` on a file to enter `git add -p` and stage specific
hunks in the file.

Use `:Gdiff` on an open file to see what changes have been made to that
file

**QuickStart** `<leader>gs` to bring up git status

**Customizations**:

 * `<leader>gs` :Gstatus<CR>
 * `<leader>gd` :Gdiff<CR>
 * `<leader>gc` :Gcommit<CR>
 * `<leader>gb` :Gblame<CR>
 * `<leader>gl` :Glog<CR>
 * `<leader>gp` :Git push<CR>
 * `<leader>gw` :Gwrite<CR>
 * :Git ___ will pass anything along to git.

![fugitive image][fugitive-img]



# Intro to VIM

Here's some tips if you've never used VIM before:

## Tutorials

* Type `vimtutor` into a shell to go through a brief interactive
  tutorial inside VIM.
* Read the slides at [VIM: Walking Without Crutches](https://walking-without-crutches.heroku.com/#1).

## Modes

* VIM has two (common) modes:
  * insert mode- stuff you type is added to the buffer
  * normal mode- keys you hit are interpreted as commands
* To enter insert mode, hit `i`
* To exit insert mode, hit `<ESC>`

## Useful commands

* Use `:q` to exit vim
* Certain commands are prefixed with a `<Leader>` key, which by default maps to `\`.
  Spf13-vim uses `let mapleader = ","` to change this to `,` which is in a consistent and
  convenient location.
* Keyboard [cheat sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif).