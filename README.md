# Decentralized Identity Verification System

A full-stack secure identity verification system built on blockchain technology that prioritizes privacy and security through hash-based identity management.

## 🌟 Features

- **Privacy-First Design**: Users submit hashed versions of identity data instead of raw personal information
- **Trusted Verification Network**: Authorized verifiers authenticate and validate user identities
- **Immutable Records**: Smart contracts maintain tamper-proof verification statuses on blockchain
- **Gas Optimized**: Efficient storage layout and minimal state updates for cost-effective operations
- **Security Focused**: OpenZeppelin-based access control with comprehensive input validation

## 🏗️ Project Structure

```
project/
├── client/          # React Frontend Application
├── backend/         # Express.js Backend Server
├── contracts/       # Smart Contracts for Identity Management
├── migrations/      # Truffle Migration Files
├── test/           # Test Files
└── node_modules/   # Project Dependencies
```

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **React.js** | Frontend user interface |
| **Express.js** | Backend API server |
| **Solidity** | Smart contract development |
| **Truffle** | Smart contract deployment and testing |
| **Ganache** | Local Ethereum blockchain simulation |
| **Web3.js** | Blockchain connectivity |
| **MetaMask** | Wallet integration |
| **MongoDB** | Off-chain data storage |
| **OpenZeppelin** | Security and access control |

## 📋 Prerequisites

Before running this project, ensure you have:

- [Node.js](https://nodejs.org/) (v14 or higher)
- [MetaMask Browser Extension](https://metamask.io/)
- [Truffle Suite](https://trufflesuite.com/truffle/)
- [Ganache](https://trufflesuite.com/ganache/)
- [MongoDB](https://www.mongodb.com/)

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone "https://github.com/keshav-singhal04/Decentralized-Identity-Verification"
cd project
```

### 2. Install Dependencies
```bash
# Install root dependencies
npm install

# Install frontend dependencies
cd client
npm install
cd ..

# Install backend dependencies
cd backend
npm install
cd ..
```

### 3. Setup Ganache
1. Install and launch Ganache
2. Create a new workspace with these settings:
   - **Network ID**: 5777
   - **RPC Server**: HTTP://127.0.0.1:7545
   - **Chain ID**: 1337
3. Save and start the workspace
4. Note the first account's private key for development

### 4. Configure MetaMask
1. Install MetaMask browser extension
2. Add custom network:
   - **Network Name**: Ganache
   - **RPC URL**: HTTP://127.0.0.1:7545
   - **Chain ID**: 1337
   - **Currency Symbol**: ETH
3. Import account using private key from Ganache

### 5. Environment Configuration
Create a `.env` file in the root directory:
```env
MONGODB_URI=your_mongodb_connection_string
PRIVATE_KEY=your_ganache_private_key
```

### 6. Start the Application

**Terminal 1 - Backend Server:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Smart Contract Deployment:**
```bash
truffle compile
truffle migrate
```

**Terminal 3 - Frontend Application:**
```bash
cd client
npm start
```

### 7. Connect MetaMask
- Click MetaMask extension and connect to your Ganache account
- The first account automatically becomes admin (contract deployer)
- For regular user access, import other Ganache account private keys

## 🔧 Core Functionality

### Identity Registration
- Users register hashed identity (`bytes32 identityHash`)
- Prevents duplicate registrations
- Emits `IdentityRegistered` event for auditability

### Verifier Management
- **Owner Controls**: Add/remove authorized verifiers
- **Access Control**: `onlyOwner` and `onlyVerifier` modifiers
- **Verification Process**: Authorized verifiers validate identities

### Identity Lifecycle
1. **Registration**: User submits identity hash
2. **Verification**: Verifier confirms and validates identity
3. **Revocation**: If needed, verifier can revoke with reason and timestamp

### Status Querying
- Public `checkIdentity` function returns:
  - Registration status
  - Verification status
  - Revocation details (timestamp and reason)

## ⚡ Gas Optimization

### Storage Efficiency
- **Compact Layout**: Uses `bytes32` for identity hashes instead of strings
- **Struct Packing**: Optimized field arrangement for reduced storage slots
- **Minimal Updates**: Functions only modify necessary state variables

### Event-Driven Architecture
- **Off-chain Indexing**: Events enable efficient data querying
- **Reduced Storage**: Critical information stored in events rather than state
- **Gas Savings**: Event logging costs less than storage operations

### Algorithmic Efficiency
- **O(1) Lookups**: Direct mapping access for verifiers and identities
- **Chain ID Optimization**: Uses `block.chainid` to avoid external calls

## 🔐 Security Features

### Access Control
- **OpenZeppelin Ownable**: Proven access control patterns
- **Multi-level Permissions**: Owner and verifier role separation
- **State Guards**: Prevents invalid state transitions

### Input Validation
- **Zero-value Protection**: Rejects empty identity hashes
- **State Verification**: `notRegistered` and `notRevoked` modifiers
- **Duplicate Prevention**: Ensures unique identity registration

### Privacy Protection
- **Hash-only Storage**: Raw personal data never touches blockchain
- **Fixed-salt Hashing**: Consistent hashing with preimage attack resistance
- **Off-chain Data**: Sensitive information stored securely off-chain

## 📊 Smart Contract Events

```solidity
event IdentityRegistered(bytes32 indexed identityHash, address indexed user);
event IdentityVerified(bytes32 indexed identityHash, address indexed verifier);
event IdentityRevoked(bytes32 indexed identityHash, address indexed verifier, string reason);
event VerifierAdded(address indexed verifier);
event VerifierRemoved(address indexed verifier);
```

## 🧪 Testing

Run the test suite:
```bash
truffle test
```

## 📱 Usage

1. **Admin Dashboard**: Manage verifiers and system settings
2. **User Registration**: Submit identity hash for verification
3. **Verifier Portal**: Validate and manage identity statuses
4. **Status Checking**: Query identity verification states

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [Repository](https://github.com/keshav-singhal04/Decentralized-Identity-Verification)
- [Truffle Documentation](https://trufflesuite.com/docs/)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/)
- [Web3.js Documentation](https://web3js.readthedocs.io/)

## 📞 Support

If you encounter any issues or have questions, please open an issue in the GitHub repository.

---

**Built with ❤️ for secure and decentralized identity management**
