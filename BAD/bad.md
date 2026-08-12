# Blockchain Application Development

- [Blockchain Application Development](#blockchain-application-development)
  - [Chapter 1: Introduction to Blockchain](#chapter-1-introduction-to-blockchain)
    - [1.1 Glossary of Key Terms](#11-glossary-of-key-terms)
    - [1.2 Blockchain Process (Step‑by‑Step)](#12-blockchain-process-stepbystep)
    - [1.3 Blockchain Characteristics](#13-blockchain-characteristics)
    - [1.4 Smart Contracts](#14-smart-contracts)
    - [1.5 Types of Blockchain (Comparison)](#15-types-of-blockchain-comparison)
    - [1.6 Example Blockchain Applications](#16-example-blockchain-applications)
    - [1.7 Use Cases](#17-use-cases)
  - [Chapter 2: Discovering Blockchain Technology](#chapter-2-discovering-blockchain-technology)
    - [2.1 Elements of Trust](#21-elements-of-trust)
    - [2.2 Core Technologies](#22-core-technologies)
    - [2.3 Hash Function](#23-hash-function)
      - [2.3.1 Block Header](#231-block-header)
      - [2.3.2 Merkle Tree](#232-merkle-tree)
    - [2.4 Public Key Cryptography](#24-public-key-cryptography)
    - [2.5 Peer‑to‑Peer Network](#25-peertopeer-network)
    - [2.6 Consensus Protocols](#26-consensus-protocols)
      - [2.6.1 Proof of Work (PoW)](#261-proof-of-work-pow)
      - [2.6.2 Proof of Stake (PoS)](#262-proof-of-stake-pos)
        - [2.6.3 PoS in Ethereum](#263-pos-in-ethereum)
      - [2.6.4 Practical Byzantine Fault Tolerance (PBFT)](#264-practical-byzantine-fault-tolerance-pbft)
      - [2.6.5 Bitcoin UTXO Model](#265-bitcoin-utxo-model)
  - [Chapter 3: Ethereum Platform](#chapter-3-ethereum-platform)
    - [3.1 Ethereum Overview](#31-ethereum-overview)
    - [3.2 Ethereum Nodes](#32-ethereum-nodes)
    - [3.3 Ethereum Node Components](#33-ethereum-node-components)
    - [3.4 Ethereum Accounts](#34-ethereum-accounts)
    - [3.5 Ethereum Wallet](#35-ethereum-wallet)
    - [3.6 Seed Words (Recovery/Mnemonic Phrase)](#36-seed-words-recoverymnemonic-phrase)
    - [3.7 Ether (ETH)](#37-ether-eth)
    - [3.8 Gas](#38-gas)
    - [3.9 EIP1559 (London Upgrade – August 5, 2021)](#39-eip1559-london-upgrade--august-5-2021)
    - [3.10 Gas Costs in EVM](#310-gas-costs-in-evm)
    - [3.11 Transaction Fee Calculation](#311-transaction-fee-calculation)
    - [3.12 Ethereum Virtual Machine (EVM)](#312-ethereum-virtual-machine-evm)
    - [3.13 Merkle Patricia Trie](#313-merkle-patricia-trie)
      - [3.13.1 Transaction Trie](#3131-transaction-trie)
      - [3.13.2 Receipt Trie](#3132-receipt-trie)
      - [3.13.3 World State Trie](#3133-world-state-trie)
    - [3.14 Building Merkle Patricia Trie](#314-building-merkle-patricia-trie)
    - [3.15 Verification at a Full Node](#315-verification-at-a-full-node)
    - [3.16 Ethereum Blockchain Synchronization](#316-ethereum-blockchain-synchronization)
    - [3.17 Limitations of PoW‑Based Ethereum](#317-limitations-of-powbased-ethereum)
    - [3.18 Ethereum 2.0 (Eth2) Upgrade](#318-ethereum-20-eth2-upgrade)

---

## Chapter 1: Introduction to Blockchain

### 1.1 Glossary of Key Terms

| Term                    | Definition                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------ |
| **Distributed Ledger**  | A database shared and synchronized across multiple sites, institutions, or geographies.                |
| **Blockchain**          | A type of distributed ledger containing linear, chronological blocks of data linked cryptographically. |
| **Node**                | A computer that participates in the blockchain network by validating and relaying transactions.        |
| **Block**               | A collection of transactions bundled together and added to the blockchain.                             |
| **Transaction**         | A record of value or information transfer between parties on the blockchain.                           |
| **Smart Contract**      | Self-executing code with agreement terms directly written into lines of code.                          |
| **Consensus Mechanism** | A process used by nodes to agree on transaction validity and ledger state.                             |

---

### 1.2 Blockchain Process (Step‑by‑Step)

1. **Transaction Request** – Someone requests a transaction to be added.  
2. **Broadcast** – The transaction is broadcasted to the peer‑to‑peer network of nodes.  
3. **Validation** – Nodes validate the transaction using known algorithms.  
4. **Block Creation** – The transaction is combined with others to form a new block.  
5. **Permanent Addition** – The new block is appended to the existing blockchain in an unalterable way.

---

### 1.3 Blockchain Characteristics

| Characteristic        | Description                                            |
| --------------------- | ------------------------------------------------------ |
| **Data Immutability** | Data cannot be altered once recorded.                  |
| **Decentralization**  | No intermediary is required.                           |
| **Transparency**      | The ledger is auditable by participants.               |
| **Trust**             | Trust is established through cryptographic mechanisms. |

---

### 1.4 Smart Contracts

- Self‑enforcing agreements embedded in computer code.  
- Enable execution of business logic on the blockchain.  
- Perform credible transactions without third parties.  
- Can feed external data into the contract via **oracles**.

---

### 1.5 Types of Blockchain (Comparison)

| Feature            | Public            | Private               | Consortium            |
| ------------------ | ----------------- | --------------------- | --------------------- |
| Permissionless     | ✅                 | ❌                     | ❌                     |
| Read Access        | Anyone            | Only authorized users | Depends               |
| Write Access       | Anyone            | Only authorized users | Only authorized users |
| Ownership          | None              | Single entity         | Multiple entities     |
| Participants Known | No                | Yes                   | Yes                   |
| Transaction Speed  | Slow              | Fast                  | Fast                  |
| Example            | Bitcoin, Ethereum | Hyperledger Fabric    | R3 Corda              |

---

### 1.6 Example Blockchain Applications

| Platform               | Type                   | Currency      | Features                                 |
| ---------------------- | ---------------------- | ------------- | ---------------------------------------- |
| **Bitcoin**            | Public, Permissionless | Bitcoin (BTC) | Currency exchange only                   |
| **Ethereum**           | Public, Permissionless | Ether (ETH)   | Currency exchange + Smart Contracts      |
| **Hyperledger Fabric** | Private, Permissioned  | N/A           | Smart Contracts + Customizable consensus |

---

### 1.7 Use Cases

- **Supply Chain Management** – Immutable records, automated payments/penalties, no intermediary.  
- **Identity Management** – Self‑sovereign, decentralised, secure verification.  
- **Electronic Health Records (EHR) Sharing** – Secure, private, auditable medical data.  
- **P2P Insurance** – Decentralised platform with automated claims processing.

---

## Chapter 2: Discovering Blockchain Technology

### 2.1 Elements of Trust

| Element           | How It Is Achieved                 |
| ----------------- | ---------------------------------- |
| Immutable Records | Distributed immutable ledger       |
| Verification      | Smart Contract functions/modifiers |
| Validation        | Smart Contract functions/modifiers |
| Consensus         | Blockchain protocol                |
| Identity          | Private‑public key cryptography    |
| Confidentiality   | Cryptography and hashing           |
| Security          | Cryptography and hashing           |
| Privacy           | Cryptography and hashing           |

---

### 2.2 Core Technologies

1. Hash Function  
2. Public Key Cryptography  
3. Peer‑to‑Peer Network  
4. Consensus Protocols

---

### 2.3 Hash Function

**Definition** – Maps arbitrary‑size data to a fixed‑size output (hash/digest).  

**Properties**:

- Deterministic  
- Quick computation  
- One‑way (non‑reversible)  
- Negligible collision probability  
- Small input change → large output change  

**Examples** – MD5, SHA‑256 (SHA‑2), Keccak‑256 (superseded SHA‑3)  

**Uses** – Integrity checking, password storage, blockchain linking.

---

#### 2.3.1 Block Header

- Provides a summary of the block and its contents.  
- Hash of the header becomes the block’s unique identifier, inserted into the next block’s header to form the chain.  
- Generated via **SHA‑256 double hashing**.

| Field              | Description                                | Size     |
| ------------------ | ------------------------------------------ | -------- |
| **Version**        | Block version                              | 4 bytes  |
| **hashPrevBlock**  | Hash of the previous block                 | 32 bytes |
| **hashMerkleRoot** | Hash of all transactions (Merkle root)     | 32 bytes |
| **Time**           | Epoch time of block creation               | 4 bytes  |
| **Bits**           | Current target difficulty (compact format) | 4 bytes  |
| **Nonce**          | 32‑bit number used to find a valid hash    | 4 bytes  |

---

#### 2.3.2 Merkle Tree

**Construction** (example with 7 transactions):

1. Hash each transaction: `Hᵢ = SHA256(SHA256(Tᵢ))`
2. Pair and hash consecutive hashes; duplicate the last if odd:  
   `H₁₂ = SHA256(SHA256(H₁+H₂))`, … , `H₇₇ = SHA256(SHA256(H₇+H₇))`  
3. Repeat until one root remains.

```txt
                        root
                         |
            ------------------------------
            |                            |
        H₁₂₃₄                        H₅₆₇₇
            |                            |
       -----------                  -----------
       |         |                  |         |
    H₁₂       H₃₄                H₅₆       H₇₇
       |         |                  |         |
     ----       ----              ----       ----
     |  |       |  |              |  |       |  |
    H₁  H₂     H₃  H₄            H₅  H₆     H₇  H₇
     |  |       |  |              |  |       |  |
    T₁  T₂     T₃  T₄            T₅  T₆     T₇  T₇
```

**Verification** – To prove T₅ is included, provide only H₁₂₃₄, H₆, and H₇₇ (obtained from full nodes).  

**Benefits** – Proves data integrity, requires little storage/computation, minimises network transmission.

---

### 2.4 Public Key Cryptography

- Uses **ECDSA** (Elliptic Curve Digital Signature Algorithm).  
- **Private key** – kept secret; used to sign transactions.  
- **Public key** – shared; used to verify signatures.  
- A transaction cannot be forged without the private key.  
- Public address = hash of the public key (used to receive funds).

---

### 2.5 Peer‑to‑Peer Network

- A group of nodes that collectively store and share files, with equal power, enabling trustless transactions.  

**Advantages** – Greater security, DoS resistance, tamper‑resistant, censorship‑resistant.  

**Disadvantages** – High computing power required (every node updates), less scalable, difficult to regulate.

---

### 2.6 Consensus Protocols

A procedure for all peers to agree on the ledger state – every new block is the single version of truth.

---

#### 2.6.1 Proof of Work (PoW)

- Miners solve a cryptographic puzzle: find a nonce such that the block header hash is **below the target** (has a required number of leading zeros).  
- Difficulty adjusts every 2016 blocks to maintain a ~10‑minute block time (e.g., if blocks come too fast, the target shrinks, increasing difficulty).  
- Highly CPU‑ and energy‑intensive.  
- **Mining pools** combine computational power and split rewards proportionally.

---

#### 2.6.2 Proof of Stake (PoS)

- Validators stake a deposit to participate.  
- They bet on the validity of a block; rewards are proportional to the stake.  
- Cheaters lose their stake and are banned.  

**Advantages over PoW** – Lower entry barrier, greater decentralisation, better scalability (supports sharding).

---

##### 2.6.3 PoS in Ethereum

- **Becoming a validator** – Stake 32 ETH, run execution/consensus clients, join an activation queue.  
- **Block proposal** – One epoch = 32 slots (12 seconds each); validators are shuffled and randomly assigned to slots to prevent collusion. One validator per slot proposes a block; others attest (vote).  
- **Rewards** – Proposers and attesters earn ETH.  
- **Penalties** – Offline or dishonest behaviour (e.g., double‑proposing, contradictory attestations) results in loss of staked ETH.

---

#### 2.6.4 Practical Byzantine Fault Tolerance (PBFT)

- Requires **3F + 1** nodes (F = maximum faulty nodes tolerated).  
- **2F + 1** nodes must agree on a transaction.  
- **Process**:  
  1. Transaction broadcast to all nodes.  
  2. Proposer chosen round‑robin.  
  3. Proposer sends PRE‑PREPARE with the block.  
  4. Nodes send PREPARE (need 2F+1).  
  5. Nodes send COMMIT (need 2F+1).  
  6. Block finalised; new proposer chosen.

---

#### 2.6.5 Bitcoin UTXO Model

- **UTXO** = Unspent Transaction Output.  
- Bitcoin does **not** store account balances; balance is the sum of all UTXOs.  
- A transaction consumes entire UTXOs; change is returned as a new UTXO.  

**Transaction fields** – Version, Flag (SegWit indicator), In‑counter, Input list, Out‑counter, Output list, Witnesses, Lock time.  

**Coinbase transaction** – First in each block; contains block reward (halved every 4 years until 2140) and transaction fees.  

**Double‑spending** – Attempting to spend the same UTXO twice.

Mitigations:

- Accept the first transaction seen.  
- If simultaneous, create two branches; next block determines the winner.  
- The longest chain is considered valid.  
- Wait for 6 confirmations.  
- A 51% attack can reverse transactions (risk in smaller networks).

---

## Chapter 3: Ethereum Platform

### 3.1 Ethereum Overview

- Proposed by Vitalik Buterin in 2013 to extend blockchain beyond currency.  
- Dr. Gavin Wood co‑founded and built the EVM and Solidity.  
- Aims to simplify dApp development.  

**Main innovations** – EVM (Turing‑complete), smart contracts, and a **Patricia Merkle Tree**‑based blockchain.  

**Genesis block** – The first block, created at network launch.

---

### 3.2 Ethereum Nodes

| Type           | Data Stored                          | Resource Demand | Query Capability                         | Consensus Participation |
| -------------- | ------------------------------------ | --------------- | ---------------------------------------- | ----------------------- |
| **Full Node**  | Entire blockchain + all transactions | High            | All historical data                      | Yes                     |
| **Light Node** | Only block headers                   | Low             | Relies on full nodes for historical data | No                      |

**Archive Node** – Stores all history from genesis; used by explorers, wallets, and analytics platforms.

---

### 3.3 Ethereum Node Components

| Component          | Role                                                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------ |
| **JSON‑RPC API**   | Exposes client functionality to other nodes and users.                                           |
| **Client Process** | Handles API requests, coordinates execution, dispatches to EVM, manages mempool, appends blocks. |
| **EVM**            | Executes smart contracts and transactions; maintains state.                                      |
| **Memory Pool**    | Holds unconfirmed transactions until they are included in a block.                               |
| **Blockchain DB**  | Stores transaction data, contract bytecode, and state.                                           |

---

### 3.4 Ethereum Accounts

| Type                       | Control                   | Identification                  | Balance | Operations                                                                                |
| -------------------------- | ------------------------- | ------------------------------- | ------- | ----------------------------------------------------------------------------------------- |
| **Externally Owned (EOA)** | Private key               | Public key                      | Ether   | Can start **transaction** (writes to chain, consumes gas, changes state)                  |
| **Contract Account**       | Bytecode (contract logic) | Address generated at deployment | Ether   | Can start **call** (reads only, no gas, no state change) – has associated code (bytecode) |

---

### 3.5 Ethereum Wallet

An application that lets users manage accounts – view balances, send/receive Ether.  
Types: software‑based (desktop, mobile, web) or hardware‑based (physical device).

---

### 3.6 Seed Words (Recovery/Mnemonic Phrase)

- An ordered list of **12‑24** dictionary words.  
- Acts as a master key to regenerate all private keys and addresses.  
- Allows full wallet recovery if access is lost.  
- Security: 2¹²⁸ (12 words) to 2²⁵⁶ (24 words) combinations; the checksum (last word) prevents forgery.

---

### 3.7 Ether (ETH)

| Unit       | Other Name | Value in Wei |
| ---------- | ---------- | ------------ |
| Wei        | –          | 1            |
| Kwei       | Babbage    | 1e3          |
| Mwei       | Lovelace   | 1e6          |
| Gwei       | Shannon    | 1e9          |
| Microether | Szabo      | 1e12         |
| Milliether | Finney     | 1e15         |
| Ether      | –          | 1e18         |

---

### 3.8 Gas

- Unit measuring transaction fees.  
- Depends on the computational resources (opcodes) required.  
- **Purpose**: Prevents DoS attacks.  
- **Formula**: `Transaction Fee = Gas Used × Price per Gas Unit (in ETH)`  
- **Gas Limit** – maximum gas a transaction can consume; if exceeded, the transaction reverts.  
- **Block Gas Limit** – maximum total gas for all transactions in one block.

---

### 3.9 EIP1559 (London Upgrade – August 5, 2021)

Makes fees more predictable.  

**Fee components**:  

- **Base fee** – standard charge based on network traffic (burned).  
- **Priority fee (tip)** – optional incentive for miners.  
- **Max fee** – optional cap (base + priority); any leftover refunded.  

Burning base fees reduces ETH supply, creating a deflationary effect.

---

### 3.10 Gas Costs in EVM

| Opcode           | Description             | Gas Cost |
| ---------------- | ----------------------- | -------- |
| ADD, SUB         | Addition/Subtraction    | 3        |
| MUL, DIV         | Multiplication/Division | 5        |
| LT, GT, SLT, SGT | Comparisons             | 3        |
| MLOAD            | Load from memory        | 3        |
| MSTORE           | Store to memory         | 3        |
| SLOAD            | Load from storage       | 200      |
| SSTORE           | Store to storage        | >5000    |
| CREATE           | Deploy contract         | 32000    |
| Transfer         | Ether transfer          | 21000    |

---

### 3.11 Transaction Fee Calculation

**Inputs** – Gas Limit, Base Fee, Priority Fee, (optional) Transfer Amount.

| Calculated Value          | Formula                                 |
| ------------------------- | --------------------------------------- |
| Total transaction fee     | Gas Limit × (Base Fee + Priority Fee)   |
| ETH deducted from account | Total transaction fee + Transfer Amount |
| ETH received by recipient | Transfer Amount                         |
| Tip to validator          | Gas Limit × Priority Fee                |
| ETH burned                | Gas Limit × Base Fee                    |

---

### 3.12 Ethereum Virtual Machine (EVM)

- Stack‑based, Turing‑complete, sandboxed virtual machine.  
- Runs smart contracts on Ethereum.  

**Memory areas**:

- **Volatile memory** – word‑addressed byte array (reads 256‑bit, writes 8/256‑bit).  
- **Storage** – persistent key‑value store (256‑bit keys/values); each contract has its own; expensive to read/write.  

**Byte code** – compiled smart contract.  
**Opcodes** – low‑level instructions (similar to assembly).

---

### 3.13 Merkle Patricia Trie

Combines Merkle Tree and Patricia Trie.  
**Desired properties**:  

- Quick root recalculation after updates.  
- Bounded depth (prevents DoS attacks).  
- Root depends only on data, not update order.  

Each Ethereum block contains three roots:  

- Transaction root  
- Receipt root  
- World state root

---

#### 3.13.1 Transaction Trie

- **Not updated** after block is mined.  
- Stores: nonce, gas price, gas limit, recipient, value, signature, and either initialisation (contract creation) or data (message call).

---

#### 3.13.2 Receipt Trie

- **Never updated**.  
- Stores: post‑transaction state, cumulative gas used, logs, and a Bloom filter for quick log lookups.

---

#### 3.13.3 World State Trie

- **Updated over time**; all fields except code hash are mutable.  
- Stores per‑account: nonce, balance, storage root, and code hash (empty for EOAs).

---

### 3.14 Building Merkle Patricia Trie

**Node types**:  

- **Extension** – shared prefix: `| prefix | shared nibbles | next node |`  
- **Branch** – diverging paths: `| 0 | 1 | 2 | … | f | value |`  
- **Leaf** – end of a key: `| prefix | key‑end | value |`  

**Prefixes**:  

| Node Type | Path Length | Prefix |
| --------- | ----------- | ------ |
| Extension | Even        | 0x00   |
| Extension | Odd         | 0x1    |
| Leaf      | Even        | 0x20   |
| Leaf      | Odd         | 0x3    |

*Prefix also aligns the path to even nibbles.*

**Example** (keys and values):  

- `A711355` → 45.0 ETH  
- `A77D337` → 1.00 WEI  
- `A7F9365` → 1.1 ETH  
- `A77D397` → 0.12 ETH  

```txt
                   Extension
                   +---------------+
                   | 0x00 | A7 |   |
                   +---------------+
                                 |
                   Branch        |
             +-----+---+-----+---+-----+---+-------+
             | ... | 1 | ... | 7 | ... | f | value |
             +-----+---+-----+---+-----+---+-------+
                     |         |         |
Leaf                 |   Extension      Leaf
+------+------+--------+ +---+----+---+ +------+------+---------+
| 0x20 | 1355 | 45 ETH | | 0 | d3 |   | | 0x20 | 9365 | 1.1 ETH |
+------+------+--------+ +---+----+---+ +------+------+---------+
                                    |
                  Branch            |
                  +-----+---+-----+---+-----+-------+
                  | ... | 3 | ... | 9 | ... | value |
                  +-----+---+-----+---+-----+-------+
                          |         |
          Leaf            |    Leaf |
          +-----+---+-------+  +-----+---+----------+
          | 0x3 | 7 | 1 WEI |  | 0x3 | 7 | 0.12 ETH |
          +-----+---+-------+  +-----+---+----------+
```

---

### 3.15 Verification at a Full Node

- Transactions are organised in a transaction trie.  
- EVM executes them and generates receipts, which are arranged in a receipt trie.  
- The world state changes (only one instance per node).  
- **Block validity** is confirmed if all three root hashes in the block header match those recomputed.  

**What can be verified** – transaction inclusion, transaction output, account existence, and account balance.

---

### 3.16 Ethereum Blockchain Synchronization

| Mode      | Historical Data         | History Validation       | Speed   | Integrity | New Block Validation |
| --------- | ----------------------- | ------------------------ | ------- | --------- | -------------------- |
| **Full**  | Entire blockchain       | Full validation          | Slow    | Highest   | Yes                  |
| **Fast**  | Entire blockchain       | 64 blocks prior to start | Faster  | Higher    | Yes                  |
| **Light** | Only current state trie | None                     | Fastest | Lower     | Yes                  |

---

### 3.17 Limitations of PoW‑Based Ethereum

- Energy‑intensive mining.  
- Slow transaction processing.  
- High financial barrier limits scalability.

---

### 3.18 Ethereum 2.0 (Eth2) Upgrade

- Transition to **Proof of Stake** – reduces energy consumption.  
- Introduces **shard chains** – improves scalability.  
- Lower entry barrier for validators.
