---
description: >-
  A custom ERC20 token that can be used to issue bonds.The contract handles
  issuance, payment, conversion, and redemption.
---

# Bond

## Events

### Approval

| address `indexed` | owner   |
| ----------------- | ------- |
| address `indexed` | spender |
| uint256           | value   |

### CollateralWithdraw

Emitted when collateral is withdrawn.

| address `indexed` | from     |
| ----------------- | -------- |
| address `indexed` | receiver |
| address `indexed` | token    |
| uint256           | amount   |

### Convert

Emitted when bond shares are converted by a Bond holder.

| address `indexed` | from                     |
| ----------------- | ------------------------ |
| address `indexed` | collateralToken          |
| uint256           | amountOfBondsConverted   |
| uint256           | amountOfCollateralTokens |

### ExcessPaymentWithdraw

Emitted when payment over the required amount is withdrawn.

| address `indexed` | from     |
| ----------------- | -------- |
| address `indexed` | receiver |
| address `indexed` | token    |
| uint256           | amount   |

### Initialized

### OwnershipTransferred

| address `indexed` | previousOwner |
| ----------------- | ------------- |
| address `indexed` | newOwner      |

### Payment

Emitted when a portion of the Bond's principal is paid.

| address `indexed` | from   |
| ----------------- | ------ |
| uint256           | amount |

### Redeem

Emitted when a bond share is redeemed.

| address `indexed` | from                          |
| ----------------- | ----------------------------- |
| address `indexed` | paymentToken                  |
| address `indexed` | collateralToken               |
| uint256           | amountOfBondsRedeemed         |
| uint256           | amountOfPaymentTokensReceived |
| uint256           | amountOfCollateralTokens      |

### TokenSweep

Emitted when a token is swept by the contract owner.

| address                 | from     |
| ----------------------- | -------- |
| address `indexed`       | receiver |
| contract IERC20Metadata | token    |
| uint256                 | amount   |

### Transfer

| address `indexed` | from  |
| ----------------- | ----- |
| address `indexed` | to    |
| uint256           | value |

## Errors

### BondBeforeGracePeriodAndNotPaid

* Bond redemption is impossible because the grace period has not yet passed and the bond has not been fully paid.

### BondPastMaturity

* Operation restricted because the Bond has matured.

### NoPaymentToWithdraw

* Attempted to withdraw with no excess payment in the contract.

### NotEnoughCollateral

* Attempted to withdraw more collateral than available.

### PaymentAlreadyMet

* Attempted to pay after payment was met.

### SweepDisallowedForToken

* Attempted to sweep a token used in the contract.

### ZeroAmount

* Attempted to perform an action that would do nothing.

## Methods

### allowance

```solidity
function allowance(address owner, address spender) external view returns (uint256)
```

#### Parameters

| address | owner   |
| ------- | ------- |
| address | spender |

#### Returns

### amountUnpaid

```solidity
function amountUnpaid() external view returns (uint256 paymentTokens)
```

The amount of paymentTokens required to fully pay the contract.

#### Returns

### approve

```solidity
function approve(address spender, uint256 amount) external nonpayable returns (bool)
```

#### Parameters

| address | spender |
| ------- | ------- |
| uint256 | amount  |

#### Returns

### balanceOf

```solidity
function balanceOf(address account) external view returns (uint256)
```

#### Parameters

#### Returns

### burn

```solidity
function burn(uint256 amount) external nonpayable
```

#### Parameters

### burnFrom

```solidity
function burnFrom(address account, uint256 amount) external nonpayable
```

#### Parameters

| address | account |
| ------- | ------- |
| uint256 | amount  |

### collateralBalance

```solidity
function collateralBalance() external view returns (uint256 collateralTokens)
```

The external balance of the ERC20 collateral token.

#### Returns

### collateralRatio

```solidity
function collateralRatio() external view returns (uint256)
```

The number of collateralTokens per Bond.

#### Returns

