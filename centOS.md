# CentOS

## Repository with the latest TMUX version

Note: You should just build it from source

```bash
sudo yum install http://galaxy4.net/repo/galaxy4-release-7-current.noarch.rpm --assume-yes && \
sudo yum update --assume-yes && \
sudo yum install tmux --assume-yes
```

## CentOS 8 repository

```bash
http://mirror.centos.org/centos/8/BaseOS/x86_64/os/
```
## Get newer version of GCC

```bash
sudo yum install centos-release-scl devtoolset-7 --assume-yes && \
scl enable devtoolset-7 "$(which $SHELL)"
```
