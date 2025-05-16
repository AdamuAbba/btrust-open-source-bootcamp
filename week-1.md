# Week 1

## Tasks

### Read Bitcoin Core’s [Developer Guide](https://github.com/bitcoin/bitcoin/blob/master/doc/developer-notes.md)

I can confirm that i did infact read the developer guide

### Setup Bitcoin Core from source

I had no issues setting up Bitcoin Core from source, as this was not my first time. steps I followed;

- Since I use a mac, I followed the [build-osx docs](https://github.com/bitcoin/bitcoin/blob/master/doc/build-osx.md)
- I built from source with both `cmake --build build` and `ctest --test-dir build` commands working fine
- I also took the time to set the following aliases for convenience or maybe i'm just lazy 😅:

  ```sh
  alias edit-bitcoin='nvim "$HOME/Library/Application Support/Bitcoin/bitcoin.conf"'
  alias bitcoin-cli="$HOME/Documents/bitcoin/build/bin/bitcoin-cli"
  alias bitcoind="$HOME/Documents/bitcoin/build/bin/bitcoind"

### Run Bitcoin in regtest mode, generate blocks, run some cli commands, and write short notes on 5 of them

#### Commands I played with

- `bitcoind -regtest -daemon` – start Bitcoin node in regtest mode in background
- `bitcoin-cli -regtest createwallet "testwallet"` – create a wallet named "testwallet"
- `bitcoin-cli -regtest getnewaddress` – generate a new receiving address
- `bitcoin-cli -regtest generatetoaddress 101 <address>` – mine 101 blocks to the given address
- `bitcoin-cli -regtest getbalance` – show current wallet balance
- `bitcoin-cli -regtest getblockcount` – show current block height

#### Screenshots?

### Read Bitcoin Core documentation and summarize what the project is about

My breakdown for the Bitcoin Core repository is that it is the primary integration and staging tree for Bitcoin. The project includes the source code for **Bitcoin Core**, which implements the **Bitcoin protocol**, enabling users to participate in the Bitcoin network as full nodes. It is written primarily in C++ and includes components for:

- transaction validation,
- peer-to-peer networking,
- And a wallet for managing Bitcoin funds.

**In summary:**

- **Bitcoin Core** is the **reference implementation** of the Bitcoin protocol
- It runs a **full node**, validating all transactions and blocks
- Includes a **Bitcoin wallet**, **RPC server**, and **P2P networking**
- Enforces Bitcoin's **consensus rules** and maintains **network security**
- Stores and syncs the **entire blockchain**
- Offers tools to **interact with Bitcoin**, like `bitcoind` and `bitcoin-cli`
- Developed and maintained by **open-source contributors**
- Documentation covers setup, usage, wallet functions, RPC calls, and dev guidelines

### Select a major feature of Bitcoin Core, read and summarise its functionality

### Explain Bitcoin Core in one paragraph using your own words

Bitcoin Core is the main software that powers the Bitcoin network 🌐. It connects to other nodes, verifies all transactions and blocks, and keeps a full copy of the blockchain. This helps secure the network and make sure everyone follows the same rules. It also has tools for sending, receiving, and managing Bitcoin, but its main job is to enforce the protocol and keep the system decentralized.

### What use cases/other solutions are currently using Bitcoin Core

So below are some of the use cases and solutions using bitcoin core, i've also provided some examples of each;

- 🏦 **Full Nodes:** Most Bitcoin full nodes run Bitcoin Core to validate and relay transactions
  - **Example:** [Umbrel node](https://github.com/getumbrel/umbrel)
- 🔐 **Wallets:** Many wallets rely on Bitcoin Core's backend for security and consensus
  - **Example:** [Wasabi Wallet](https://github.com/WalletWasabi)
- 🛠️ **Developers:** Build applications using Bitcoin Core's RPC interface
  - **Example:** [BTCPay Server](https://github.com/btcpayserver/btcpayserver),
- ⚡ **Lightning Network:** Often runs on top of Bitcoin Core nodes for on-chain data
  - **Example:** [LND](https://github.com/lightningnetwork/lnd)

### Who are the core maintainers/reviewers of Bitcoin Core

### What is the git commit style/structure of Bitcoin Core

### What is the dev community platform where Bitcoin Core maintainers/contributors are reachable?

As explained in the [Communication Channels](https://github.com/bitcoin/bitcoin/blob/master/CONTRIBUTING.md#communication-channels) section of the docs, most bitcoin discussions happen on IRC, in the `#bitcoin-core-dev` channel on Libera Chat, so maintainers/contributors alike would most likely be active there.

### Join Bitcoin Core community and make connections

So I went ahead and created a `Nik` and joined;

- `#bitcoin-core-dev`
- `bitcoin-core-pr-reviews`

channels on `Libera Chat`

### Select a merged PR, review and analyse the PR’s conversations/comments. What are your takeaways?

### What is the process of proposing new features/enhancements on Bitcoin Core?

### How do you identify the priority features in Bitcoin Core?

### Choose an open PR on Bitcoin Core, review, and submit your review in your Google doc (and not on the PR)

### Share the new things you learned from this week
