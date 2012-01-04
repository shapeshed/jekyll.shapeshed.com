--- 
layout: post
title: Compiling Node.js from source on Ubuntu 10.04
description: Compiling Node.js from source is easy enough so here's how. 
categories: 
- Node.js 
- Unix
---
Compiling Node.js from source is easy enough so here's how. 

## Installing from a tarball

Node.js needs a few things to compile so make sure they are installed. 

``` bash Installing Node.js dependencies
sudo apt-get update
sudo apt-get install build-essential openssl libssl-dev pkg-config 
```

Get the link for the latest tarball from the Source Code link on the [Node.js homepage][3]. Then download it and extract it.

``` bash Downloading and extracting the tarball
cd /usr/local/src
sudo mkdir node
cd node
sudo wget http://nodejs.org/dist/v0.6.6/node-v0.6.6.tar.gz
sudo tar -xzf node-v0.6.6.tar.gz 
```

Now you can compile and install the binary. By default Node.js will be installed to `/usr/local/bin/node` and npm will be installed to `/usr/local/bin/npm`. 

``` bash Compiling Node.js
cd node-v0.6.6/
sudo ./configure
sudo make
sudo make install
```

## Upgrading via a tarball

To upgrade Node.js simply download the new tarball, extract and repeat the installation process. 

## Installing from Git

If you plan to upgrade each time a new release comes out you may find cloning the Git repository more convenient than downloading and extracting  a tarball each time. 

You will need Git and the dependencies to be installed first.

``` bash Installing Node.js dependencies
sudo apt-get update
sudo apt-get install git-core build-essential openssl libssl-dev pkg-config 
```

Using Git means that instead of downloading extracting a tarball you can just clone the repository and checkout the latest version. If you need to check the versions that are available run `git tag`.

``` bash Cloning the Node.js Git repository
cd /usr/local/src
sudo git clone git://github.com/joyent/node.git
cd node
sudo git checkout v0.6.6
```

Now you can compile the binary as before

``` bash Compiling Node.js
sudo ./configure
sudo make
sudo make install
```

## Upgrading via Git

To upgrade to a new release of Node.js first pull the latest source.

``` bash Pulling the latest Node.js source 
cd /usr/local/src/node
sudo git checkout master
sudo git pull origin master
```

Then checkout the latest version where `v.x.x.x` is the version you want. 

``` bash Checking out the latest version
sudo git checkout vx.x.x
```

Then follow the installation process as before

``` bash Compiling Node.js
sudo ./configure
sudo make
sudo make install
```

This will upgrade Node.js and overwrite the previous version. 

[1]: https://launchpad.net/~chris-lea/+archive/node.js
[2]: https://launchpad.net/ubuntu/+source/nodejs
[3]: http://nodejs.org/#download