### collateralToken

```solidity
function collateralToken() external view returns (address)
```

The ERC20 token used as collateral backing the bond.

#### Returns

### convert

```solidity
function convert(uint256 bonds) external nonpayable
```

For convertible Bonds (ones with a convertibilityRatio > 0), the Bond holder may convert their bond to underlying collateral at the convertibleRatio. The bond must also have not past maturity for this to be possible.

#### Parameters

### convertibleRatio

```solidity
function convertibleRatio() external view returns (uint256)
```

The number of convertibleTokens the bonds will convert into.

#### Returns

### decimals

```solidity
function decimals() external view returns (uint8)
```

#### Returns

### decreaseAllowance

```solidity
function decreaseAllowance(address spender, uint256 subtractedValue) external nonpayable returns (bool)
```

#### Parameters

| address | spender         |
| ------- | --------------- |
| uint256 | subtractedValue |

#### Returns

### gracePeriodEnd

```solidity
function gracePeriodEnd() external view returns (uint256 gracePeriodEndTimestamp)
```

One week after the maturity date. Bond collateral can be redeemed after this date.

#### Returns

### increaseAllowance

```solidity
function increaseAllowance(address spender, uint256 addedValue) external nonpayable returns (bool)
```

#### Parameters

| address | spender    |
| ------- | ---------- |
| uint256 | addedValue |

#### Returns

### initialize

```solidity
function initialize(string bondName, string bondSymbol, address bondOwner, uint256 _maturity, address _paymentToken, address _collateralToken, uint256 _collateralRatio, uint256 _convertibleRatio, uint256 maxSupply) external nonpayable
```

This one-time setup initiated by the BondFactory initializes the Bond with the given configuration.

#### Parameters

