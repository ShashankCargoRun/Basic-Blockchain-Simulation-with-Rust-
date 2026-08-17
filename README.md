# Basic Blockchain Simulation with Rust

A basic blockchain simulation built from scratch using **Rust**. This project demonstrates the core concepts behind blockchain technology, including blocks, transactions, cryptographic hashing, Proof of Work mining, nonces, mining rewards, and blockchain validation.

> **Educational Project:** This project is intended for learning and demonstrating fundamental blockchain concepts. It is not intended to be used as a production cryptocurrency or blockchain network.

## Features

* Genesis block creation
* Block creation and chaining
* Transaction handling
* SHA-256 based block hashing
* Proof of Work mining
* Nonce generation
* Mining rewards
* Previous block hash linking
* Blockchain integrity validation
* JSON-formatted transaction data
* Simple command-line output

## Tech Stack

* **Rust**
* **Cargo**
* **SHA-256**
* **Serde / JSON**
* **Linux / Ubuntu**

## Project Structure

```text
Basic-Blockchain-Simulation-with-Rust-/
│
├── src/
│   └── main.rs
│
├── Cargo.toml
├── Cargo.lock
├── .gitignore
└── README.md
```

## Requirements

Make sure you have the following installed:

* Rust
* Cargo
* Linux/Ubuntu or another Rust-supported operating system

Check your Rust installation:

```bash
rustc --version
cargo --version
```

If Rust is not installed, install it using:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Then load Cargo into your current shell:

```bash
source "$HOME/.cargo/env"
```

## Clone the Repository

Clone the project using:

```bash
git clone https://github.com/ShashankCargoRun/Basic-Blockchain-Simulation-with-Rust-.git
```

Move into the project directory:

```bash
cd Basic-Blockchain-Simulation-with-Rust-
```

## Build and Run

Build and run the simulation with:

```bash
cargo run
```

Or build the project first:

```bash
cargo build
```

Then run the compiled executable:

```bash
./target/debug/simulation
```

## How the Blockchain Works

The simulation creates a chain consisting of a Genesis Block followed by mined blocks.

```text
Genesis Block
     │
     ▼
  Block #1
     │
     ▼
  Block #2
```

Each block contains important information such as:

* Block number
* Timestamp
* Previous block hash
* Current block hash
* Transactions
* Nonce

The `Previous Hash` connects each block to the block before it.

## Genesis Block

The first block is the **Genesis Block**.

Example:

```text
Block #0
Timestamp: 1786989478
Previous Hash: 0
Hash: 8a522f6557f0a98232e9aec46653b6b502a4d78e30cf8e33613008e69d686e72
Transactions: []
Nonce: 0
```

Because the Genesis Block is the first block in the chain, it does not have a previous block. Therefore, its previous hash is set to `0`.

## Block #1

The first mined block contains two transactions:

```text
Alice   → Bob       50.0
Bob     → Charlie   30.0
```

The block references the Genesis Block using its previous hash.

Example mined hash:

```text
0000ce384087a86fd3ec48ea239ebd4cb34cc7e86dcd157ca73cd10fb4677e18
```

The nonce found during mining was:

```text
138616
```

## Block #2

The second mined block contains:

```text
system  → miner1    10.0
Charlie → David     20.0
David   → Alice     15.0
```

The first transaction represents a simple mining reward:

```text
system → miner1 : 10.0
```

The mined block produced the following hash:

```text
000085a4feff0214623a970400cfc40735233dc3c05f391ab8a2951df0cd5a00
```

The nonce found during mining was:

```text
14925
```

## Proof of Work

This project demonstrates a basic **Proof of Work (PoW)** mechanism.

During mining, the program repeatedly changes the block's nonce and calculates its hash until a hash satisfying the required difficulty is found.

In this simulation, the mined hashes begin with:

```text
0000
```

For example:

```text
0000ce384087a86fd3ec48ea239ebd4cb34cc7e86dcd157ca73cd10fb4677e18
```

and:

