---
description: Additional steps may be taken to enhance the borrower's credit.
---

# Credit Enhancers

## Promissory Note

Issuers may add an on-chain promise to repay the bond. This is displayed alongside the issuer information on the Bond page. The message to be signed consists of the `bond` address as well as the content **"This signature represents a promise to unconditionally pay the bond by the maturity date."**

<details>

<summary>Developer Details</summary>

```
ARBOR_PROMISSORY_NOTE_DOMAIN = ({ chainId }: { chainId: number }) => ({
  chainId,
  name: 'Arbor Finance',
  version: '1.0.0',
})

ARBOR_PROMISSORY_NOTE_TYPES = {
  PromissoryNote: [
    { type: 'address', name: 'bond' },
    { type: 'string', name: 'content' },
  ],
}

ARBOR_PROMISSORY_NOTE_VALUE = (address: string) => ({
  bond: address,
  content:
    'This signature represents a promise to unconditionally pay the bond by the maturity date.',
})
```



</details>