| string  | bondName           | Passed into the ERC20 token to define the name.                                                                                                                            |
| ------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| string  | bondSymbol         | Passed into the ERC20 token to define the symbol.                                                                                                                          |
| address | bondOwner          | Ownership of the created Bond is transferred to this address by way of \_transferOwnership and also the address that tokens are minted to. See \`initialize\` in \`Bond\`. |
| uint256 | \_maturity         | The timestamp at which the Bond will mature.                                                                                                                               |
| address | \_paymentToken     | The ERC20 token address the Bond is redeemable for.                                                                                                                        |
| address | \_collateralToken  | The ERC20 token address the Bond is backed by.                                                                                                                             |
| uint256 | \_collateralRatio  | The amount of collateral tokens per bond.                                                                                                                                  |
| uint256 | \_convertibleRatio | The amount of convertible tokens per bond.                                                                                                                                 |
| uint256 | maxSupply          | The amount of Bonds given to the owner during the one- time mint during this initialization.                                                                               |

### isMature

```solidity
function isMature() external view returns (bool isBondMature)
```

Checks if the maturity timestamp has passed.

#### Returns

### maturity

```solidity
function maturity() external view returns (uint256)
```

A date set at Bond creation when the Bond will mature.

#### Returns

### name

```solidity
function name() external view returns (string)
```

#### Returns

### owner

```solidity
function owner() external view returns (address)
```

#### Returns

### pay

```solidity
function pay(uint256 amount) external nonpayable
```

Allows the owner to pay the bond by depositing paymentTokens.

#### Parameters

### paymentBalance

```solidity
function paymentBalance() external view returns (uint256 paymentTokens)
```

Gets the external balance of the ERC20 paymentToken.

#### Returns

### paymentToken

```solidity
function paymentToken() external view returns (address)
```

This is the token the borrower deposits into the contract and what the Bond holders will receive when redeemed.

#### Returns

### previewConvertBeforeMaturity

```solidity
function previewConvertBeforeMaturity(uint256 bonds) external view returns (uint256 collateralTokens)
```

Before maturity, if the given bonds are converted, this would be the number of collateralTokens received. This function rounds down the number of returned collateral.

#### Parameters

#### Returns

### previewRedeemAtMaturity

```solidity
function previewRedeemAtMaturity(uint256 bonds) external view returns (uint256 paymentTokensToSend, uint256 collateralTokensToSend)
```

At maturity, if the given bond shares are redeemed, this would be the number of collateralTokens and paymentTokens received by the bond holder. The number of paymentTokens to receive is rounded down.

#### Parameters

#### Returns

| uint256 | The number of paymentTokens that the bond shares would be redeemed for. |
| ------- | ----------------------------------------------------------------------- |
| uint256 | The number of collateralTokens that would be redeemed for.              |

### previewWithdrawExcessCollateral

```solidity
function previewWithdrawExcessCollateral() external view returns (uint256 collateralTokens)
```

The number of collateralTokens that the owner would be able to withdraw from the contract. This does not take into account an amount of payment like `previewWithdrawExcessCollateralAfterPayment` does. See that function for more information.

#### Returns

### previewWithdrawExcessCollateralAfterPayment

```solidity
function previewWithdrawExcessCollateralAfterPayment(uint256 payment) external view returns (uint256 collateralTokens)
```

The number of collateralTokens that the owner would be able to withdraw from the contract. This function rounds up the number of collateralTokens required in the contract and therefore may round down the amount received.

#### Parameters

#### Returns

### previewWithdrawExcessPayment

```solidity
function previewWithdrawExcessPayment() external view returns (uint256 paymentTokens)
```

The number of excess paymentTokens that the owner would be able to withdraw from the contract.

#### Returns

### redeem

```solidity
function redeem(uint256 bonds) external nonpayable
```

The Bond holder can burn bond shares in return for their portion of paymentTokens and collateralTokens backing the Bonds. These portions of tokens depends on the number of paymentTokens deposited. When the Bond is fully paid, redemption will result in all paymentTokens. If the Bond has reached maturity without being fully paid, a portion of the collateralTokens will be available.

#### Parameters

### renounceOwnership

```solidity
function renounceOwnership() external nonpayable
```

### sweep

```solidity
function sweep(contract IERC20Metadata sweepingToken, address receiver) external nonpayable
```

Sends ERC20 tokens to the owner that are in this contract.

#### Parameters

| contract IERC20Metadata | sweepingToken | The ERC20 token to sweep and send to the receiver. |
| ----------------------- | ------------- | -------------------------------------------------- |
| address                 | receiver      | The address that is transferred the swept token.   |

### symbol

```solidity
function symbol() external view returns (string)
```

#### Returns

### totalSupply

```solidity
function totalSupply() external view returns (uint256)
```

#### Returns

### transfer

```solidity
function transfer(address to, uint256 amount) external nonpayable returns (bool)
```

#### Parameters

| address | to     |
| ------- | ------ |
| uint256 | amount |

#### Returns

### transferFrom

```solidity
function transferFrom(address from, address to, uint256 amount) external nonpayable returns (bool)
```

#### Parameters

| address | from   |
| ------- | ------ |
| address | to     |
| uint256 | amount |

#### Returns

### transferOwnership

```solidity
function transferOwnership(address newOwner) external nonpayable
```

#### Parameters

### withdrawExcessCollateral

```solidity
function withdrawExcessCollateral(uint256 amount, address receiver) external nonpayable
```

The Owner may withdraw excess collateral from the Bond contract. The number of collateralTokens remaining in the contract must be enough to cover the total supply of Bonds in accordance to both the collateralRatio and convertibleRatio.

#### Parameters

| uint256 | amount   | The number of collateralTokens to withdraw. Reverts if the amount is greater than available in the contract. |
| ------- | -------- | ------------------------------------------------------------------------------------------------------------ |
| address | receiver | The address transferred the excess collateralTokens.                                                         |

### withdrawExcessPayment

```solidity
function withdrawExcessPayment(address receiver) external nonpayable
```

The owner can withdraw any excess paymentToken in the contract.

#### Parameters
