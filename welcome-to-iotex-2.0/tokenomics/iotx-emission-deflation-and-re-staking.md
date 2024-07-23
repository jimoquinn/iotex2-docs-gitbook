# IOTX Emission, Deflation, and Re-Staking

In addition to the utility for IOTX token above, there are also new designs for IoTeX 2.0 regarding how IOTX tokens will be burned based on infrastructure usage, how IOTX will be shared with Dapps and builders via incentives programs, and how new IOTX will be emitted to stakers going forward.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcbaVZkuxbIVCx4eAaQd3VttUPRLbPuVdttCE4Sf8DEts9FRlpWr5cOTOsNNmWH4cMdBiF5Uf2VnHGUFF-92nmXBOwgprTQu5ZhFXr14iQJdLpf70-7Mm2W6bPPiSx07y1sNLwXDx3nST6w7NhYA_cPosw?key=xRhwvsy-gk4_S1iqjhFKlQ" alt=""><figcaption></figcaption></figure>

## Inflationary Staking Rewards

{% hint style="info" %}
Inflationary staking rewards are defined as new IOTX added to the token supply, delivered to Delegates that participate in consensus and token-holders that stake IOTX.
{% endhint %}

When the IoTeX Mainnet launched in 2019, 12% of the total IOTX supply (1.2 billion IOTX) was allocated for staking rewards to Delegates. Token-holders stake IOTX to vote for Delegates who share a portion of the staking rewards with their voters. Since then, approximately 200 million IOTX per year has been distributed as block and epoch rewards to Delegates and voters. Block rewards were given to the Top 36 Consensus Delegates for each new block produced, while epoch rewards were distributed proportionally among the Top 100 Delegates every hour.

After more than four years of Mainnet operation, the initial IOTX allocation for staking rewards is nearly exhausted. To continue incentivizing Delegates to validate transactions and secure the network, IoTeX 2.0 will introduce inflationary staking rewards. These rewards involve minting new IOTX tokens, which are distributed to Delegates and stakers participating in network consensus.

Inflationary staking rewards will maintain the existing distribution structure, with block rewards for block-producing Delegates and epoch rewards for the Top 100 Delegates. This approach ensures a higher staking ratio and enhanced security for the IoTeX network. The specific annual inflation rate will be determined by network-wide governance, aiming for mild inflation that offers competitive staking rewards APRs, while considering deflationary token burning to maintain a stable token supply.

This concept aligns with practices of other Layer 1 blockchains, such as Ethereum, Solana, and Cosmos. For instance, Solana started with an 8% inflation rate, reducing annually by 15%, reaching about 5.5% in early 2024. IoTeX 2.0 aims to introduce a balanced inflationary mechanism that supports network growth and security, detailed further in the following sections.

## Deflationary Burning

To maintain a stable token supply, IoTeX 2.0 introduces deflationary burning of tokens based on network usage, similar to the Burn and Mint Equilibrium model. For instance, Ethereum balances the issuance of new ETH with the deflationary burning of gas fees (EIP-1559) to achieve a stable or deflationary token supply. Since 2020, IoTeX has implemented the Burn-Drop program, resulting in approximately 4% (400M IOTX) of the total supply being burned based on new device registrations.

With IoTeX 2.0, new deflationary mechanisms will be introduced at the protocol level:

* **Gas Fee Burning**: Similar to Ethereum's EIP-1559, gas fees will be burned to incentivize and redistribute value to IOTX token-holders as network usage increases.
* **ioID**: Creating new on-chain identities for devices will require burning IOTX, with the burn rate dynamic based on the total number of registered devices. Additionally, obtaining Verifiable Credentials (VCs) for DIDs will involve burning IOTX, linking device identities to the IoTeX L1 and DIMs like W3bstream.
* **Modular Products**: The adoption of modular products like W3bstream, ioConnect, and ioDDK by Dapps and companies will drive deflationary burning of IOTX due to device interactions. Periodic token burns based on community-defined adoption thresholds may also be implemented.

IoTeX 2.0 tokenomics aim to reward increased usage of the platform's modular components through deflationary burning, initially counterbalancing inflationary staking rewards to maintain a stable token supply. As the platform achieves mass adoption, the IOTX token supply could become net deflationary. To support this growth, IoTeX 2.0 will allocate IOTX tokens to various builders through growth incentive programs.

## Growth Incentives

An important pillar of IoTeX 2.0 is [The Marshall DAO (IIP-23)](https://community.iotex.io/t/iip-23-the-marshall-dao/11172), a Decentralized Autonomous Organization (DAO) that will enable IoTeX stakeholders to make proposals regarding how to allocate IOTX incentives to grow the IoTeX ecosystem, including onboarding reputable DePIN projects and funding network-wide initiatives. This creates a transparent and meritocratic system where the best ideas are funded using IOTX. The Marshall DAO will initially be funded by more than 500M IOTX that was repurposed from the Burn-Drop allocation, which was decided by the IoTeX community via a network-wide vote in Q1 2024. In the future, additional funding for the Marshall DAO may be added via further network-wide votes to add newly minted IOTX to the pool.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdf8fSGLwRecqY4Gjm5lv2mJBmXyBPCahOiN1vaBfztB3wt0kRhZuxEXFYLWGR9kqyRIJeRLO_yzAd5bCLYE_PDiFMZ5ih_Lh95fRTaE7LMN3XIk3kbov4NpywdBfjR3j-cZru28-PRf29ejcj_hiBthIRI?key=xRhwvsy-gk4_S1iqjhFKlQ" alt=""><figcaption><p>Marshal DAO</p></figcaption></figure>

The Marshall DAO employs a vote-escrow on-chain governance model, which means the more IOTX is staked in the DAO the more voting power a user has. This ensures decisions to fund projects and initiatives are made by those who are most invested in the long-term success of IoTeX. Token-holders that stake for at least 91 days will earn veIOTX, a non-transferrable on-chain token, which can be used to propose and vote on funding allocations via gauges that represent specific proposals. This means long-term stakers can vote using their veIOTX to shape how IOTX from the DAO funds various projects, including but not limited to boosting liquidity for DEX trading pairs on IoTeX, sponsoring early-stage DePIN projects via launchpads, accelerating DePIN projects via dual-mining, issuing grants for public goods and network-wide tools, and more.

