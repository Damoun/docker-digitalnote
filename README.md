[docker-digitalnote](https://registry.hub.docker.com/u/damoun/digitalnote/) [![License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](/LICENSE) [![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)
====================

[DigitalNote XDN (duckNote, DarkNote)](http://digitalnote.org/) container definition for docker.

## Quickstart

First, start by pull the container :

```sh
docker pull damoun/digitalnote
```

#### DigitalNoted

To retrieve the blockchain, you need to start the digitalnote daemon :

```sh
docker run -dt --name digitalnote-daemon --volume /opt/digitalnote:/var/digitalnote damoun/digitalnote ./digitalnoted --data-dir /var/digitalnote/data
```

#### Wallet

If you want to run a wallet, you can create a new wallet with a passphrase :

```sh
docker run --rm -it --name digitalnote-wallet --link digitalnote-daemon:digitalnote-daemon --volume /opt/digitalnote:/var/digitalnote damoun/digitalnote ./simplewallet --generate-new-wallet /var/digitalnote/xdn.wallet --daemon-host digitalnote-daemon
```

### Mining

The simpleminer binary seems don't work at the moment with mining pool.

```sh
docker run -di --name digitalnote-miner damoun/digitalnote ./simpleminer --pool-addr xdn.miner.center:4555 --login ddeH5fnSdLU99rK8mJ3V8RLNXEozW7hZBZxiJWt2acEfXSkTH4hyoGEL8JCu3o197r2vfDRpcfbjkCbLZvJhT5Bc2kHFrRoE1 --pass x
```
