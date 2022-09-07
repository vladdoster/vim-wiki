# Linux

## apply patch via a `.diff` file

```bash
patch --merge -i <diff>
```

## create soft link
 
```bash 
ln -s `<real>` `<to create>`
```

## add non-standard shell to `/etc/shells`

```bash
echo "/usr/local/bin/fish" | sudo tee -a /etc/shells
```
