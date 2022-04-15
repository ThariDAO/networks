# thari-test

> This is Thari testnet chain

> PRE-GENESIS NOT PUBLISHED

> GENESIS NOT PUBLISHED

> PEERS NOT PUBLISHED

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

### Generate keys

`tharid keys add [key_name]`

or

`tharid keys add [key_name] --recover` to regenerate keys with your [BIP39](https://github.com/bitcoin/bips/tree/master/bip-0039) mnemonic


## Validator setup instructions

### GenTx : Accepting Now.[Date TBD]

* [Install](#installation-steps) tharid core application
* Initialize node
```shell
tharid init {{NODE_NAME}} --chain-id thari-test
```

```shell
tharid add-genesis-account {{KEY_NAME}} 1000000000uthari
```

```shell
tharid gentx {{KEY_NAME}} 10000000uthari \
--chain-id thari-test \
--moniker="{{VALIDATOR_NAME}}" \
--commission-max-change-rate=0.01 \
--commission-max-rate=0.10 \
--commission-rate=0.02 \
--details="XXXXXXXX" \
--security-contact="XXXXXXXX" \
--website="XXXXXXXX"
```

* Copy the contents of `${HOME}/.thari/config/gentx/gentx-XXXXXXXX.json`.
* Fork the [repository](https://github.com/ThariCommunity/networks/)
* Create a file `gentx-{{VALIDATOR_NAME}}.json` under the testnet/thari-test/gentxs folder in the forked repo, paste the copied text into the file. Find reference file gentx-examplexxxxxxxx.json in the same folder.
* Run `tharid tendermint show-node-id` and copy your nodeID.
* Run `ifconfig` or `curl ipinfo.io/ip` and copy your publicly reachable IP address.
* Create a file `peers-{{VALIDATOR_NAME}}.json` under the testnet/thari-test/peers folder in the forked repo, paste the copied text from the last two steps into the file. Find reference file sample-peers.json in the same folder.
* Create a Pull Request to the `main` branch of the [repository](https://github.com/ThariCommunity/networks)
>**NOTE:** The Pull Request will be merged by the maintainers to confirm the inclusion of the validator at the genesis. The final genesis file will be published under the file testnet/thari-test/genesis_final.json.
* Replace the contents of your `${HOME}/.thari/config/genesis.json` with that of testnet/thari-test/genesis_final.json.
* Copy below node as `persistent_peers` or `seeds` in `${HOME}/.thari/config/config.toml`
 
```shell

```
* Copy below value as minimum-gas-prices in ${HOME}/.thari/config/app.toml
```shell
0.025uthari
```

* Start tharid by running below command or create a `systemd` service to run tharid in background.
```shell
tharid start
```


### Become a validator

* [Install](#installation-steps) tharid core application
* Initialize node
```shell
tharid init {{NODE_NAME}}
```
* Replace the contents of your `${HOME}/.thari/config/genesis.json` with that of testnet/thari-test/genesis_final.json from the `main` branch of [repository](https://github.com/ThariCommunity/networks).
* Copy below node as `persistent_peers` or `seeds` in `${HOME}/.thari/config/config.toml`
```shell

```

* Copy below value as minimum-gas-prices in ${HOME}/.thari/config/app.toml
```shell
0.025uthari
```

### Bootstrap node from state-sync snapshot 

```
To be published
```

##### Set options in config.toml

* Set persistent-peers in config.toml. These are the list of peers in which there are snapshots.
```
persistent_peers = ""
```

* Start tharid by running below command or create a `systemd` service to run tharid in background.
```shell
tharid start
```
* Acquire $uthari by sending a message to the validators channel in [Discord](TBD).
* Run `tharid tendermint show-validator` and copy your consensus public key.
* Send a create-validator transaction
```
tharid tx staking create-validator \
--from {{KEY_NAME}} \
--amount XXXXXXXXuthari \
--pubkey $(tharid tendermint show-validator) \
--chain-id thari-test \
--moniker="{{VALIDATOR_NAME}}" \
--commission-max-change-rate=0.02 \
--commission-max-rate=0.10 \
--commission-rate=0.02 \
--min-self-delegation="1" \
--details="XXXXXXXX" \
--security-contact="XXXXXXXX" \
--website="XXXXXXXX"
```

## Version
This chain is currently running on tharid [v0.1.0](https://github.com/ThariCommunity/thari/releases/tag/v0.1.0)

>Note: If your node is running on an older version of the application, please update it to this version at the earliest to avoid being exposed to security vulnerabilities /defects.

## Explorer
The explorer for this chain is hosted [TestNet Explorer](TBA)

## Genesis Time
The genesis transactions sent before TBD will be used to publish the genesis_final.json at TBD and then start the chain at 14.30UTC once the quorum is reached.

