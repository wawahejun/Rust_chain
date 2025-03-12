# Rust Blockchain Framework

## Project Overview

This project is a modular Rust blockchain framework demo with three versions: B1 (Educational), B2 (Core), and B3 (Extended). Each version is optimized and expanded for different use cases, suitable for needs ranging from learning blockchain fundamentals to developing blockchain applications.

---

## Version Comparison

| Feature            | B1 (Educational)                 | B2 (Core)                       | B3 (Extended)                     |
|--------------------|---------------------------------|----------------------------------|----------------------------------|
| **Target Users**    | Beginners, Teaching Scenarios   | Developers, Rapid Prototyping   | Advanced Developers, Production  |
| **Core Features**   | Blocks, Transactions, Mining, Wallets | Blocks, Transactions, Mining | Blocks, Transactions, Mining, Smart Contracts, Privacy |
| **Extended Features** | File Storage, CLI Interaction | None | Smart Contracts, Private Transactions, P2P Network |
| **Performance Optimization** | Moderate | High | High |
| **Code Complexity** | Medium (with detailed comments) | Low | High |

---

## Project Structure

### B1 (Educational)
```
src/
├── block.rs          # Block core structure (with full comments)
├── blockchain.rs     # Blockchain management (with file storage)
├── cli.rs            # Command line interface
├── merkle_tree.rs    # Complete Merkle tree implementation
├── node.rs           # Simple node networking functionality
├── pow.rs            # Proof of work module
├── transaction.rs    # Transaction system (with wallet integration)
├── utils.rs          # Utility toolkit
├── wallet.rs         # Independent wallet module
└── main.rs           # Command line main program entry
```

### B2 (Core)
```
src/
├── block.rs          # Streamlined block structure (redundant fields removed)
├── blockchain.rs     # Blockchain core logic (file storage removed)
├── merkle_tree.rs    # Optimized Merkle tree implementation
├── transaction.rs    # Basic transaction verification
├── node.rs           # Simple node networking functionality
└── main.rs           # Direct run example
```

### B3 (Extended)
```
src/
├── block.rs          # Block core structure
├── blockchain.rs     # Blockchain management
├── transaction.rs    # Transaction system
├── merkle_tree.rs    # Merkle tree implementation
├── node.rs           # P2P network node
├── cli.rs            # Command line interface
├── wallet.rs         # Wallet management
├── smart_contract.rs # Smart contract support
├── privacy.rs        # Private transaction implementation
├── pow.rs            # Proof of work module
├── utils.rs          # Utility toolkit
└── main.rs           # Main program entry
```

---

## Core Features

### 1. Blocks and Blockchain
- **Block**: Includes index, timestamp, transaction list, hash value, etc.
- **Blockchain**: Manages the chain structure of blocks, supports genesis block, adding new blocks, verifying chain integrity.
- **Merkle Tree**: Used for efficient verification of transaction data integrity.

### 2. Transactions and Wallet
- **Transaction**: Supports sender, receiver, amount, and signature verification.
- **Wallet**: Generates key pairs, signs data, verifies signatures.

### 3. Proof of Work (PoW)
- Adjusts nonce value to make block hash meet specific conditions (prefix contains specified number of 0s).
- Configurable difficulty controls mining complexity.

### 4. Smart Contracts (B3 Exclusive)
- Supports deployment and execution of simple smart contracts.
- Contract state stored in the blockchain.

### 5. Private Transactions (B3 Exclusive)
- Uses Zero-Knowledge Proofs (ZKP) to protect transaction privacy.
- Supports creating and verifying private transactions.

### 6. P2P Network (B3 Exclusive)
- Implements blockchain synchronization between nodes.
- Supports peer node discovery and connection.

---

## Usage Guide

### Installation and Running
```bash
# Clone repository
git clone <repository>
cd 

# Compile project
cargo build --release

# Run B1 version
cargo run --bin b1

# Run B2 version
cargo run --bin b2

# Run B3 version
cargo run --bin b3
```

