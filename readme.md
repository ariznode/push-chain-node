# Specification
- CPU 4 core
- 16 GB ram
- ssd 400gb

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

Make sure go version 1.23+

## Running Localnet

Locknet is the local testnet environment for Push Chain. To spin up Locknet, use the following command:

```sh
git clone https://github.com/pushchain/push-chain-node.git
cd push-chain-node
```

```sh
make install
```

```sh
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> ~/.bashrc
source ~/.bashrc
```

## Run Node

Create screen session and run inside screen

```sh
screen -S push
```

```sh
make sh-testnet
```

## Node Status

Check node status

Detach screen first with ctrl a + d

```sh
pchaind status
```

If "catching_up": false that means your node is synced


# Validator

You can run Push validator on new tab on your VPS or detach screen by pressing ctrl a + d after node is running

## Run Validator

```sh
cd ~/push-chain-node
```

```sh
curl -fsSL https://get.push.network/node/install.sh | bash
```

Then fund your validator address with minimum 2 $push.

Claim push token : https://faucet.push.org/

## Verify Sync

```sh
push-validator status
```

## Register Validator

```sh
push-validator register-validator
```

## Monitor Dashboard

Monitor your validator in real-time with an interactive dashboard:

```sh
push-validator dashboard
```

### Validator command

#### Core

```bash
push-validator start                # Start with state sync (2-3 min)
push-validator stop                 # Stop node
push-validator status               # Check sync & validator status
push-validator dashboard            # Live interactive monitoring dashboard
push-validator register-validator   # Register as validator
push-validator logs                 # View logs
```

#### Validator Operations

```bash
push-validator increase-stake       # Increase validator stake and voting power
push-validator unjail               # Restore jailed validator to active status
push-validator withdraw-rewards     # Withdraw validator rewards and commission
push-validator restake              # Auto-withdraw and restake all rewards to increase validator power
```

#### Monitoring

```bash
push-validator sync            # Monitor sync progress
push-validator peers           # Show peer connections (from local RPC)
push-validator doctor          # Run diagnostic checks on validator setup
```

#### Management

```bash
push-validator restart         # Restart node
push-validator validators      # List validators (supports --output json)
push-validator balance         # Check balance (defaults to validator key)
push-validator reset           # Reset chain data (keeps address book)
push-validator full-reset      # ⚠️ Complete reset (deletes ALL keys and data)
push-validator backup          # Backup config and validator state
```

## Key Command

- Detach screen

```sh
ctrl a + d
```

- attach screen

```
screen -d -r push
```

- Stop Node

```sh
ctrl + c
```


## Contributing

We welcome contributions from the community! To get started:

- Fork this repository and create a new branch for your feature or bugfix.
- Make your changes and ensure all tests pass (`go test ./... -v`).
- Open a pull request with a clear description of your changes.
- For major changes, please open an issue first to discuss what you would like to change.
