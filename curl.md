# cURL

## Compile from source

```bash
#! /bin/bash

# Tested on CentOS 7 and CentOS 8
# Check the latest version at https://curl.se/download/
VERSION=7.80.0

cd ~
sudo yum update -y
sudo yum install wget gcc openssl-devel make -y
wget https://curl.haxx.se/download/curl-${VERSION}.tar.gz
tar -xzvf curl-${VERSION}.tar.gz 
rm -f curl-${VERSION}.tar.gz
cd curl-${VERSION}
./configure --prefix=/usr/local --with-ssl
make
sudo make install
sudo ldconfig
cd ~
rm -rf curl-${VERSION}
```
