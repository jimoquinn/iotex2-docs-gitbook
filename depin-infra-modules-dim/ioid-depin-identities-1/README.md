---
hidden: true
---

# \[ioID] DePIN Identities - Initial Draft

## Introduction

**ioID** is a decentralized identity infrastructure designed for the machine economy. It provides globally unique, metadata-rich identifiers, programmable multi-chain wallets, and secure messaging for physical devices, enabling interoperability, financial automation, and data verifiability across ecosystems like DePIN, AI, and IoT.

## Core Concepts

### ioID&#x20;

A decentralized identity (DID) assigned to a physical machine.&#x20;

Format: `did:io:<identifier>`

### **DID Document (DID Doc)**

Metadata JSON stored somewhere (e.g., on IPFS) with keys, geolocation, ownership, and access policies.

### **Machine-Bound Account (MBA)**

An ERC-6551-inspired smart wallet linked to each ioID-enabled device for on-chain actions.

### **Device NFT**

ERC-721 token representing ownership and linking to ioID/MBA.

## **Services Enabled by ioID**

* Incentives Distribution on-chain
* Token Staking
* Proof-of-Liveness
* Device Financing & Lending
* Device Discovery via depinscan.io

## Use Cases

* Autonomous drones earning tokens via their MBA
* Weather stations reporting data + staking
* AI agents verifying data origin
* Community-owned edge devices sharing rewards
