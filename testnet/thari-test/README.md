# thari-test
> This is Thari testnet chain

> GENESIS PUBLISHED

> PEERS PUBLISHED

1st testnet for ThariCommunity/thari application.

## Hardware Requirements
* **Minimal**
    * 4 GB RAM
    * 100 GB SSD
    * 3.2 x4 GHz CPU
* **Recommended**
    * 8 GB RAM
    * 100 GB NVME SSD
    * 4.2 GHz x6 CPU

## Operating System
* Linux/Windows/MacOS(x86)
* **Recommended**
    * Linux(x86_64)

## Installation Steps
>Prerequisite: go1.17+ required. [ref](https://golang.org/doc/install)

   Append the below lines to the file ${HOME}/.bashrc and execute the command source ${HOME}/.bashrc to reflect in the current Terminal session
   ```shell
   export GOROOT=/usr/local/go
   export GOPATH=${HOME}/go
   export GOBIN=${GOPATH}/bin
   export PATH=${PATH}:${GOROOT}/bin:${GOBIN}
   ```

>Prerequisite: git. [ref](https://github.com/git/git)

>Optional requirement: GNU make. [ref](https://www.gnu.org/software/make/manual/html_node/index.html)

* Clone git repository
```shell
git clone https://github.com/ThariCommunity/thari.git
```
* Checkout latest tag
```shell
cd thari
git fetch --tags
git checkout vlatest
```
* Install
```shell
make all
```
