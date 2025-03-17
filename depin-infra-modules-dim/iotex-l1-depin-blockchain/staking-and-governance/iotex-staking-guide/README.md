# IoTeX Staking Guide

## **Configure a Wallet**

To begin staking IOTX, you will need a compatible wallet. Use ioPay if you prefer to manage your stakes on a mobile phone, or MetaMask for managing your stake from a desktop.

[→ Learn how to configure Metamask and ioPay Wallets](../../wallets/)

## **Acquire IOTX Tokens**

To start, purchase IOTX tokens from a cryptocurrency exchange. Then, transfer them to your chosen wallet. For detailed guidance on funding your wallet, follow this link:

[Learn how to fund your wallet ->](broken-reference)

## **IoTeX Staking Portal**

This can be done directly through the ioPay app's in-built browser or via a Metamask-enabled web browser. Once you reach the staking portal, you will be prompted to choose between two staking methods: 'Native Staking' or 'Stake as NFT'.

[Access the Staking Portal ->](https://stake.iotex.io/stake)

In the first screen of the Staking process, you can browse the list of IoTeX Validators and choose one to delegate your IOTX tokens to. At any time you will be able to redirect your votes to a different delegate without the need to unstake your IOTX.

[Go to the Native Staking Guide ->](native-staking.md)

[Got to the Staking as NFT Guide ->](staking-as-nft.md)

## Choose a Delegate

Delegates all have unique reward plans to cover costs, donate to funds, and re-distribute rewards to their voters. Think of it as Delegates charging a service fee to stake your token.&#x20;

Create a diverse voting portfolio that is representative of your vision for the future of IoTeX.&#x20;

* **Community:** If you want IoTeX to prioritize community, vote for an IoTeX Ambassador!&#x20;
* **DApps:** If you want to prioritize dApp development, vote for a Dev Group!
* **Enterprise**: If you want enterprise to be a priority, vote for a delegate founded by an investor.

{% hint style="info" %}
The difference in rewards across Delegates is marginal (i.e., 80% vs. 85%), but the difference in potential impact can be large – **vote for multiple delegates, and** **vote for the benefit of IoTeX**!
{% endhint %}

<details>

<summary>About Native Staking</summary>

.

</details>

<details>

<summary>About Staking as NFT</summary>

Staking as NFT introduces Non-Fungible Tokens (NFTs) to represent your staking deposits. In this mechanism, when you stake your tokens, you receive an NFT that signifies ownership and details of the staked amount and lock options.

#### Why Choose Staking as NFT?

Staking as NFT enables participation in Liquid Staking or other DeFi applications and unlocks the potential to earn additional passive income. Furthermore, you have the option to liquidate your stake in an [NFT marketplace](https://nft.mimo.exchange/) if you prefer not to wait for the lock period to conclude.

Opt for this option when your staking deposit aligns with one of the fixed amounts of 10k, 100k, or 1M IOTX, and you are willing to lock your deposit for at least 91 days.

</details>

<figure><img src="../../../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

## **Decide the amount of IOTX**

When selecting the amount of IOTX to stake, consider your investment goals and risk tolerance. Here are a few tips:&#x20;

* **Minimum Stake**: Ensure you stake at least 100 IOTX, as this is the minimum requirement.
* **Transaction Fees**: Do not try to stake your entire balance: leave some IOTX in your wallet for transaction fees.

### **Understand the Staking Duration (Lock-up Period)**

The staking duration setting allows you to specify how long you wish to lock your IOTX tokens for staking. Here are some key points to consider when selecting a duration:

1. **Short-term vs Long-term**: Shorter durations provide more flexibility but typically offer lower rewards. Longer durations can offer higher rewards but keep in mind that the extra rewards decrease exponentially so it many not be worth locking for very long periods.
2. **91-day period**: 91 day is a special threshold for the staking duration: when [StakeLock](./#understand-stake-lock) is also enabled, it entitles you to the Burn-Drop rewards that come from DePIN devices registered on the IoTeX blockchain.
3. **Unstaking**: Once the staking period ends (if [StakeLock is not enabled](./#understand-stake-lock)), your tokens become unlocked. At this point, your tokens remain staked but will no longer earn additional staking rewards because they are no longer locked. You now have the option to unstake, renew your staking period by locking the tokens again, or leave your tokens staked without locking.
4. **Goal Alignment**: Choose a duration that aligns with your investment goals and liquidity needs.

<figure><img src="../../../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

### **Understand Stake-Lock**

StakeLock is a feature that, when enabled, prevents the countdown of your staking duration from progressing. This means that your IOTX tokens remain locked for the specified duration, and the lock period does not decrease until you disable StakeLock. Once disabled, the countdown will begin, and you'll need to wait for the lock period to expire before you can unstake your tokens. It's useful when your staking duration is short and you don't want to keep renewing it manually each time it expires.

{% hint style="warning" %}
Be careful when enabling StakeLock for long staking durations. If you decide to unstake afterward, you must first disable StakeLock and then wait for the entire lock period to expire before you can unstake your tokens.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

### **Earn Rewards**

Staking IOTX earns you rewards, which are typically distributed automatically to the same wallet you used to stake. To easily identify delegates who distribute rewards daily through IoTeX's Hermes service, look for the Hermes wing icon on [stake.iotex.io](https://stake.iotex.io).&#x20;

{% hint style="info" %}
Note: If you've enabled the **compound** option, your staking rewards will be reinvested into your staking bucket rather than transferred directly to your wallet balance.
{% endhint %}

When staking for an Hermes Delegate, you can always check your reward distribution transactions on the Hermes website:&#x20;

{% embed url="https://hermes.to" %}

### **Participate in Governance**

As a staker, you may have the right to participate in IoTeX governance decisions, contributing to the future direction of the network.

### **Unstaking**

Unstaking IOTX involves a few key steps:

1. **Disable StakeLock**: If StakeLock is enabled, you first need to disable it. This will start the countdown of your staking duration, allowing the lock period to expire.
2. **Wait for Lock Period**: Wait for the lock period to count down to zero.
3. **Initiate Unstaking**: After the lock period expires, you can initiate the unstaking process.
4. **Cooldown Period**: Once you start unstaking, there is a mandatory 3-day cooldown period.
5. **Withdraw**: After the cooldown period, you can withdraw your IOTX back to your wallet.
