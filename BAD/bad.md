# Blockchain Application Development

## Chapter 1: Introduction to Blockchain

### Glossary

- **Distributed Ledger**: A database that is shared and synchronized across multiple sites, institutions, or geographies.
- **Blockchain**: A type of distributed ledger that contains linear, chronological blocks of data that are linked cryptographically.
- **Node**: A computer that participates in the blockchain network by validating and relaying transactions.
- **Block**: A collection of transactions that are bundled together and added to the blockchain.
- **Transaction**: A record of a transfer of value or information between parties on the blockchain.
- **Smart Contract**: A self-executing contract with the terms of the agreement between buyer and seller being directly written into lines of code.
- **Consensus Mechanism**: A process used by nodes in a blockchain network to agree on the validity of transactions and the state of the ledger.

### Blockchain Process

- Someone requests a **transaction** to be added to the blockchain.
- The transaction is broadcasted to a network of peer-to-peer computers, known as **nodes**.
- The transaction is validated by these nodes using known algorithms.
- The transaction is combined with other transactions to create a new **block** of data for the ledger.
- The new block is then added to the existing blockchain, in a way that is permanent and unalterable.

### Blockchain Characteristics

- **Data Immutability**
- **Decentralization** (No intermediary)
- **Transparency** (Auditable)
- **Trust**

### Smart Contracts

- Capability of executing code for embedding business logic on the blockchain.
- Self-enforcing agreements embedded in computer code
- Perform credible transactions without third parties
- May feed external data into the smart contract through **oracles**.

### Type of Blockchain

|                    | Public            | Private               | Consortium            |
| ------------------ | ----------------- | --------------------- | --------------------- |
| Permissionless     | ✅                 | ❌                     | ❌                     |
| Read Access        | Anyone            | Only authorized users | Depends               |
| Write Access       | Anyone            | Only authorized users | Only authorized users |
| Ownership          | None              | Single entity         | Multiple entities     |
| Participants Known | No                | Yes                   | Yes                   |
| Transaction Speed  | Slow              | Fast                  | Fast                  |
| Example            | Bitcoin, Ethereum | Hyperledger Fabric    | R3 Corda              |

### Example of Blockchain Applications

- **Bitcoin**
  - Public, permissionless
  - Bitcoin
  - Currency exchange only
- **Ethereum**
  - Public, permissionless
  - Ether
  - Currency exchange + Smart Contracts
- **Hyperledger Fabric**
  - Private, permissioned
  - Smart Contracts
  - Customizable consensus protocol

### Use cases

- **Supply Chain Management**
  - Immutable and non-repudiable record of transactions
  - Automated payment on delivery
  - Automated penalties for late delivery
  - Decentralized supply chain (No intermediary)
- **Identity Management**
  - Self-sovereign identity
  - Decentralized identity management
  - Secure and private identity verification
- **Electronic Health Records (EHR) Sharing**
  - Secure and private sharing of medical information
  - Immutable and auditable health records
- **P2P Insurance**
  - Decentralized insurance platform
  - Automated claims processing

## Chapter 2: Discovering Blockchain Technology

### Element of Trust

- **Immutable Records**: Distributed immutable ledger
- **Verification**: Smart Contract functions/modifiers
- **Validation**: Smart Contract functions/modifiers
- **Consensus Mechanism**: Blockchain protocol
- **Identity**: Private-Public key pair cryptography
- **Confidentiality**: Cryptography and hashing algorithms
- **Security**: Cryptography and hashing algorithms
- **Privacy**: Cryptography and hashing algorithms

### Technologies Used in Blockchain

