# CentOS

## Latest TMUX version repositpory

```shell
sudo yum install http://galaxy4.net/repo/galaxy4-release-{7,8}-current.noarch.rpm --assume-yes \
&& sudo yum update --assume-yes \
&& sudo yum install tmux --assume-yes
```

## CentOS 8 repository

```shell
http://mirror.centos.org/centos/8/BaseOS/x86_64/os/
```
## Get newer version of GCC

```
sudo yum install centos-release-scl --assumeyes
sudo yum install devtoolset-7 --assumeyes
scl enable devtoolset-7 "$(which $SHELL)"
```
