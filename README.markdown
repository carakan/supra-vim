(NEW) SUPRA (spf13)-vim is a distribution of vim plugins and resources for Vim, Gvim and [MacVim].

It is a good starting point for anyone intending to use VIM for development running equally well on Windows, Linux, \*nix and Mac.

The distribution is completely customisable using a `~/.vimrc.local`, `~/.vimrc.bundles.local`, and `~/.vimrc.before.local` Vim RC files.

# Installation

## Requirements

#### Install [NeoVim]

use homebrew

```zsh
brew install neovim
```

#### Installation

```zsh
curl https://raw.githubusercontent.com/carakan/supra-vim/master/bootstrap.sh -L > supra-vim.sh && sh supra-vim.sh
```

# A highly optimized .vimrc config file

## Customization

Create `~/.vimrc.local` for any local
customizations.

For example, to override the default color schemes:

```zsh
    echo colorscheme ir_black  >> ~/.vimrc.local
```

### Before File

Create a `~/.vimrc.before.local` file to define any customizations
that get loaded _before_ the spf13-vim `.vimrc`.

For example, to prevent autocd into a file directory:

```bash
    echo let g:spf13_no_autochdir = 1 >> ~/.vimrc.before.local
```

For a list of available spf13-vim specific customization options, look at the `~/.vimrc.before` file.

### Fork Customization

There is an additional tier of customization available to those who want to maintain a
fork of spf13-vim specialized for a particular group. These users can create `.vimrc.fork`
and `.vimrc.bundles.fork` files in the root of their fork. The load order for the configuration is:

1. `.vimrc.before` - spf13-vim before configuration
2. `.vimrc.before.local` - before user configuration
3. `.vimrc.bundles` - spf13-vim bundle configuration
4. `.vimrc.bundles.local` - local user bundle configuration
5. `.vimrc` - spf13-vim vim configuration
6. `.vimrc.local` - local user configuration

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
