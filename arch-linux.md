# Arch Linux

## Initialize the arch-keyring

```bash

pacman-key --init && \
pacman-key --populate && \
pacman-key --refresh-keys && \
pacman -Sy archlinux-keyring
```
