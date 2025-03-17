# B1 Blockchain Implementation

This repository contains a simple yet comprehensive blockchain implementation in Rust. The blockchain supports key features including block mining with Proof of Work, transaction signing and verification, wallet management, and a command-line interface for interaction.

## Table of Contents

- [Project Structure](#project-structure)
- [Core Components](#core-components)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Technical Details](#technical-details)

## Project Structure

```
blockchain-implementation/
├── src/
│   ├── main.rs              # Entry point of the application
│   ├── block.rs             # Block structure and methods
│   ├── blockchain.rs        # Blockchain structure and operations
│   ├── transaction.rs       # Transaction structure and signing
│   ├── wallet.rs            # Wallet management and key operations
│   ├── merkle_tree.rs       # Merkle tree implementation for transactions
│   ├── node.rs              # Network node implementation
│   ├── cli.rs               # Command-line interface
│   ├── pow.rs               # Proof of Work implementation
│   └── utils.rs             # Utility functions
```

## Core Components

### Block (`block.rs`)
Defines the core block structure containing:
- Block index
- Timestamp
- Transaction list
- Previous block hash
- Current block hash
- Nonce (for Proof of Work)
- Merkle root of transactions

Includes methods for:
- Creating new blocks
- Calculating block hash
- Mining blocks (Proof of Work)

### Blockchain (`blockchain.rs`)
Manages the chain of blocks with functionality for:
- Creating the genesis block
- Adding new blocks to the chain
- Validating the entire chain's integrity
- Persisting the blockchain to a file
- Loading the blockchain from a file

### Transaction (`transaction.rs`)
Defines transaction structure with:
- Sender address
- Receiver address
- Amount
- Digital signature

Provides methods for:
- Creating and signing transactions
- Verifying transaction signatures
- Converting transactions to string format for hashing

### Wallet (`wallet.rs`)
Implements cryptocurrency wallets with:
- ED25519 key pair generation
- Address derivation from public key
- Signing data with private key
- Verifying signatures

### Merkle Tree (`merkle_tree.rs`)
Implements a Merkle tree for transaction verification:
- Creating trees from transaction lists
- Computing the Merkle root for block headers
- Efficient transaction verification

### Node (`node.rs`)
Provides peer-to-peer networking capabilities:
- Managing connections to peer nodes
- Synchronizing blockchain across the network
- Managing blockchain state

### CLI (`cli.rs`)
Command-line interface for interacting with the blockchain:
- Creating new wallets
- Adding transactions
- Mining blocks
- Validating the blockchain

## Features

- **Proof of Work Consensus**: Mining blocks with adjustable difficulty
- **Transaction Security**: Digital signatures using ED25519
- **Data Integrity**: Merkle trees for efficient transaction verification
- **Persistence**: Save and load blockchain state from file storage
- **Network Capability**: P2P network synchronization
- **User Interface**: Simple command-line interface

## Getting Started

### Prerequisites
- Rust and Cargo (latest stable version)
- Required dependencies are specified in the `Cargo.toml` file

### Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/blockchain-implementation.git

# Navigate to the project directory
cd blockchain-implementation

# Build the project
cargo build --release
```

## Usage

The blockchain can be interacted with through the command-line interface:

```bash
# Create a new wallet
cargo run -- create-wallet

# Add a transaction
cargo run -- add-transaction --sender <SENDER_ADDRESS> --receiver <RECEIVER_ADDRESS> --amount <AMOUNT>

# Mine a new block
cargo run -- mine-block --miner <MINER_ADDRESS>

# Validate the blockchain
cargo run -- validate-chain
```

## Technical Details

### Consensus Algorithm
The project uses Proof of Work (PoW) for consensus, where miners must find a hash that meets certain difficulty criteria. The difficulty is configurable when creating the blockchain.

### Cryptography
- **Hashing**: SHA-256 for block hashing
- **Signatures**: ED25519 for transaction signing
- **Key Management**: PKCS#8 format for storage

### Data Structures
- **Block**: Contains block header metadata and transaction list
- **Merkle Tree**: Binary tree of transaction hashes for efficient verification
- **Transaction**: Includes sender, receiver, amount, and signature

### Networking
Simple peer-to-peer network with capabilities to sync blockchain data across nodes.
