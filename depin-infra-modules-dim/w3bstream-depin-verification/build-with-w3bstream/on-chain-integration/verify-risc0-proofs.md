# Verify Risc0 Proofs

## **Risc Zero Verifier Contract**

If your W3bstream project generates Risc Zero proofs, you can verify it by calling the IoTeX pre-deployed verifier contract for Risc Zero.

<table><thead><tr><th width="122">Network</th><th width="434">Verifier Contract</th><th>Source Code</th></tr></thead><tbody><tr><td><strong>Testnet</strong></td><td>0xD6c51c8Fb86F8e7b051AB52B3EEDd70467378016</td><td><a href="https://github.com/machinefi/sprout/blob/develop/examples/risc0-circuit/contract/RiscZeroGroth16Verifier.sol#L139">-> Link to GitHub</a></td></tr><tr><td><strong>Mainnet</strong></td><td>N/A</td><td>N/A</td></tr></tbody></table>

### Example Receiver Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;
import { RiscZeroGroth16Verifier } from "./Risc0Groth16Verifier.sol";

contract DePINContract {
    RiscZeroGroth16Verifier private verifier;

    event ProofVerified();

    constructor(address _verifierAddress) {
        verifier = RiscZeroGroth16Verifier(_verifierAddress);
    }

    function submitRisc0Proof(
        bytes calldata seal,
        bytes32 imageId,
        bytes32 postStateDigest,
        bytes memory journal
    ) external {
        require(verifier.verifySnark(seal, imageId, postStateDigest, journal), "Proof verification failed.");
        emit ProofVerified();
        
        // Process the Journal and run your toke economy here
    }
}
```
