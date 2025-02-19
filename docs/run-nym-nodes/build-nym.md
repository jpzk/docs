---
sidebar_label: "Building Nym"
description: "How to build the Nym platform. Nym is relatively simple to build and run on Mac OS X, Linux, and Windows."
hide_title: false
title: Building Nym
---

Nym runs on Mac OS X, Linux, and Windows. All nodes **except the Desktop Wallet** on Windows should be considered experimental - it works fine if you're an app developer but isn't recommended for running nodes. 

### Building Nym

Nym has two main codebases:

- the Nym platform, written in Rust. This contains all of our code _except_ for the validators.
- the Nym validators, written in Go.

:::note
This page details how to build the main Nym platform code. **If you want to build and run a validator, [go here](/docs/next/run-nym-nodes/nodes/validators) instead.**
:::

### Prerequisites

- (Debian/Ubuntu) `pkg-config`, `build-essential`, `libssl-dev`, `curl`, `jq`, `git`

```
sudo apt update
sudo apt install pkg-config build-essential libssl-dev curl jq git
```

- `Rust & cargo >= v1.56`

We recommend using the [Rust shell script installer](https://www.rust-lang.org/tools/install). Installing cargo from your package manager (e.g. `apt`) is not recommended as the packaged versions are usually too old.

If you really don't want to use the shell script installer, the [Rust installation docs](https://forge.rust-lang.org/infra/other-installation-methods.html) contain instructions for many platforms.

### Download and build Nym binaries

The following commands will compile binaries into the `nym/target/release` directory:

```
rustup update
git clone https://github.com/nymtech/nym.git
cd nym
git reset --hard # in case you made any changes on your branch
git pull # in case you've checked it out before

# Note: the default branch you clone from Github, `develop`, may be
# incompatible with both the mainnet and testnet. As such, make sure 
# to checkout the current release: 
# `git checkout tags/v1.0.1`.

git checkout tags/v1.0.1
# this builds your binaries with mainnet configuration
cargo build --release
# to build your binaries with Sandbox testnet configuration, run this instead: 
NETWORK=sandbox cargo build --release
```

Quite a bit of stuff gets built. The key working parts are:

1. the [mixnode](/docs/next/run-nym-nodes/nodes/mixnodes): `nym-mixnode`
2. the [gateway node](/docs/next/run-nym-nodes/nodes/gateways): `nym-gateway`
3. the [websocket client](/docs/next/developers/develop-with-nym/websocket-client): `nym-client`
4. the [socks5 client](/docs/next/developers/develop-with-nym/socks5-client): `nym-socks5-client`
5. the [network requester](/docs/next/run-nym-nodes/nodes/requester): `nym-network-requester`
6. the [network explorer api](/docs/next/nym-apps/network-explorer): `explorer-api`

The repository also contains two Typescript applications which aren't built in this process: the [Nym Wallet](docs/next/nym-apps/wallet) and the [Network Explorer UI](docs/next/nym-apps/network-explorer). Both of these can be built by following the instructions on their respective docs pages. 

:::note
You cannot build from GitHub's .zip or .tar.gz archive files on the releases page - the Nym build scripts automatically include the current git commit hash in the built binary during compilation, so the build will fail if you use the archive code (which isn't a Git repository). Check the code out from github using `git clone` instead. 
:::

### (Optional) build binaries with Ethereum features enabled

If power users want to use Basic Bandwidth Credentials (BBCs), then they have to build the various binaries slightly differently. 

:::warning
This is an optional feature at the moment; users can utilise the mixnet without these as well. 
:::

To build the code repo with these features enabled, replace the `cargo build --release` command in the instructions above to: 

```
cargo build --release --features eth
```

This flag compiles and builds the `nym-client`, `nym-socks5-client`, and `gateway` binaries with `eth` features enabled. These features are a setting where clients and gateways are running expecting BBCs to create a connection and send packets through the mixnet. There will be a blogpost explaining these features very soon. 

