# Guide-0g-storage-kv

# Hardware Requirement
```bash
- Memory: 16 GB RAM
- CPU: 4 cores
- Disk: 500GB / 1T NVME SSD
- Bandwidth: 500 MBps for Download / Upload
```

# Installation
## Download Source Code
```bash
git clone -b v1.1.0-testnet https://github.com/0glabs/0g-storage-kv.git
```

## Build The Source Code
```bash
cd 0g-storage-kv
git submodule update --init
cargo build --release
```

## Copy config
Copy the config_example.toml to config.toml and update the parameters
```toml
# rpc endpoint
rpc_listen_address
# ips of storage service, separated by ","
zgs_node_urls = "http://ip1:port1,http://ip2:port2,..."

# layer one blockchain rpc endpoint
blockchain_rpc_endpoint

# flow contract address
log_contract_address

# block number to start the sync, better to align with the config in storage service
log_sync_start_block_number

# storage nodes to download data from, separated by ","
# the provided nodes should cover full data in the storage network
zgs_node_urls
```

# Run
```bash
cd run

# consider using tmux in order to run in background
../target/release/zgs_kv --config config.toml
```
