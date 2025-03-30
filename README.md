# t3rn
T3rn Node run on VPS
# T3rn Executor Setup

This document provides the steps to set up the T3rn executor on a Linux-based machine for interacting with different blockchain networks.

## Prerequisites

Make sure you have the following installed:

- `curl`
- `screen`
- `jq`

You can install them by running:

```bash
sudo apt update && sudo apt upgrade -y


sudo apt install curl screen jq -y

Setup
Follow the steps below to download, configure, and run the T3rn executor.

1. Remove any old t3rn executables
If there are any previous instances of the t3rn binary on your machine, remove them:

find ~/ -type f -name 't3rn' -exec rm -f {} ;

2. Start a New Screen Session
Start a new screen session for running the T3rn executor:

screen -S t3rn

3. Download and Extract the Executor Binary
Download the executor from GitHub and extract the tarball:

wget https://github.com/t3rn/executor-release/releases/download/v0.53.0/executor-linux-v0.53.0.tar.gz
rm -rf executor
tar -xvzf executor-linux-v0.53.0.tar.gz


4. Configure the Executor
Navigate to the executor directory and configure the environment variables:

cd executor/executor/bin
export ENVIRONMENT=testnet
export LOG_LEVEL=debug
export LOG_PRETTY=false
export EXECUTOR_PROCESS_BIDS_ENABLED=true
export EXECUTOR_PROCESS_ORDERS_ENABLED=true
export EXECUTOR_PROCESS_CLAIMS_ENABLED=true
export ENABLED_NETWORKS='arbitrum-sepolia,base-sepolia,optimism-sepolia,l2rn,unichain-sepolia'
export EXECUTOR_MAX_L3_GAS_PRICE=3000
export PRIVATE_KEY_LOCAL=<Private Key>  # Replace with your private key
export RPC_ENDPOINTS='{"l2rn": ["http://b2n.rpc.caldera.xyz/"], "arbt": ["https://arbitrum-sepolia.drpc.org/", "https://arbitrum-sepolia.publicnode.com/"], "bast": ["https://base-sepolia.publicnode.com/"], "opst": ["https://optimism-sepolia.publicnode.com/"], "unit": ["https://sepolia.unichain.org"]}'

5. Run the Executor
After configuring the environment variables, you can run the executor in the background with the desired settings.

Additional Information
Replace <Private Key> with your actual private key.

The networks configured are for testnet environments. Modify the ENABLED_NETWORKS and RPC_ENDPOINTS if you're working with other networks.
