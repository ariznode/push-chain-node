## Install Dependencies
```sh
apt update && apt upgrade -y
```

```sh
apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev -y
```

## Install Go

```sh
wget https://go.dev/dl/go1.23.0.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.23.0.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
source ~/.profile
go version
```

## Running Localnet

Locknet is the local testnet environment for Push Chain. To spin up Locknet, use the following command:

```sh
git clone https://github.com/pushchain/push-chain-node.git
cd push-chain-node
make sh-testnet
```

## Directory Structure

- `app/` – Core application logic and configuration
- `x/` – Cosmos SDK modules (UExecutor, UTxVerifier, etc.)
- `precompiles/` – EVM precompiles for universal verification
- `proto/` – Protobuf definitions
- `cmd/` – CLI entrypoints
- `deploy/` – Deployment scripts and testnet configs
- `interchaintest/` – E2E and integration tests
- `utils/` – Utility functions

## Contributing

We welcome contributions from the community! To get started:

- Fork this repository and create a new branch for your feature or bugfix.
- Make your changes and ensure all tests pass (`go test ./... -v`).
- Open a pull request with a clear description of your changes.
- For major changes, please open an issue first to discuss what you would like to change.
