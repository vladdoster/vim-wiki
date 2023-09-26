==== reset commit count ====

 Make a new branch from the first commit of master/whatever branch you want

====rename branch====

1. Rename branch locally
  
  git branch -m old_branch new_branch
  
2. Delete the old branch

  git push origin :old_branch

3. Push the new branch, set local branch to track the new remote
  
  git push --set-upstream origin new_branch
====git stash untracked files====
 
 git stash --keep-index 
====git stash w/ message====

 git stash save “<stash_message>” 
====set git pager====

 git config --global core.pager cat
====view git log====

 git log --oneline --graph --all

====delete release w/ gh cli====

 yes | gh release delete $(gh release list -L 1 | awk '{print $2}')


```
#!/bin/bash

VERSION="2.42.0"
BUILD_DIR="$(mktemp -d)"

INIT_DIR="$PWD"
echo "Started in $INIT_DIR"
(
  sudo rpm -Va --nofiles --nodigest
  sudo yum install --skip-broken -y \
    asciidoc \
    curl-devel \
    dh-autoreconf \
    docbook2X \
    expat-devel \
    gettext-devel \
    openssl-devel \
    perl-devel \
    xmlto \
    zlib-devel
  cd $BUILD_DIR
  wget --no-check-certificate https://github.com/git/git/archive/refs/tags/v${VERSION}.tar.gz
  tar -xzvf v${VERSION}.tar.gz
  cd "git-${VERSION}"
  make -j configure
  ./configure --prefix=/usr
  make --jobs 8 all doc info
  sudo make --jobs 8 install install-doc install-html install-info
  sudo ldconfig
)
rm -rf $BUILD_DIR
exit 0
```
