# sudo

## disable password prompt for `sudo`

Add a line at the end of `/etc/sudoers` file via `sudo visudo` command.

### single user

```
<USER> ALL=(ALL) NOPASSWD: ALL 
```

### group

```bash
%<GROUP>  ALL=(ALL) NOPASSWD: ALL
```

### oneliner

```bash
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee "/etc/sudoers.d/dont-prompt-$USER-for-sudo-password"
```
