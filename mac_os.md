# MacOS

## Don't generate .DS_store

```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores false
```

## Recursive .DS_store removal

```bash
find . -name ".DS_Store" -print -delete
```
