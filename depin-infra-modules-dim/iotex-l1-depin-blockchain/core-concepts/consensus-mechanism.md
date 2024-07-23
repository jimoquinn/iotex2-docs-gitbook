# Consensus Mechanism

## Randomized Delegated Proof of Stake (Roll-DPoS)

To have a fast and efficient consensus mechanism with instant block finality in the context of DePIN, the IoTeX blockchain combines the concepts of Delegated Proof of Stake (DPoS), Proctical Bizantine Fault Tolerance (PBFT) and Verifiable Random Functions (VRFs). VRF is a family of functions that can produce publicly verifiable proofs for the correctness of their random outputs. At a high level, our Roll-DPOS has four phases elect candidates, form committee, propose block and finalize block.

<figure><img src="../../../.gitbook/assets/image (97).png" alt="" width="375"><figcaption><p>Randomized Delegated Proof of Stake (Roll-DPoS)</p></figcaption></figure>

### Elect Candidates

All nodes in the IoTeX network participate this phase in terms of voting for the committee candidates. To encourage nodes to vote, the system makes sure the delegates share forged rewards with their voters. The candidates forms a set of at least 36 delegates; this number will increase in the future to further avoid the centralization of the mining power. Once the candidates are selected, they will be  fixed in one epoch, which consists of 30 iterations.&#x20;

### Form Committee&#x20;

In each iteration, a random committee of size 24 is selected from the candidate pool using VRF for creating blocks in the next 30 rounds. The use of VRF is important as it provides a non-interactive way to sort all delegates for proposing blocks in a fairness and security way. To this end, we use the efficient VRF as being used in Algorand.

### Propose Block

In each round (which is roughly every 5 seconds), every committee node proposes a new block and broadcasts it to the network, together with the the proof. Only the block proposed by the expected committee node and has not been proposed in the same iteration is considered by other nodes, which is called a candidate block.&#x20;

### Finalize Block

In the same round, all other nodes use PBFT to vote for/against the candidate block. If more than 2/3 committee nodes agree on candidate block's validness, it is finalized and is appended to the blockchain by everyone in the network. After that, "propose block" and "finalize block" are executed in the next round; if the current iteration finishes, another random committee will be formed before propose block and finalize block are executed again.