### Command Line Tools (B1/B3)
```bash
# Create wallet
cargo run --bin b1 -- create-wallet

# Initiate transaction
cargo run --bin b1 -- add-transaction --sender <sender address> --receiver <receiver address> --amount <amount>

# Mining
cargo run --bin b1 -- mine-block --miner <miner address>

# Deploy smart contract (B3)
cargo run --bin b3 -- deploy-contract --code <contract code>

# Create private transaction (B3)
cargo run --bin b3 -- create-privacy-transaction --amount <amount>
```

## Extended Development
## Some B3 extension feature code has not been fully uploaded to the repository, see documentation to complete and resolve on your own. Below are some hints for completing certain extension features

### 1. Smart Contracts
The current `smart_contract.rs` implements basic contract functionality, but the following parts need to be completed:
- **Contract Language Support**: Extend support for Solidity or other advanced contract languages.
- **Gas Mechanism**: Introduce a Gas fee mechanism for contract execution.
- **Event Logs**: Add contract event logging functionality.

Example code:
```rust
// Extending Gas mechanism
pub struct GasCounter {
    gas_limit: u64,
    gas_used: u64,
}

impl GasCounter {
    pub fn new(gas_limit: u64) -> Self {
        GasCounter { gas_limit, gas_used: 0 }
    }

    pub fn charge(&mut self, amount: u64) -> Result<(), String> {
        self.gas_used += amount;
        if self.gas_used > self.gas_limit {
            Err("Out of gas".to_string())
        } else {
            Ok(())
        }
    }
}
```

### 2. Private Transactions
The current `privacy.rs` implements basic Zero-Knowledge Proof (ZKP) functionality, but the following parts need to be completed:
- **Performance Optimization**: Optimize ZKP generation and verification performance.
- **Range Proofs**: Support range proofs for amounts.
- **Batch Verification**: Support batch verification of private transactions.

Example code:
```rust
// Extending range proofs
pub struct RangeProof {
    // Implement range proof logic
}

impl RangeProof {
    pub fn new(amount: u64) -> Self {
        // Initialize range proof
    }

    pub fn verify(&self) -> bool {
        // Verify range proof
    }
}
```

### 3. P2P Network
The current `node.rs` implements basic node functionality, but the following parts need to be completed:
- **Node Discovery**: Implement Kademlia DHT node discovery protocol.
- **Message Protocol**: Define standardized network message protocols.
- **Sharding Support**: Support blockchain sharding technology.

### 4. Token Issuance
*See the **project documentation** to improve and supplement on your own. This project does not provide complete token issuance code*

Example code:
```rust
// Extending node discovery
pub struct NodeDiscovery {
    // Implement node discovery logic
}

impl NodeDiscovery {
    pub fn new() -> Self {
        // Initialize node discovery
    }

    pub fn discover_peers(&self) -> Vec<SocketAddr> {
        // Discover peer nodes
    }
}
```

### B1 Extension Suggestions
- Add more detailed logs and debugging information.
- Implement cross-chain functionality.

### B2 Optimization Directions
- Use more efficient hash algorithms (such as Blake3).
- Optimize memory pool management.

### B3 Advanced Features
- Token issuance
- Support for more complex smart contract languages (like Solidity).
- Enhance performance of private transactions.
- Cross-chain
- Distributed network
- Other extension features to be improved

---

## Detailed Documentation

- **B1 Detailed Documentation**: Please go to [B1/readme.md](B1/readme.md) to view.
- **B2 Detailed Documentation**: Please go to [B2/readme.md](B2/readme.md) to view.
- **B3 Detailed Documentation**: Please go to [B3/readme.md](B3/readme.md) to view.

Project actual demonstration screenshots can be found in the product description PDF.

---

## License

This project is licensed under the MIT License. Please refer to the [LICENSE](LICENSE) file for details.

---

By integrating B1, B2, and B3, developers can choose the appropriate version for development and learning based on their needs. B1 is suitable for beginners, B2 is suitable for rapid prototype development, and B3 is suitable for advanced application scenarios.
