# Components of AA

## Components of the AA Infra <a href="#components-of-the-aa-infra" id="components-of-the-aa-infra"></a>

The components of the AA infrastructure are illustrated below:

<figure><img src="https://docs.iotex.io/~gitbook/image?url=https%3A%2F%2F448392349-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-MUPHwAAaa4_zIrX70rA%252Fuploads%252Fa75kvybShBILJ8McfG9j%252Faa%2520.png%3Falt%3Dmedia%26token%3Da652153f-cb94-42e9-ab2b-32b134436bc3&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=4bf139ed464d73d03c9f9d8c7ab075b9d2dde7c16241017673b032c4ce7393fd" alt=""><figcaption></figcaption></figure>

### **Bundler Services**

A bundler is an off-chain node that aggregates multiple abstracted user operations into a single transaction that the underlying blockchain can process. This transaction is sent to the other fixed component, called the `EntryPoint` Contract.

**Mainnet endpoint:** [https://bundler.w3bstream.com](https://bundler.w3bstream.com/)

**Testnet endpoint:** [https://bundler.testnet.w3bstream.com](https://bundler.testnet.w3bstream.com/)

### **EntryPoint Contract**:

The EntryPoint contract is in charge of deploying certain special contracts, called `AccountFactory` contracts, which in turn are in charge of creating certain accounts (wallet contracts) that can be used for specific purposes.

**Mainnet Entrypoint:** `0xc3527348De07d591c9d567ce1998eFA2031B8675`

**Testnet Entrypoint:** `0xc3527348De07d591c9d567ce1998eFA2031B8675`
