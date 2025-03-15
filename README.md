# CKPOOL + CKPROXY + libckpool

**Ultra low overhead, massively scalable Bitcoin mining pool, proxy, passthrough, and library in C for Linux.**

Developed by Con Kolivas, CKPOOL is optimized for high performance and minimal resource usage.

---

## Overview

CKPOOL provides a versatile Bitcoin mining solution, designed to efficiently handle large-scale mining operations. It can operate as a standalone pool, proxy, passthrough node, or library, and supports ultra-low latency and minimal overhead.

---

## Features

- **Massively Scalable:** Multiprocess and multithreaded architecture for optimal multicore CPU utilization.
- **Minimal Overhead:** Efficient memory usage and reliance only on essential Linux libraries.
- **Reliable Communication:** Unix sockets for inter-process communication.
- **Flexible Deployment:** Supports multiple modes (pool, proxy, passthrough).
- **Bitcoind Integration:** Supports multiple local/remote bitcoind instances with failover.
- **Advanced Configuration:** Supports coinbase signatures, customizable vardiff, rapid work updates, and detailed logging.
- **Easy Upgrades:** Virtually seamless upgrades with socket handover.
- **Library Support:** Standalone C library (libckpool) for integration with other software.

---

## Deployment Modes

- **Simple Pool:** Standard Bitcoin mining pool.
- **Solo Mining:** Per-user solo mining configuration.
- **Proxy:** Acts as a front-end to upstream pools.
- **Passthrough Node:** Aggregates connections, isolating the primary pool.
- **Redirector:** Filters and redirects miners based on share contributions.

---

## Installation

### Dependencies

Basic dependencies:
```bash
sudo apt-get install build-essential yasm
```

Recommended build (with ZMQ support):
```bash
sudo apt-get install build-essential yasm libzmq3-dev
```

Building from git additionally requires:
```bash
sudo apt-get install autoconf automake libtool pkgconf
```

### Building CKPOOL

```bash
./configure
make
```

From git repository:
```bash
./autogen.sh
./configure
make
```

Binaries (`ckpool`, `ckproxy`, `ckpmsg`, `notifier`) are generated in the `src/` directory.

Installation (optional):
```bash
sudo make install
```

---

## Usage

### Running CKPOOL

Example:
```bash
./ckpool -c ckpool.conf
```

### Command-line Options

- `-B`: Solo mining mode (BTCSOLO)
- `-c CONFIG`: Specify config file
- `-g GROUP`: Group ID
- `-H`: Handover mode
- `-k`: Kill existing instance
- `-L`: Enable share logging
- `-l LOGLEVEL`: Set logging level (default: 5)
- `-N`: Passthrough node mode
- `-n NAME`: Instance name
- `-P`: Passthrough proxy mode
- `-p`: Proxy mode
- `-R`: Redirector mode
- `-s SOCKDIR`: Socket directory
- `-u`: User proxy mode

### Example Configuration (`ckpool.conf`)

```json
{
  "btcd": [{"url": "http://localhost:8332", "auth": "user", "pass": "password"}],
  "btcaddress": "your-bitcoin-address",
  "btcsig": "Custom signature",
  "donation": 0.5,
  "serverurl": ["0.0.0.0:3333"],
  "mindiff": 1,
  "startdiff": 42,
  "logdir": "logs"
}
```

---

## License

CKPOOL is released under the GNU Public License V3. Please see the included `COPYING` file for full details.

**Support development:** By default, CKPOOL contributes 0.5% of solved blocks in pool mode to support ongoing development. Consider keeping this contribution active or directly donating to the authors.

---

**Thank you for using CKPOOL!**

For further assistance, refer to documentation or the community forums.
