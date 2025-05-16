# Week 1

## Tasks

### Read Bitcoin Core’s [Developer Guide](https://github.com/bitcoin/bitcoin/blob/master/doc/developer-notes.md)

I can confirm that i did in fact read the developer guide (As much as i could)

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

- `bitcoind -regtest` – start Bitcoin node in regtest mode in background
- `bitcoin-cli -regtest createwallet "testwallet"` – create a wallet named "testwallet"
- `bitcoin-cli -regtest getnewaddress` – generate a new receiving address
- `bitcoin-cli -regtest generatetoaddress 101 <address>` – mine 101 blocks to the given address
- `bitcoin-cli -regtest getbalance` – show current wallet balance
- `bitcoin-cli -regtest getblockcount` – show current block height

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

One major feature of Bitcoin Core is it's **full node validation** capability. It ensures that all blockchain data complies with consensus rules through the following:

- **Independent Verification**:Bitcoin Core downloads and verifies the entire blockchain, ensuring all transactions and blocks comply with consensus rules

  - [Source](https://coinrule.com/blog/learn/bitcoin-core-how-it-works-and-whos-behind-it/)

- **Security and Integrity**:By validating every transaction and block, Bitcoin Core prevents fraud, such as double-spending, and maintains the network’s integrity

  - [Source](https://cointelegraph.com/learn/bitcoin-core-explained)

- **Decentralization**:Running a full node contributes to the decentralization of the Bitcoin network, as each node operates independently without relying on third parties.

  - [Source](https://bitcoinmagazine.com/glossary/bitcoin-core)

- **Consensus Enforcement**:Ensures all participants agree on a single blockchain history by enforcing the network's rules.  

  - [Source](https://bitcoin-core.io/)

### Explain Bitcoin Core in one paragraph using your own words

Bitcoin Core is the main software that powers the Bitcoin network 🌐. It connects to other nodes, verifies all transactions and blocks, and keeps a full copy of the blockchain. This helps secure the network and make sure everyone follows the same rules. It also has tools for sending, receiving, and managing Bitcoin, but its main job is to enforce the protocol and keep the system decentralized.

### What use cases/other solutions are currently using Bitcoin Core

So below are some of the use cases and solutions using bitcoin core, i've also provided some examples of each;

- **Full Nodes:** Most Bitcoin full nodes run Bitcoin Core to validate and relay transactions

  - **Example:** [Umbrel node](https://github.com/getumbrel/umbrel)

- **Wallets:** Many wallets rely on Bitcoin Core's backend for security and consensus

  - **Example:** [Wasabi Wallet](https://github.com/WalletWasabi)

- **Developers:** Build applications using Bitcoin Core's RPC interface

  - **Example:** [BTCPay Server](https://github.com/btcpayserver/btcpayserver),

- **Lightning Network:** Often runs on top of Bitcoin Core nodes for on-chain data

  - **Example:** [LND](https://github.com/lightningnetwork/lnd)

### Who are the core maintainers/reviewers of Bitcoin Core

Based on the [Bitcoin Core: What It Is and How It Works](https://blog.areabitcoin.co/bitcoin-core/) article written in 2023 by [Carol Souza](https://blog.areabitcoin.co/author/carol/), some of the maintainers are;

- [Michael Ford (`fanquake`)](https://github.com/fanquake)

  - **Focus**: Build system and general maintenance.

- [Hennadii Stepanov (`hebasto`)](https://github.com/hebasto)

  - *Focus: GUI, build system, and testing.*
  - **GPG:** D1DB F2C4 B96F 2DEB F4C1  6654 4101 0811 2E7E A81F

- [Andrew Chow (`achow101`)](https://github.com/achow101)

  - **Focus:** Wallet functionality and hardware wallet interface.
  - **PGP Key**: 1528 1230 0785 C964 44D3 334D 1756 5732 E08E 5E41

- [Gloria Zhao (`glozow`)](https://github.com/glozow)

  - **Focus:** Mempool and transaction validation logic
  - **PGP key**: 6B00 2C6E A3F9 1B1B 0DF0  C9BC 8F61 7F12 00A6 D25C

### What is the git commit style/structure of Bitcoin Core

Bitcoin Core follows a **precise and structured commit message format** to maintain clarity and consistency across its codebase. This format is detailed in the [CONTRIBUTING.md](https://github.com/bitcoin/bitcoin/blob/master/CONTRIBUTING.md) file.

#### Format

```
<component>: <short description>

<optional longer description>

<optional issue reference>
```

- **Component**: The part of the codebase affected (e.g., `wallet`, `rpc`, `doc`, `gui`, `test`, `build`, etc.)
- **Short Description**: A concise summary (ideally under 60 characters)
- **Longer Description**: Optional; explains the rationale or more details
- **Issue Reference**: Optional; links to related issues or PRs

#### Quick Example

```
rpc: improve error handling in getblock

Previously, getblock would return a generic error if the block
hash was not found. This changes it to return a more informative
message.

Fixes #12345.
```

### What is the dev community platform where Bitcoin Core maintainers/contributors are reachable?

As explained in the [Communication Channels](https://github.com/bitcoin/bitcoin/blob/master/CONTRIBUTING.md#communication-channels) section of the docs, most bitcoin discussions happen on IRC, in the `#bitcoin-core-dev` channel on Libera Chat, so maintainers/contributors alike would most likely be active there.

### Join Bitcoin Core community and make connections

So I went ahead and created a `Nik` and joined both the `#bitcoin-core-dev` and `bitcoin-core-pr-reviews` channels on `Libera Chat`

### Select a merged PR, review and analyse the PR’s conversations/comments. What are your takeaways?

- PR: [include verbose "reject-details" field in testmempoolaccept response #28121](https://github.com/bitcoin/bitcoin/pull/28121)
- dev: [pinheadmz](https://github.com/pinheadmz)

#### Breakdown

A quick summary of the PR is that it adds a new field to the `testmempoolaccept` RPC response, providing detailed rejection messages for transactions that are not accepted into the mempool. The PR was eventually merged into Bitcoin Core on January 3, 2025 after feedback and revisions.

Based on the conversations on the PR a summary of the concerns raised were;

- Implementation might end up Revealing internal debug strings and might expose implementation details.
- There’s potential for non-standard or fragile information that could change across versions.
- Consensus vs. policy logic separation.
  - Ensure only mempool policy (m_debug_message) info is exposed.
- Consideration of whether the new field should be behind a debug flag—ultimately decided against it to maintain RPC consistency.

#### In Conclusion

The `reject-reason` field was carefully limited to **policy-level** messages only, ensuring clear boundaries are maintained in the codebase and the necessary changes were implemented by pinheadmz and the `reject-reason` added as an [optional field](https://github.com/bitcoin/bitcoin/pull/28121/files#diff-9c5b83de6dc84af277e352c88b9291aa44340a3c75f572a0b51661eb0a838de9)

### What is the process of proposing new features/enhancements on Bitcoin Core?

- **Idea & Research**

  - Ensure the feature aligns with Bitcoin Core’s goals (security, privacy, decentralization).
  - Research past discussions or issues to avoid duplicates.

- **Start a discussion/proposal via a Github issue**

  - Open an issue in the [Bitcoin Core GitHub repository](https://github.com/bitcoin/bitcoin/issues).
  - Clearly describe the proposal and rationale.
  - Add the `feature` label.
  - Tag relevant component labels (e.g., `wallet`, `rpc`, `gui`, etc.) to scope the change.

- **Fork and Implement**

  - Fork the [Bitcoin Core repository](https://github.com/bitcoin/bitcoin).
  - Write clean, tested code with minimal scope.

- **Follow Contribution Guidelines**

  - Conform to [coding style](https://github.com/bitcoin/bitcoin/blob/master/doc/developer-notes.md).
  - Write structured [commit messages](https://github.com/bitcoin/bitcoin/blob/master/CONTRIBUTING.md).

- **Submit a Pull Request**

  - Open a PR to the `master` branch.
  - Include motivation, usage, and rationale in the PR description.

- **Review & Iteration**

  - Respond to feedback from maintainers and contributors.
  - Make necessary changes until it’s approved or closed.

### How do you identify the priority features in Bitcoin Core?

To identify the priority features in Bitcoin Core i would:

- **Check the Project Boards**: [The Bitcoin Core Roadmap](https://github.com/bitcoin/bitcoin/projects) often show what's actively being worked on.
- **Watch Active PRs and Issues**: High-traffic pull requests for features in Bitcoin Core's repo would signify some degree of priority
- **Follow Contributor Discussions**: Important discussions happen in PR comments (Witnessed this myself multiple times), mailing lists, and IRC (#bitcoin-core-dev).
- **Look at Labels**: I think looking for `feature` labels and filtering out the ones with hight traffic would be one way to do it.
- **Review Release Notes & Changelogs**: Each release (e.g., v26.0) details completed priorities and what might come next.

### Choose an open PR on Bitcoin Core, review, and submit your review in your Google doc (and not on the PR)

> [!NOTE]
> I don't know any C++ so i decided to do a docs review instead since it
> covers a small scope and not alot of C++ code to look at.

- PR: [doc: Add missing top-level description to pruneblockchain RPC #32333](https://github.com/bitcoin/bitcoin/pull/32333)
- dev:[nervana21](https://github.com/nervana21)

#### summary

Adds a top-level description to the `pruneblockchain` RPC help, improving clarity and warning users about its effects.

#### Review Process

- Checked out PR [#32333](https://github.com/bitcoin/bitcoin/pull/32333)

- Recompiled Bitcoin Core using CMake

- Started `bitcoind` in regtest mode:

  ```sh
  ./build/bin/bitcoind --regtest
  ```

- Ran the `pruneblockchain` help command to verify output:

  ```sh
  ./build/bin/bitcoin-cli --regtest pruneblockchain --help
  ```

- **Final Remark**: ACK [`135a0f0`](https://github.com/bitcoin/bitcoin/commit/135a0f0aa711b95c50aa4cbe0c38d82d647f1c8b) — tested and works locally

  ```text
  error code: -1
  error message:
  pruneblockchain height
  
  Attempts to delete block and undo data up to a specified height or timestamp, if eligible for pruning.
  Requires `-prune` to be enabled at startup. While pruned data may be re-fetched in some cases (e.g., via `getblockfrompeer`), local deletion is irreversible.
  
  Arguments:
  1. height    (numeric, required) The block height to prune up to. May be set to a discrete height, or to a UNIX epoch time
               to prune blocks whose block time is at least 2 hours older than the provided timestamp.
  
  Result:
  n    (numeric) Height of the last block pruned
  
  Examples:
  > bitcoin-cli pruneblockchain 1000
  > curl --user myusername --data-binary '{"jsonrpc": "2.0", "id": "curltest", "method": "pruneblockchain", "params": [1000]}' -H 'content-type: application/json' http://127.0.0.1:8332/
  ```
  
### Share the new things you learned from this week

- Bitcoin core's documentation is ALOT to take in, but it is very well structured and easy to follow by narrowing down your search so you don't get overwhelmed (Reading the docs like a story book is a bad idea)

- So I don't know if this counts as something I've learned, but I realized that since I've been looking at Rust code for a while now, I've been able to sort of understand some C++ code in the Bitcoin Core repo 😂

- There are a number of conversations on even the smallest or `first good issue` pr's and i think that's because Bitcoin Core contributors try to cover as many edge cases as possible? they don't just show up and drop an `ACK` and bounce? well maybe they do and i haven't seen those PRs yet.

- you need to build solid history on bitcoin core with your commits and contributions to be made a maintainer and once that happens you're going to have an area of focus like wallets, rpc and other components of bitcoin core
