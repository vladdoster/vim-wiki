# MacOS

## Don't generate .DS_store

```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

## Recursive .DS_store removal

```bash
find . -name ".DS_Store" -print -delete
```
## Enable tiling window management

1. Install [HammerSpoon](https://github.com/Hammerspoon/hammerspoon)
1. Clone [Hammerspoon_asm](https://github.com/asmagill/hammerspoon_asm)
  1. Compile the `spaces`, `undocumented`, and `auxieulment` modules

  ```bash
  make && make install
  ```
1. Rest is handled by [dotfiles](https://github.com/vladdoster/dotfiles)
