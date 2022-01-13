# CentOS

## Repository with the latest TMUX version

**pro-tip**: build from source

```bash
sudo $(
  yum install -y http://galaxy4.net/repo/galaxy4-release-7-current.noarch.rpm
  yum update -y
  yum install -y tmux
)
```

## CentOS 8 repository

```bash
http://mirror.centos.org/centos/8/BaseOS/x86_64/os/
```
## Get current core utils (e.g., gcc, make, automake, cmake, etc.)

### dev-toolset 7

```bash
sudo yum install -y \
  centos-release-scl \
  devtoolset-7 \
&& scl enable devtoolset-7 "${SHELL}"
```

### dev-toolset 9

```bash
sudo yum install -y \
  centos-release-scl \
  devtoolset-9 \
&& scl enable devtoolset-9 "${SHELL}"
```

### IUS repository

```bash
sudo yum install -y \
  https://repo.ius.io/ius-release-el7.rpm \
  https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```
