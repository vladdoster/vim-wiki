# Zinit - ZSH configuration framework

## collection of program & plugin ices

Rarely used programs are offloaded here.

### Select correct binary for OS

```bash
case "$OSTYPE" in
linux*) bpick='*((#s)|/)*(linux|musl)*((#e)|/)*' ;;
darwin*) bpick='*(macos|darwin)*' ;;
*) error 'unsupported system -- some cli programs might not work' ;;
esac
```

### [fd](https://github.com/sharkdp/fd)

A simple, fast and user-friendly alternative to 'find'.

```bash
zinit from'gh-r' as"command" sbin'**/fd -> fd' for \
	@sharkdp/fd
```

### [git-sizer](https://github.com/github/git-sizer)

Compute various size metrics for a Git repository, flagging those that might
cause problems.

```bash
zinit from'gh-r' as"command" sbin'git-sizer' bpick"${bpick}" for \
	@github/git-sizer
```

### [glow](https://github.com/charmbracelet/glow)

Glow is a terminal based markdown reader designed from the ground up to bring
out the beauty—and power—of the CLI.

```bash
zinit from'gh-r' as"command" sbin'glow' for \
	charmbracelet/glow
```

### [grex](https://github.com/pemistahl/grex)

A command-line tool and library for generating regular expressions from
user-provided test cases.

```bash
zinit from'gh-r' as"command" sbin'grex' for \
	pemistahl/grex
```