```text
000085a4feff0214623a970400cfc40735233dc3c05f391ab8a2951df0cd5a00
```

The nonce is the value that allows the block to produce a hash meeting the mining difficulty.

## Transactions

Transactions are represented using sender, recipient, and amount fields.

Example:

```json
{
  "sender": "Alice",
  "recipient": "Bob",
  "amount": 50.0
}
```

The simulation demonstrates transactions between different participants:

| Sender  | Recipient | Amount |
| ------- | --------- | -----: |
| Alice   | Bob       |   50.0 |
| Bob     | Charlie   |   30.0 |
| Charlie | David     |   20.0 |
| David   | Alice     |   15.0 |
| system  | miner1    |   10.0 |

## Blockchain Validation

After mining all blocks, the blockchain is validated.

The program produces:

```text
Is blockchain valid? true
```

This confirms that the blockchain passes the validation logic implemented in the simulation.

The blocks are linked using their hashes:

```text
Block #0
Hash
 │
 ▼
Block #1
Previous Hash = Block #0 Hash
Hash
 │
 ▼
Block #2
Previous Hash = Block #1 Hash
Hash
```

If the data inside an earlier block were modified, its hash would change. The following block would then contain an incorrect `Previous Hash`, allowing the chain's integrity check to detect the change.

## Sample Output

```text
Mining first block...
Mining second block...

Blockchain contents:

Block #0
Timestamp: 1786989478
Previous Hash: 0
Hash: 8a522f6557f0a98232e9aec46653b6b502a4d78e30cf8e33613008e69d686e72
Transactions: []
Nonce: 0

Block #1
Timestamp: 1786989478
Previous Hash: 8a522f6557f0a98232e9aec46653b6b502a4d78e30cf8e33613008e69d686e72
Hash: 0000ce384087a86fd3ec48ea239ebd4cb34cc7e86dcd157ca73cd10fb4677e18
Transactions: [
  {
    "sender": "Alice",
    "recipient": "Bob",
    "amount": 50.0
  },
  {
    "sender": "Bob",
    "recipient": "Charlie",
    "amount": 30.0
  }
]
Nonce: 138616

Block #2
Timestamp: 1786989480
Previous Hash: 0000ce384087a86fd3ec48ea239ebd4cb34cc7e86dcd157ca73cd10fb4677e18
Hash: 000085a4feff0214623a970400cfc40735233dc3c05f391ab8a2951df0cd5a00
Transactions: [
  {
    "sender": "system",
    "recipient": "miner1",
    "amount": 10.0
  },
  {
    "sender": "Charlie",
    "recipient": "David",
    "amount": 20.0
  },
  {
    "sender": "David",
    "recipient": "Alice",
    "amount": 15.0
  }
]
Nonce: 14925

Is blockchain valid? true
```

## What This Project Demonstrates

This project provides a simple practical demonstration of:

1. **Blockchain data structures**
2. **Genesis blocks**
3. **Block hashing**
4. **SHA-256 cryptographic hashing**
5. **Transactions**
6. **Previous hash references**
7. **Proof of Work**
8. **Nonce generation**
9. **Mining rewards**
10. **Blockchain integrity**
11. **Blockchain validation**

## Future Improvements

Possible improvements for this project include:

* [ ] Digital signatures
* [ ] Public/private key based wallets
* [ ] Transaction verification
* [ ] Adjustable mining difficulty
* [ ] Dynamic mining rewards
* [ ] Persistent blockchain storage
* [ ] Peer-to-peer networking
* [ ] Multiple blockchain nodes
* [ ] Transaction pool / mempool
* [ ] Merkle tree implementation
* [ ] Command-line interface
* [ ] Unit and integration tests

## Repository

**GitHub:** [Basic Blockchain Simulation with Rust](https://github.com/ShashankCargoRun/Basic-Blockchain-Simulation-with-Rust-)

## Author

**Shashank Mishra**

Built as a learning project to understand the fundamental concepts of blockchain technology and Rust programming.

## License

This project is intended for educational and learning purposes.

