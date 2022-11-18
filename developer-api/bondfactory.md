---
description: This factory contract issues new bond contracts.
---

# BondFactory

## Events

### BondCreated

Emitted when a new bond is created.

| address           | newBond                |
| ----------------- | ---------------------- |
| string            | name                   |
| string            | symbol                 |
| address `indexed` | owner                  |
| uint256           | maturity               |
| address `indexed` | paymentToken           |
| address `indexed` | collateralToken        |
| uint256           | collateralTokenAmount  |
| uint256           | convertibleTokenAmount |
| uint256           | bonds                  |

### IssuerAllowListEnabled

Emitted when the restriction of bond creation to allow-listed accounts is toggled on or off.

### RoleAdminChanged

| bytes32 `indexed` | role              |
| ----------------- | ----------------- |
| bytes32 `indexed` | previousAdminRole |
| bytes32 `indexed` | newAdminRole      |

### RoleGranted

| bytes32 `indexed` | role    |
| ----------------- | ------- |
| address `indexed` | account |
| address `indexed` | sender  |

### RoleRevoked

| bytes32 `indexed` | role    |
| ----------------- | ------- |
| address `indexed` | account |
| address `indexed` | sender  |

### TokenAllowListEnabled

Emitted when the restriction of collateralToken and paymentToken to allow-listed tokens is toggled on or off.

## Errors

### CollateralTokenAmountLessThanConvertibleTokenAmount

* There must be more collateralTokens than convertibleTokens.

### InvalidDeposit

* Fails if the collateralToken takes a fee.

### InvalidMaturity

* Maturity date is not valid.

### TokensMustBeDifferent

* The paymentToken and collateralToken must be different.

### TooManyDecimals

* Decimals with more than 18 digits are not supported.

### ZeroBondsToMint

* Bonds must be minted during initialization.

## Methods

### ALLOWED\_TOKEN

```solidity
function ALLOWED_TOKEN() external view returns (bytes32)
```

The role given to allowed tokens.

#### Returns

### DEFAULT\_ADMIN\_ROLE

```solidity
function DEFAULT_ADMIN_ROLE() external view returns (bytes32)
```

#### Returns

### ISSUER\_ROLE

```solidity
function ISSUER_ROLE() external view returns (bytes32)
```

The role required to issue bonds.

#### Returns

### createBond

```solidity
function createBond(string name, string symbol, uint256 maturity, address paymentToken, address collateralToken, uint256 collateralTokenAmount, uint256 convertibleTokenAmount, uint256 bonds) external nonpayable returns (address clone)
```

Creates a new Bond. The calculated ratios are rounded down.

#### Parameters

| string  | name                   | Passed into the ERC20 token to define the name.                                                       |
| ------- | ---------------------- | ----------------------------------------------------------------------------------------------------- |
| string  | symbol                 | Passed into the ERC20 token to define the symbol.                                                     |
| uint256 | maturity               | The timestamp at which the Bond will mature.                                                          |
| address | paymentToken           | The ERC20 token address the Bond is redeemable for.                                                   |
| address | collateralToken        | The ERC20 token address the Bond is backed by.                                                        |
| uint256 | collateralTokenAmount  | The amount of collateral tokens per bond.                                                             |
| uint256 | convertibleTokenAmount | The amount of convertible tokens per bond.                                                            |
| uint256 | bonds                  | The amount of Bonds given to the owner during the one-time mint during the \`Bond\`'s \`initialize\`. |

#### Returns

### getRoleAdmin

```solidity
function getRoleAdmin(bytes32 role) external view returns (bytes32)
```

#### Parameters

#### Returns

### grantRole

```solidity
function grantRole(bytes32 role, address account) external nonpayable
```

#### Parameters

| bytes32 | role    |
| ------- | ------- |
| address | account |

### hasRole

```solidity
function hasRole(bytes32 role, address account) external view returns (bool)
```

#### Parameters

| bytes32 | role    |
| ------- | ------- |
| address | account |

#### Returns

### isBond

```solidity
function isBond(address) external view returns (bool)
```

Returns whether or not the given address key is a bond created by this Bond factory.

#### Parameters

#### Returns

### isIssuerAllowListEnabled

```solidity
function isIssuerAllowListEnabled() external view returns (bool)
```

If enabled, issuance is restricted to those with ISSUER\_ROLE.

#### Returns

### isTokenAllowListEnabled

```solidity
function isTokenAllowListEnabled() external view returns (bool)
```

If enabled, tokens used as paymentToken and collateralToken are restricted to those with the ALLOWED\_TOKEN role.

#### Returns

### renounceRole

```solidity
function renounceRole(bytes32 role, address account) external nonpayable
```

#### Parameters

| bytes32 | role    |
| ------- | ------- |
| address | account |

### revokeRole

```solidity
function revokeRole(bytes32 role, address account) external nonpayable
```

#### Parameters

| bytes32 | role    |
| ------- | ------- |
| address | account |

### setIsIssuerAllowListEnabled

```solidity
function setIsIssuerAllowListEnabled(bool _isIssuerAllowListEnabled) external nonpayable
```

Sets the state of bond restriction to allow-listed accounts.

#### Parameters

### setIsTokenAllowListEnabled

```solidity
function setIsTokenAllowListEnabled(bool _isTokenAllowListEnabled) external nonpayable
```

Sets the state of token restriction to the list of allowed tokens.

#### Parameters

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool)
```

#### Parameters

#### Returns

### tokenImplementation

```solidity
function tokenImplementation() external view returns (address)
```

Address where the bond implementation contract is stored.

#### Returns