- [Hash Function](#hash-function)
- [Public Key Cryptography](#public-key-cryptography)
- [Peer-to-Peer Network](#peer-to-peer-network)
- [Consensus Protocols](#consensus-protocols)

#### Hash Function

- Map arbitrary size data to fixed-size output (hash/digest)
- **Properties**
  - Deterministic
  - Quick computation
  - One-way function
  - Astronomically low probability of collision
  - Slight change in input drastically changes output
- Examples
  - MD5
  - SHA-256 (SHA-2 family)
  - Keccak-256 (Superseded SHA-3)
- Functions
  - Integrity Checking
  - Password Storage and Protection
  - Blockchain (Chain of blocks linked by hashes)

##### Block Header

- Used to provide a summary of the block and its contents.
- Hashing the block header produces a unique identifier for the block, which is inserted into the next block's header to create a chain of blocks.
- Use **SHA-256 double hashing** to generate the block hash.

| Field          | Description                                         | Size     |
| -------------- | --------------------------------------------------- | -------- |
| Version        | Version of the block                                | 4 bytes  |
| hashPrevBlock  | Hash of the previous block                          | 32 bytes |
| hashMerkleRoot | Hash of the Merkle root (All transactions)          | 32 bytes |
| Time           | Epoch time of the block creation                    | 4 bytes  |
| Bits           | Current target difficulty in compact format         | 4 bytes  |
| Nonce          | 32-bit number needed to generate a valid block hash | 4 bytes  |

##### Merkle Tree

Given 7 transactions, the Merkle tree is constructed as follows:

1. Hash each transaction T1 to T7 to get H1 to H7, using

    $H_i = SHA256(SHA256(T_i))$

2. Pair each hash and hash them together to get the next level of hashes. If there is an odd number of hashes, duplicate the last hash to make a pair.

    $H_{12} = SHA256(SHA256(H_1 + H_2))$

    $H_{34} = SHA256(SHA256(H_3 + H_4))$

    $H_{56} = SHA256(SHA256(H_5 + H_6))$

    $H_{77} = SHA256(SHA256(H_7 + H_7))$

3. Repeat the process until there is only one hash left, which is the Merkle root.

    $H_{1234} = SHA256(SHA256(H_{12} + H_{34}))$

    $H_{5677} = SHA256(SHA256(H_{56} + H_{77}))$

    $H_{root} = SHA256(SHA256(H_{1234} + H_{5677}))$

```txt

                        root
                         |
            ------------------------------
            |                            |
        H_{1234}                     H_{5677}
            |                            |
       -----------                  -----------
       |         |                  |         |
    H_{12}     H_{34}            H_{56}     H_{77}
       |         |                  |         |
     ----       ----              ----       ----
     |  |       |  |              |  |       |  |
    H1  H2     H3  H4            H5  H6     H7  H7
     |  |       |  |              |  |       |  |
    T1  T2     T3  T4            T5  T6     T7  T7
```

To verify that a transaction is included in the Merkle tree, you only need to provide the hashes along the path from the transaction to the root. For example, to verify T5, you need H1234, H6 and H77, which can be downloaded from **full node peers**.

Benefits:

- Used to prove integrity of data
- Require little memory/disk space (Easily to proof, fast computation)
- Require only small amounts of information to be transmitted across the network

#### Public Key Cryptography

- ECDSA (Elliptic Curve Digital Signature Algorithm) is a public key cryptography algorithm used in blockchain.
- Uses a pair of keys: a public key and a private key.
- The private key is kept secret and is used to sign transactions, while the public key is shared with others to verify the signature.
- The message cannot be forged without the private key, and the signature can be verified by anyone with the public key.
- In blockchain, it is used to ensure the authenticity and integrity of transactions when they are broadcasted to the network.
- The public key is hashed to create a public address, which is used to receive funds. The private key is used to sign transactions and spend funds from the corresponding public address.

#### Peer-to-Peer Network

- Group of nodes collectively store and share files.
- Equal power, allow transactions without need for intermediary.
- **Advantages**:
  - Greater security
  - Immune to DoS attacks
  - With consensus protocol, data is almost impossible to tamper with
  - Resistant to censorship by central authorities
- **Disadvantages**:
  - Distributed ledgers must be updated on every single node, require massive computing power
  - Less scalable
  - Difficult to control and regulate

#### Consensus Protocols

- Procedure for all peers in a blockchain network to reach **common agreement** on the state of the distributed ledger.
- Ensure every new block added to the blockchain is the one and only version of the truth that is agreed upon by all nodes in the network.

##### Proof of Work (PoW)

- Miners solve a complex mathematical puzzle to validate transactions and create new blocks.
- In Bitcoin, the puzzle is to find a nonce that, when hashed with the block header, produces a hash that is **less than the current target / produce certain count of leading zeros**, given by the network's difficulty level.
- The network difficulty adjusts every 2016 blocks to ensure that a new block is mined approximately every 10 minutes, which is dependent on the hash rate of the network.
- E.g., if all blocks are mined in 10 days instead of 14 days, the target will be multiplied by 10/14 (shrinking), increasing the difficulty of the puzzle and making it harder for miners to find a valid nonce.
- Very CPU-intensive and energy-consuming.
- **Mining Pools**: Groups of miners that combine their computational resources to increase their chances of solving the puzzle and earning rewards. The rewards are then distributed among the pool members based on their contributed hash power.

##### Proof of Stake (PoS)

- **Validators**: Responsible for checking validity of new blocks propagated in the network, and creating new blocks when selected as block proposers.
- Pool of validators vote on the validity of new blockchain block.
- Validators must commit a deposit (stake), ethereum requires 32 ETH to become a validator.
- Validators are selected pseudorandomly to create new blocks. (The more cryptocurrency a validator stakes, the higher their chances of being selected to create a new block.)
- Validators are incentivized to act honestly, as they can lose their staked cryptocurrency if they validate fraudulent transactions or attempt to manipulate the blockchain. E.g. propose multiple blocks, submit contradictory attestations/votes
- The created block needs to be broadcasted and validated by other validators in the network, who will vote on its validity. Each validator's vote is weighted based on the amount of cryptocurrency they have staked.
- If the block is validated by a majority of validators, it is added to the blockchain, and the validator who created the block receives a reward in the form of transaction fees and newly minted cryptocurrency.
- Advantages over PoW:
  - **Accessibility** (lower entry barrier)
  - **Decentralization** (lower barrier, more validators)
  - **Scalability** (support sharding, which partitions the blockchain into multiple shard chains, each capable of processing its own transactions and smart contracts)

##### Practical Byzantine Fault Tolerance (PBFT)

- 3F + 1 nodes are required, where F is the maximum number of faulty nodes that can be tolerated in the network.
- 2F + 1 nodes must agree on the validity of a transaction for it to be added to the blockchain.

1. Transaction is broadcasted to all nodes in the network.
2. Proposer chosen in round-robin fashion.
3. Proposer broadcasts PRE-PREPARE message to all nodes, including the proposed block.
4. All nodes broadcast PREPARE message to agree on the proposed block, requiring 2F + 1 PREPARE messages to move to the next step.
5. Prepared nodes broadcast COMMIT message to agree on the proposed block, requiring 2F + 1 COMMIT messages to finalize the block.
6. Finalized block is added to the blockchain, and all nodes moves to FINAL COMMITED state.
7. New proposer is chosen, repeat.

##### Bitcoin UTXO Model

- UTXO (Unspent Transaction Output) 
- Bitcoint does not hold account balances
- Each account adding up number of bills (UTXOs) to get the total balance
- The entire UTXO is spent in a transaction, and any leftover change is sent back to the sender as a new UTXO.

| Field           | Description                                                                                                          |
| --------------- | -------------------------------------------------------------------------------------------------------------------- |
| Version         | Version of the transaction                                                                                           |
| Flag            | A value of 0x0001 indicates that the transaction using SegWit, which removes the signature data from the transaction |
| In-counter      | No of input                                                                                                          |
| List of inputs  |                                                                                                                      |
| Out-counter     | No of output                                                                                                         |
| List of outputs |                                                                                                                      |
| Witnesses       | List of witnesses                                                                                                    |
| Lock time       | Identifies the earliest time or blockchain height at which the transaction may be added to the blockchain            |

- Transactions
  - Movement of value from one address to another
  - Transactions recorded on the blockchain are to be confirmed
  - Transfer of control of funds require signing the transaction with the private key
  - Public key is used to verify the signature and ensure that the transaction is valid
  - Transaction fee is paid in order for a transaction to go through quickly.
- Coinbase Transaction
  - First transaction recorded on every block
  - Contains
    - **Block reward**: Reward received by the miner for successfully discovering a new block. Block reward is halved every 4 years until reaching 0 at the year 2140. 
    - **Transaction fees**: Sum of all transaction fees included in each transaction added to the current block. Transaction fees are paid by users to incentivize miners to include their transactions in the next block.
- Double Spending
  - Attempting to spend the same UTXO in multiple transactions.
  - Can inflate the total supply of a cryptocurrency and undermine the integrity of the blockchain.
  - Solution
    - **First in Line**: Accept the first transaction that reaches the ledger
    - **Tie Breaker**: If same time, create two branches of the blockchain, next block mined will determine which branch is valid, the other branch will be discarded.
    - **Longer chain wins**: Longer chain is always considered the valid chain, as it represents the most computational work done by the network.
    - **Safe waits**: Wait for 6 confirmations before considering a transaction as final, as it is highly unlikely for a transaction to be reversed after 6 confirmations.
    - 51% Attack: If an attacker controls more than 50% of the network's hash rate, they can create a longer chain and reverse transactions, allowing them to double spend. This is a risk in smaller blockchain networks with lower hash rates.

## Chapter 3: Ethereum Platform

### Ethereum Overview

- Vitalik Buterin proposed Ethereum in 2013 to expand the use of blockchain technology beyond cryptocurrency.
- Dr. Gavin Wood, one of the co-founders of Ethereum, developed the Ethereum Virtual Machine (EVM) and the Solidity programming language to enable developers to create decentralized applications (dApps) on the Ethereum blockchain.
- Implement to simplify smart contract development and deployment.
- Main innovations:
  - **EVM (Ethereum Virtual Machine)**: A Turing-complete virtual machine that executes smart contracts on the Ethereum blockchain.
  - **Smart Contracts**: Self-executing contracts with the terms of the agreement between buyer and seller being directly written into lines of code.
  - **Improved Blockchain Design**: Modified version of Merkle Tree called **Patricia Merkle Tree**
- **Genesis block**: The first block in the Ethereum blockchain, created at the network's launch.

### Ethereum Nodes

|                         | Full Node                                                                 | Light Node                                                                   |
| ----------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Data Storage            | Stores the entire blockchain and all its data, including all transactions | Stores only the block headers without block bodies                           |
| Resource Demand         | High resource demand (CPU, memory, storage)                               | Low resource demand (CPU, memory, storage)                                   |
| Query Capabilities      | Can query any data on the blockchain, including historical data           | Cannot query historical data, needs to rely on full nodes for data retrieval |
| Consensus Participation | Can perform block validation and participate in the consensus process     | Cannot perform block validation or participate in the consensus process      |

- **Archive Node**
  - Entire history of the blockchain dating back to the genesis block
  - Used by block explorers, wallets and on chain analytics platforms to provide historical data and insights into the blockchain's activity.

### Ethereum Node

- **JSON-RPC API**:
  - Expose functionality of the client to other nodes and external users
- **Client Process**:
  - Interpret and execute JSON-RPC API requests
  - Coordinates processings
  - Dispatch transactions to the **EVM** for execution
  - Store and retrieve transaction from **memory pool**
  - Append incoming blocks to the local blockchain
- **EVM (Ethereum Virtual Machine)**:
  - Executes smart contracts and transactions
  - Maintains the state of the blockchain
- **Memory Pool**:
  - Temporary hold unconfirmed transactions before they are included in a block
- **Blockchain DB**
  - Keep transaction data & smart contract bytecode & their state

### Ethereum Accounts

- **Externally Owned Accounts (EOA)**
  - User acccount
  - Controlled by private key
  - Identifiable from public key
  - Has Ether balance
  - Can start transaction message (write operation that publishes a transaction on the blockchain, consumes gas, and changes the state of the blockchain)
- **Contract Accounts**
  - Accounts where smart contracts are executed under
  - Address generated at deployment time, identifies its location on the blockchain
  - Has Ether balance
  - Can start call message (invocation of function that does not publish a transaction on the blockchain, does not consume gas, and does not change the state of the blockchain)
  - Has code (bytecode) that is executed by the EVM when a transaction is sent to the contract account

### Ethereum Wallet

- An application that allows users to manage Ethereum accounts, including view balances, send and receive Ether.
- Can be software-based (desktop, mobile, web) or hardware-based (physical device).

### Seed words

- Recovery phrase, mnemonic phrase, or seed phrase
- An ordered list of 12-24 dictionary words
- Used as master key to generate all private keys and public addresses for an Ethereum wallet, allowing users to recover their wallet and access their funds if they lose access to their device or forget their password.
- Essentially unique, 2^128 (12) to 2^256 (24) combinations
- Cannot forge a seed phrase, as the checksum is built into the seed phrase (last word)

### Ether

| Unit       | Other Names | Value in Wei |
| ---------- | ----------- | ------------ |
| Wei        | -           | 1            |
| Kwei       | Babbage     | 1e3          |
| Mwei       | Lovelace    | 1e6          |
| Gwei       | Shannon     | 1e9          |
| Microether | Szabo       | 1e12         |
| Milliether | Finney      | 1e15         |
| Ether      | -           | 1e18         |

### Gas

- Unit of measure for transaction fees
- Depends on the amount of computation resources EVM needs to execute a transaction
- Depends on low level operations (opcodes) executed by the EVM
- **Why**: prevent DoS attack by malicious users

$\text{Transaction Fee} = \text{Gas Used} \times \text{Price per Gas Unit (In Ether)}$

- **Gas Limit**: When the gas limit is reached before transaction is completed, the transaction throws end of gas exception and rolls back.
- **Block Gas Limit**: One block can only contain transactions that consume a total amount of gas up to the `block gas limit`.

### EIP1559 (London-Upgrade - 05/08/2021)

- Introduced a new fee structure
- Make transaction fees more predictable
- Fee Structure
  - **Base Fee**: Standard Charge based on network traffic
  - **Priority Fee (Tip)**: Optional fee paid to miners to prioritize transaction processing
  - **Max Fee**: Optional maximum fee that a user is willing to pay for a transaction, which includes both the base fee and the priority fee. The leftover is refunded to the user after the transaction is processed. Useful when base fee is changing while transaction is pending.
- All base fees must be burned, which reduces the total supply of Ether and increases its scarcity, making it more valuable over time. This is a deflationary mechanism to counteract the inflationary effect of block rewards and transaction fees, which can increase the total supply of Ether over time.

### Gas Cost in EVM

| Opcode           | Description                                                    | Gas Cost |
| ---------------- | -------------------------------------------------------------- | -------- |
| ADD, SUB         | Addition, Subtraction                                          | 3        |
| MUL, DIV         | Multiplication, Division                                       | 5        |
| LT, GT, SLT, SGT | Less than, Greater than, Signed less than, Signed greater than | 3        |
| MLOAD            | Load word from memory                                          | 3        |
| MSTORE           | Save word to memory                                            | 3        |
| SLOAD            | Load word from storage                                         | 200      |
| SSTORE           | Save word to storage                                           | > 5000   |
| CREATE           | Deploy a new contract                                          | 32000    |
| Transfer         | Transfer Ether from one account to another                     | 21000    |

### Transaction Fee Calculation

- Variables
  - **Gas Limit**
  - **Base Fee**
  - **Priority Fee**
  - **(Optional) Transfer Amount**: Only needed if the transaction involves transferring Ether from one account to another.
- Calculate
  - **Total Transaction Fee** = Gas Limit * (Base Fee + Priority Fee)
  - **ETH Deducted from Account** = Total Transaction Fee + Transfer Amount
  - **ETH Received by Recipient** = Transfer Amount
  - **Tip Received by Validator** = Gas Limit * Priority Fee
  - **ETH Burned** = Gas Limit * Base Fee

### Ethereum Virtual Machine (EVM)

- **Properties**
  - Stack-based abstract computing machine
  - Lightweight OS specifically run smart contracts
  - Enable computer to run Ethereum applications
  - EVM is sandboxed
  - Turing Complete instruction set
- **Memory Areas**
  - **Volatile Memory**: Word-addressed byte array, read 256 bits at a time, write on 8 bits or 256 bits at a time
  - **Storage**: Key-value store, each key and value width of 256 bits; every contract has its own storage accessible only by that contract; storage is persistent and expensive to read/write
- **Byte Code**: Compiled code of smart contract
- **Opcodes**: Low-level instructions executed by the EVM, similar to assembly language

### Merkle Patricia Trie

- 3 desired properties
  - New tree root can be **quickly calculated** after create, update, delete operations
  - **Bounded tree depth**, the deeper the tree, the slower the update, attacker can exploit deep tree to DoS attack the network
  - Root of the tree is **data dependent, not update order dependent**, so that the same data will always produce the same root, regardless of the order in which it was added to the tree.
- Combine Merkle Tree and Patricia Trie
- Each Ethereum Block contains
  - Merkle Patricia Root of transactions
  - Merkle Patricia Root of receipts (transaction outputs like status, gas used, logs, contract address, etc.)
  - Merkle Patricia Root of current blockchain state (account balances, contract storage, etc.)

#### Transaction Trie

- 