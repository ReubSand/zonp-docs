# Zonp — Wallet-Native Private Commerce on Zcash

Zonp is a wallet-native commerce system built on Zcash that transforms private payments into fully private economic interactions.

It enables buyers and sellers to exchange structured commerce data—orders, invoices, receipts, and messages—directly through Zcash shielded transactions, without exposing any metadata to the public blockchain.

---

## What Zonp Does

Zonp extends Zcash from:
- **Private payments** → to → **Private commerce**

Using the Zcash memo field as a structured data channel, Zonp supports:

- Itemized orders (cart, quantities, pricing)
- Encrypted buyer ↔ seller messaging
- Receipts and transaction records
- IPFS-hosted storefronts
- Transaction-backed reputation system

All of this occurs **without revealing**:
- Who transacted  
- What was purchased  
- How much was paid  

---

## Key Concepts

### Privacy (Default, Not Optional)
All commerce data is:
- Encrypted at the application layer (X25519 + AES-256-GCM)
- Encrypted again by Zcash shielded transactions

No third party—including blockchain observers—can access transaction details.

---

### Identity (Without Personal Information)
Zonp uses:
- **ed25519 signing keys** for identity
- **TOFU (Trust-on-First-Use)** binding for peer relationships

Users prove authorship of actions without revealing real-world identity.

---

### Trust (Backed by Real Transactions)
Reputation is tied to:
- Verified on-chain transactions
- Signed wallet identity

Fake reviews are prevented by requiring cryptographic proof of purchase.

---

## System Overview

Zonp operates as a layered protocol:

1. **Zcash Layer**
   - Shielded transactions (Pallas curve)
   - Hides sender, receiver, and amount

2. **Zonp Protocol Layer**
   - Binary TLV memo encoding
   - Compression and chunking (ZB3 / ZB3C)
   - X25519 ECDH + AES-256-GCM encryption

3. **Application Layer**
   - Mobile wallet (React Native)
   - Kotlin bridge to Zcash SDK
   - Node.js / PostgreSQL backend
   - IPFS storefront hosting

---

## Repository Contents

This repository contains supporting documentation for the Zonp system:

### 1. Architecture Flowchart
End-to-end cryptographic architecture:
- Key derivation (BIP-39 → ed25519 / X25519 / spending key)
- Encryption pipeline
- Signed server authentication
- Identity propagation and TOFU binding

### 2. Memo Protocol
Detailed specification of:
- Binary TLV encoding
- Tokenization and compression
- Dual-layer encryption
- Identity propagation inside memos

### 3. Transaction Flow
Full lifecycle of a transaction:
- Order creation
- Encoding and encryption
- On-chain broadcast
- Decryption and order ingestion

### 4. Simplified Overview
Non-technical explanation of:
- How purchases work
- What data remains private
- How identity and trust function

### 5. Project Roadmap
Current status and future development:
- Completed core system (validated on mainnet)
- Sealed Sender upgrade (in progress)
- Rust core refactor
- Security audit and merchant onboarding

---

## Current Status

Zonp is a **working system**, not a concept.

Implemented and validated on Zcash mainnet:
- Structured memo protocol
- Dual-layer encryption
- Encrypted messaging
- IPFS storefronts
- Transaction-verified reputation

---

## Next Steps

### Phase 2 — Protocol & Security Upgrade
- Add memo-level ed25519 signatures
- Eliminate TOFU race conditions
- Transition to full cryptographic verification

### Rust Core Refactor
- Port critical protocol components to Rust
- Improve determinism, safety, and auditability
- Compile to WASM for cross-platform use

### Phase 3 — Security Audit
- Independent review of cryptographic stack
- Threat modeling and infrastructure audit

---

## Vision

Zonp evolves Zcash into:

> A private economic operating system

Long-term goals:
- Protocol standardization across wallets
- Privacy-preserving commerce discovery
- Multi-party and programmable transactions
- Zero-knowledge identity and reputation systems

---

## Why Zonp Matters

Zcash enables private money.

Zonp enables:
- Private trade  
- Private coordination  
- Private economic activity  

Without exposing users to surveillance or intermediaries.

---

## License / Status

This repository contains documentation and architecture materials supporting an active development project.

For inquiries or collaboration, refer to the project submission context (e.g., Zcash Community Grants).

---
