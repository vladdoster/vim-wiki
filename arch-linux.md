# Arch Linux

## Initialize the arch-keyring

```bash
pacman-key --init && \
pacman-key --populate && \
pacman-key --refresh-keys && \
pacman -Sy archlinux-keyring
```

## Create US only mirrorlist

```bash
awk '/^## United Statues$/{f=1; next}f==0{next}/^$/{exit}{print substr($0, 1);}' /etc/pacman.d/mirrorlist
```

## Uncomment all mirrors

```bash
sed -i 's/^#Server/Server/' /etc/pacman.d/mirrorlist
```

## Rank mirrors for improved dl speeds

```bash
pacman -S reflector rsync --noconfirm && \
reflector --ipv4 --fastest 20 --country "United States" --save /etc/pacman.d/mirrorlist
```

## Make pacman and yay colorful

```bash
grep -q "^Color" /etc/pacman.conf || sed -i "s/^#Color$/Color/" /etc/pacman.conf
grep -q "ILoveCandy" /etc/pacman.conf || sed -i "/#VerbosePkgLists/a ILoveCandy" /etc/pacman.conf
```

## Use all cores for compilation.

```bash
sed -i "s/-j2/-j$(nproc)/;s/^#MAKEFLAGS/MAKEFLAGS/" /etc/makepkg.conf
```
