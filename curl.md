# cURL

## Compile from source

```bash
#!/bin/bash
# Tested on CentOS 7 and CentOS 8
# Check the latest version at https://curl.se/download/
(
  cat <<'EOF'
#!/bin/bash

VERSION="7.80.0"
BUILD_DIR="$(mktemp -d)"

sudo yum update -y
sudo yum install wget gcc openssl-devel make -y

INIT_DIR="$PWD"
echo "Started in $INIT_DIR"
(
  cd $BUILD_DIR
  wget --no-check-certificate https://curl.haxx.se/download/curl-${VERSION}.tar.gz
  tar -xzvf curl-${VERSION}.tar.gz
  cd "curl-${VERSION}"
  ./configure --prefix=/usr/local --with-ssl
  make --jobs 8
  sudo make --jobs 8 install
  sudo ldconfig
)
rm -rf $BUILD_DIR
exit 0
```
