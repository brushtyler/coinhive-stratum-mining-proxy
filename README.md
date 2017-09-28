# CoinHive Stratum Mining Proxy

A proof of concept of web mining using [CoinHive](https://coin-hive.com/) JavaScript Mining library on a custom stratum XMR pool.

## Installation

Docker:

```sh
$ git clone git@github.com:brushtyler/coinhive-stratum-mining-proxy.git
$ cd coinhive-stratum-mining-proxy
$ docker build -t coinhive-stratum-mining-proxy .
$ docker run -p 8892:8892 coinhive-stratum-mining-proxy <stratum tcp host> <stratum tcp port>
```

eg:

```sh
$ docker run -p 8892:8892 coinhive-stratum-mining-proxy xmr.crypto-pool.fr 3333
```

Linux/Mac:

```sh
$ git clone git@github.com:brushtyler/coinhive-stratum-mining-proxy.git
$ cd coinhive-stratum-mining-proxy
$ pip install -v -r requirements.txt
$ python coinhive-stratum-mining-proxy.py <stratum tcp host> <stratum tcp port>
```

eg:

```sh
$ python coinhive-stratum-mining-proxy.py xmr.crypto-pool.fr 3333
```


Dependencies:

- python2
- pip
- openssl-dev
- gcc
- git

## Usage

1. Install and Run `coinhive-stratum-mining-proxy`
2. Load the Coinhive Miner from your http server

```html
<script src="https://url/to/your/coinhive/files/coinhive.min.js"></script>
```

3. Change the `CoinHive.CONFIG.LIB_URL` config variables to point to your files:
```html
<script>
CoinHive.CONFIG.LIB_URL = "https://url/to/your/coinhive/files/"
</script>
```

4. Change the `CoinHive.CONFIG.WEBSOCKET_SHARDS` config variable:

```html
<script>
CoinHive.CONFIG.WEBSOCKET_SHARDS = [["ws://localhost:8892/proxy"]];
</script>
```

5. Start Mining

```html
<script>
var miner = new CoinHive.Anonymous('YOUR_WALLET_ADDRESS');
miner.start();
</script>
```
or

```html
<script>
var miner = new CoinHive.User('YOUR_WALLET_ADDRESS', 'YOUR_WORKER_NAME');
miner.start();
</script>
```

6. Profit!

## Demo

Setup and run `coinhive-stratum-mining-proxy` with `xmr.crypto-pool.fr 3333` parameters and open http://localhost:8892 in your browser for live demo.

## Links

- [JavaScript Miner API](https://coin-hive.com/documentation/miner)

## License

MIT
