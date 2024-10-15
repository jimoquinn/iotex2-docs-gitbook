# Account Cryptography

IoTeX uses cryptographic techniques to secure its accounts and ensure the integrity and authenticity of transactions. Specifically, IoTeX account generation and digital signature are based on the same cryptographic schemes as Ethereum.

## Overview

Here are the key components of IoTeX's account cryptography:

1. **Elliptic Curve Digital Signature Algorithm (ECDSA):**
   * **Private Key:** IoTeX accounts are secured using private keys, which are 256-bit random numbers. The private key is known only to the account owner and is used to sign transactions.
   * **Public Key:** The public key is derived from the private key using the secp256k1 elliptic curve. The public key is then used to generate the IoTeX address, which can be both in the format of an Ethereum address (starting with "0x...") or a native IoTeX address (starting with "io1...").
2.  **IoTeX Address:**

    * The IoTeX address can be generated like an Ethereum address, derived from the public key by taking the last 20 bytes of the Keccak-256 hash of the public key. This address is a unique identifier for the account on the IoTeX network.

    [-> Learn here how to construct the IoTeX address in native format](account-cryptography.md#address-construction)
3. **Keccak-256 Hash Function:**
   * IoTeX uses the Keccak-256 cryptographic hash function (often referred to as SHA-3) for various purposes, including generating addresses from public keys and ensuring data integrity.
4. **Digital Signatures:**
   * Transactions in IoTeX are signed with the account's private key using ECDSA. The digital signature ensures that the transaction was created by the account owner and has not been altered. Nodes in the network can verify the signature using the corresponding public key.
5. **Nonce:**
   * Each account has a nonce, which is a counter that keeps track of the number of transactions sent from the account. The nonce prevents replay attacks by ensuring that each transaction can only be processed once.
6. **Account Encryption:**
   * While not a part of the core protocol, encryption is often used to protect private keys. Wallets and other storage solutions typically encrypt private keys to prevent unauthorized access.
7. **Secure Key Storage:**
   * Hardware wallets and other secure storage solutions use additional cryptographic techniques to protect private keys from being compromised.

## Private Key <a href="#private-key" id="private-key"></a>

In IoTeX, the account Private Key is generated as 64 random hex characters, e.g.:

```
90bf89cd944df5c6d8281b132783277c1760537809c534fc54dda34c4edfb4f4
```

and the corresponding **Public Key** is derived from the private key using ECDSA with the secp256k1 curve, which is the same as Ethereum.

Given a signed message, you can recover the public key of the signing account using [Ecrecover](https://github.com/ethereum/go-ethereum/blob/master/crypto/signature\_cgo.go#L36), also defined in [solidity](https://docs.soliditylang.org/en/latest/solidity-by-example.html?highlight=ecrecover#recovering-the-message-signer-in-solidity) for signature verification in smart contracts.

## Native Address Construction <a href="#address-construction" id="address-construction"></a>

An IoTeX native representation of an account address looks like:

```
io1nyjs526mnqcsx4twa7nptkg08eclsw5c2dywp4
```

and it can be constructed starting from the private key using the following steps:

**1. Generate a random private key as 64 random hex characters**

```
privKey =
0700898c9dcae0279c88318003ee210e1ee2514121d292d2f03739498ce95f4e
```

**2. Calculate the corresponding public key using secp256k1 elliptic curve**

```
pubKey := keccak256k1(privKey) = 046748ee7f4b573f1fb17517005499003385da75788b2052b18bbb05fd0dcf50597ffc54a22a02ca7343ed2654212022c1f4a0c3755dbdb81a2e70c7c0805520dc
```

**3. Apply `keccak256` hash function to the public key, excluding the first byte:**

```
hash := keccak256(pubKey[1:]) = 42a1c0796606183ccdb3d935147e805c858840099190e208d7a04a74f2a0aac8
```

**4. Take the last 20 bytes of the hash**

```
payload := hash[12:] = 147e805c858840099190e208d7a04a74f2a0aac8
```

which is the "byte representation" of the address

**5. Convert the byte representation to 5-bit encoding (base32):**

```
2, 17, 31, 8, 0, 23, 4, 5, 17, 1, 0, 0, 19, 4, 12, 16, 28, 8, 4, 13, 15, 8, 2, 10, 14, 19, 25, 10, 1, 10, 22, 8
```

{% hint style="info" %}
See a go lang implementation for the [5-bit conversion](https://github.com/iotexproject/iotex-address/blob/b07b71fc7866257680b75f1ab9c79c95dc6d255b/address/bech32/bech32.go#L141) implementation or a [nodejs](https://www.npmjs.com/package/bech32) package (use `toWords()` to convert a bytes array into 5-bit words).
{% endhint %}

**6. Apply the** [**bech32** ](https://github.com/bitcoin/bips/blob/master/bip-0173.mediawiki)**encoding on the 5-bit payload with the `io` prefix to obtain the address:**

```
address := io1bc1qz3lgqhy93pqqnyvsugyd0gz2wne2p2kght0g4r
```

{% hint style="info" %}
See a go lang implementation for the [bech32 encoding](https://github.com/iotexproject/iotex-address/blob/b07b71fc7866257680b75f1ab9c79c95dc6d255b/address/bech32/bech32.go#L97) implementation or a [nodejs](https://www.npmjs.com/package/bech32) package (use `encode` to encode 5-bit words with a prefix).
{% endhint %}

## Address Conversion Examples

Developers can refer to the iotex-antenna SDK source code to learn how IoTeX native addresses are created and converted between 0x and io1 formats. Below you can also find two short examples:

### Convert from `io1` to `0x` format

```javascript
const { bech32 } = require('bech32');

// Function to decode IoTeX address to Ethereum address
const ioToEthAddress = (ioAddress) => {
  // Step 1: Decode the Bech32 IoTeX address
  const decoded = bech32.decode(ioAddress);
  
  // Step 2: Convert 5-bit words back to bytes
  const words = bech32.fromWords(decoded.words);

  // Step 3: Slice the last 20 bytes (Ethereum address is 20 bytes)
  const ethAddressBytes = Buffer.from(words).slice(-20);

  // Step 4: Convert to Ethereum-style hex address
  const ethAddress = ethAddressBytes.toString('hex');
  return `0x${ethAddress}`;
};

// Test the function
const ioAddress = 'io12etkzmykk4mnavvqjgcrprnzhq8zxahqr698nl'; // Replace with IoTeX address
console.log(`Ethereum Address: ${ioToEthAddress(ioAddress)}`);
```

### Convert from `0x` to `io1` format

```javascript
const { bech32 } = require('bech32');

// Function to convert Ethereum address to IoTeX address
const ethToIoAddress = (ethAddress) => {
  // Step 1: Remove the '0x' prefix and convert the hex string to a byte array
  const ethAddressBytes = Buffer.from(ethAddress.slice(2), 'hex');

  // Step 2: Convert the byte array into 5-bit words for Bech32 encoding
  const words = bech32.toWords(ethAddressBytes);

  // Step 3: Encode the words into a Bech32 IoTeX address with the 'io' prefix
  const ioAddress = bech32.encode('io', words);
  return ioAddress;
};

// Test the function
const ethAddress = '0x5657616c96b5773eb1809230308e62b80e2376e0'; // Replace with your Ethereum address
console.log(`IoTeX Address: ${ethToIoAddress(ethAddress)}`);
```

