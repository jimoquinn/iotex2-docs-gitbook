# 👨‍💻 P256Account Example

## Introduction

In this page, we explore an example P256AccountFactory that allows the creation of blockchain accounts whose transactions can be signed using the P256 curve instead of the native secp256k1 provided by the blockchain protocol.&#x20;

{% hint style="info" %}
[-> View the full source code](https://github.com/iotexproject/account-abstraction-contracts/blob/main/contracts/accounts/secp256r1/P256AccountFactory.sol)&#x20;
{% endhint %}

This is incredibly useful, as many IoT devices support this type of cryptography by default, empowering developers to create applications where users can, for example, sign transactions with their biometrics.&#x20;

This example is based on the code created by the original author of the ERC-4337. The example is deployed on IoTeX and can be freely utilized by developers:

{% hint style="info" %}
**Mainnet Contract**\
`0xD98d2B6cBca981c777037c5784721d8179D7030b`&#x20;

**Testnet Contract**\
`0x508Db1A73FcBA98594679aD4f5d8D0B880BbdaFB`
{% endhint %}

## Paymaster support

The P256AccountFactory also supports a paymaster service, which is made out of two components, a **VerifyingPaymaster** contract (view [source code](https://github.com/iotexproject/account-abstraction-contracts/blob/main/contracts/paymaster/VerifyingPaymaster.sol)) and an off-chain service **endpoint** to generate payment proofs for the paymaster contract:

**Testnet Endpoint**: [https://paymaster.testnet.w3bstream.com](https://paymaster.testnet.w3bstream.com/)

## Create P256 Accounts

The code below shows you how to interact with the p256 account implementation from a javascript client in order to create an account

[-> View the full code](https://github.com/iotexproject/account-abstraction-contracts/blob/main/scripts/secp256r1/create.ts)

```javascript
async function main() {
    // load deployed contracts
    const factory = (await ethers.getContract("P256AccountFactory")) as P256AccountFactory
    const entryPoint = (await ethers.getContract("EntryPoint")) as EntryPoint

    // an EOA account for send UserOperations
    const bundler = new ethers.Wallet(process.env.BUNDLER!, ethers.provider)

    // load secp256r1 keypair
    const keyContent = fs.readFileSync(path.join(__dirname, "key.pem"))
    const keyPair = ecPem.loadPrivateKey(keyContent)

    const publicKey = "0x" + keyPair.getPublicKey("hex").substring(2)
    const index = 0
    const account = await factory.getAddress(publicKey, index)

    // create create account UserOperation
    const initCode = hexConcat([factory.address, factory.interface.encodeFunctionData("createAccount", [publicKey, index]),])
    const createOp = {
        sender: account,
        initCode: initCode,
    }

    const fullCreateOp = await fillUserOp(createOp, entryPoint)

    // stake IOTX for gas
    const stake = await entryPoint.balanceOf(account)
    if (stake.isZero()) {
        console.log(`deposit gas for account ${account}`)
        const tx = await entryPoint
            .connect(bundler)
            .depositTo(account, { value: ethers.utils.parseEther("10") })
        await tx.wait()
    }

    // sign UserOperation using secp256r1 curve
    const chainId = (await ethers.provider.getNetwork()).chainId
    const signedOp = await signOp(
        fullCreateOp,
        entryPoint.address,
        chainId,
        new P2565Signer(keyPair)
    )

    // simulate UserOperation
    const err = await entryPoint.callStatic.simulateValidation(signedOp).catch((e) => e)
    if (err.errorName === "FailedOp") {
        console.error(`simulate op error ${err.errorArgs.at(-1)}`)
        return
    } else if (err.errorName !== "ValidationResult") {
        console.error(`unknow error ${err}`)
        return
    }
    console.log(`simulate op success`)

    // send UserOpersion to EntryPoint
    const tx = await entryPoint.connect(bundler).handleOps([signedOp], bundler.address)
    console.log(`create account tx: ${tx.hash}, account: ${account}`)
}
```

## Transfer IOTX

The following code will show you how to transfer IOTX using bundler service and paymaster.

[-> View the full code](https://github.com/iotexproject/account-abstraction-contracts/blob/main/scripts/secp256r1/transfer-bundler.ts)

```javascript
async function main() {
    const factory = (await ethers.getContract("P256AccountFactory")) as P256AccountFactory
    const accountTpl = await ethers.getContractFactory("P256Account")
    const entryPoint = (await ethers.getContract("EntryPoint")) as EntryPoint
    const paymaster = await ethers.getContract("VerifyingPaymaster")
    const bundler = new JsonRpcProvider("http://localhost:4337")

    const signer = new ethers.Wallet(process.env.PRIVATE_KEY!)

    const keyContent = fs.readFileSync(path.join(__dirname, "key.pem"))
    const keyPair = ecPem.loadPrivateKey(keyContent)

    const publicKey = "0x" + keyPair.getPublicKey("hex").substring(2)

    const index = 0
    const account = await factory.getAddress(publicKey, index)

    const callData = accountTpl.interface.encodeFunctionData("execute", [
        "0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266",
        ethers.utils.parseEther("0.1"),
        "0x",
    ])

    const transferOp = {
        sender: account,
        callData,
        preVerificationGas: 50000,
    }

    const fullCreateOp = await fillUserOp(transferOp, entryPoint)
    fullCreateOp.paymasterAndData = hexConcat([
        paymaster.address,
        defaultAbiCoder.encode(["uint48", "uint48"], [0, 0]),
        "0x" + "00".repeat(65),
    ])

    const validAfter = Math.floor(new Date().getTime() / 1000)
    const validUntil = validAfter + 86400 // one day
    const pendingOpHash = await paymaster.getHash(fullCreateOp, validUntil, validAfter)
    const paymasterSignature = await signer.signMessage(arrayify(pendingOpHash))
    fullCreateOp.paymasterAndData = hexConcat([
        paymaster.address,
        defaultAbiCoder.encode(["uint48", "uint48"], [validUntil, validAfter]),
        paymasterSignature,
    ])

    const chainId = (await ethers.provider.getNetwork()).chainId
    const signedOp = await signOp(
        fullCreateOp,
        entryPoint.address,
        chainId,
        new P2565Signer(keyPair)
    )

    const err = await entryPoint.callStatic.simulateValidation(signedOp).catch((e) => e)
    if (err.errorName === "FailedOp") {
        console.error(`simulate op error ${err.errorArgs.at(-1)}`)
        return
    } else if (err.errorName !== "ValidationResult") {
        console.error(`unknow error ${err}`)
        return
    }
    console.log(`simulate op success`)

    const hexifiedUserOp = deepHexlify(await resolveProperties(signedOp))
    const result = await bundler.send("eth_sendUserOperation", [hexifiedUserOp, entryPoint.address])
    console.log(`transfer use bundler success opHash: ${result}`)
}
```

{% hint style="info" %}
The rest of the example on how to interact with the **p256** account implementation from a javascript client, can be found at [this link](https://github.com/iotexproject/account-abstraction-contracts/tree/main/scripts/secp256r1).
{% endhint %}
