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

## Enable **TouchID** to authenticate **sudo**

In `/etc/pam.d/sudo` and after line containing `pam_smartcard.so`, add:

```
auth sufficient pam_tid.so
```

E.g.,

```
auth       sufficient     pam_smartcard.so
auth       sufficient     pam_tid.so
auth       required       pam_opendirectory.so
account    required       pam_permit.so
password   required       pam_deny.so
session    required       pam_permit.so
```

## Safari Picture in Picture bookmark

Create bookmark and set address to Javascript snippet:

```js
javascript:(%20function(){%20var%20video%20=%20document.getElementsByTagName('video')[0];%20video.webkitSetPresentationMode(video.webkitPresentationMode%20===%20"picture-in-picture"%20?%20"inline"%20:%20"picture-in-picture");%20}%20)()
```
