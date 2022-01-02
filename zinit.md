# Zinit - ZSH configuration framework

Rarely used programs are offloaded here.

Last updated: 01/01/2022

## Setup


Most if not all of the programs require `zinit-annex-gem-bin-node`.

Add the following snippet as the first plugin in your configuration:

```zsh
zinit light-mode for zdharma-continuum/zinit-annex-bin-gem-node
```

The following snippet sets a variable to determine correct binary to download. It isn't requred, but
as of 01/01/2022, `zinit` binary selection will choose the wrong binary for some projects. I'm
working on a PR to address this.

```zsh
case "$OSTYPE" in
  linux*) bpick='*((#s)|/)*(linux|musl)*((#e)|/)*' ;;
  darwin*) bpick='*(macos|darwin)*' ;;
  *) error 'unsupported system -- some cli programs might not work' ;;
esac
```

## Programs & Plugins list

### [argo cd](https://github.com/argoproj/argo-cd)

```zsh
zinit for \
    as'completions' \
    atclone'
      ./argocd* completion zsh > _argocd' \
    atpull'%atclone' \
    from'gh-r' \
    if'[[ "$(uname -m)" == x86_64 ]]' \
    light-mode \
    sbin'argocd* -> argocd' \
    wait \
  argoproj/argo-cd
```

### [bat](https://github.com/sharkdp/bat)

```zsh
zinit for \
    sbin'**/bat -> bat' \
  @sharkdp/bat \
```

### [delta](https://github.com/dandavison/delta)

```zsh
zinit for \
    sbin'**/delta -> delta' \
  dandavison/delta
```

### [exa](https://github.com/ogham/exa)

```zsh
zinit for \
    sbin'**/exa -> exa'
    atclone'cp -vf completions/exa.zsh _exa'  \
  ogham/exa
```

### [fd](https://github.com/sharkdp/fd)

A simple, fast and user-friendly alternative to 'find'.

```zsh
zinit for \
    as'command' \
    from'gh-r' \
    sbin'**/fd -> fd' \
	@sharkdp/fd
```

### fzf-bin

```
zinit for \
    as'command' \
    from'gh-r'  \
    sbin'fzf'   \
  junegunn/fzf-bin
```

### [git-sizer](https://github.com/github/git-sizer)

Compute various size metrics for a Git repository, flagging those that might
cause problems.

```zsh
zinit for \
    as'command'     \
    bpick"${bpick}" \
    from'gh-r'      \
    sbin'git-sizer' \
	@github/git-sizer
```

### [glow](https://github.com/charmbracelet/glow)

Glow is a terminal based markdown reader designed from the ground up to bring
out the beauty—and power—of the CLI.

```zsh
zinit for \
    as'command' \
    from'gh-r'  \
    sbin'glow'  \
	charmbracelet/glow
```

### [grex](https://github.com/pemistahl/grex)

A command-line tool and library for generating regular expressions from
user-provided test cases.

```zsh
zinit for \
    from'gh-r'  \
    as'command' \
    sbin'grex'  \
	pemistahl/grex
```

### [homebrew](https://brew.sh/)

```zsh
zinit for \
    as'null' \
    atclone'%atpull' \
    atpull'
      ./bin/brew update --preinstall \
      && ln -sf $PWD/completions/zsh/_brew $ZINIT[COMPLETIONS_DIR] \
      && rm -f brew.zsh \
      && ./bin/brew shellenv --dummy-arg > brew.zsh \
      && zcompile brew.zsh' \
    depth'3' \
    nocompletions \
    sbin'bin/brew' \
    src'brew.zsh' \
    wait \
  Homebrew/brew
```

### [hyperfine](https://github.com/sharkdp/hyperfine)

```zsh
zinit for \
    sbin'**/hyperfine -> hyperfine' \
  @sharkdp/hyperfine
```

### [jq](https://github.com/stedolan/jq)

```zsh
zinit for \
    atclone'
      autoreconf -fi \
      && ./configure --with-oniguruma=builtin \
      && make \
      && ln -sfv $PWD/jq.1 $ZPFX/man/man1' \
    as'null' \
    if'(( ! ${+commands[jq]} ))' \
    lucid \
    sbin'jq' \
    wait \
  stedolan/jq
```

### [kubectx](https://github.com/ahmetb/kubectx)

```zsh
zinit for \
    bpick'kubectx;kubens' \
    from'gh-r' \
    light-mode \
    sbin'kubectx;kubens'  \
    wait \
  ahmetb/kubectx
```

### [neovim](https://github.com/neovim/neovim)

```zsh
zinit for \
    bpick"${bpick}"           \
    sbin'**/bin/nvim -> nvim' \
  neovim/neovim
```

### [ripgrep](https://github.com/burntSushi/ripgrep)

```zsh
zinit for \
    sbin'**/rg -> rg' \
  BurntSushi/ripgrep
```

### [shfmt](https://github.com/mvdan/sh)

```zsh
zinit for \
    bpick"${bpick}" \
    sbin'shfmt* -> shfmt' \
  @mvdan/sh
```

### [stow](https://github.com/aspiers/stow)

```zsh
zinit for \
    as'program' atpull'%atclone' atclone"
      autoreconf -iv \
      && ./configure" \
    make'bin/stow' \
    pick"bin/stow" \
  @aspiers/stow
```
