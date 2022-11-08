# Option pricing

The three biggest factors that determine the price of an option are:

- **Token price** - the token price relative to the strike price
- **Time** - the amount of time remaining until expiration
- **Historical volatility** - how much the token is expected to move until expiration

### Token Price

If an option is in the money, then it is said to have intrinsic value. For example, the $80 strike call for a token worth $100 can be immediately exercised to realize a $20 gain. When you buy this call, the $20 intrinsic value is baked into the price of the option (you don’t get it for free).

### Time

The more time to expiry, the more time there is for the token to move and the more expensive the option is. The price of an option is strictly increasing with respect to time.

### Historical volatility

Volatility provides a metric for the change in price of an asset over time. Typically, the **_higher_** the volatility of an asset, the **_more_** it is expected to move, and the more expensive the option will be. If volatility is **_low_**, the **_less_** it is expected to move, and options will be cheaper.

Traditionally, option pricing models use implied volatility (IV) instead of historical volatility (HV). The IV of an asset expresses how much the asset is expected to move in the future. However, IV is calculated based on the current price of the option and accounts for fluctuations in supply, demand, and a variety of other factors impacting markets. Because the bonds are not currently on the market, it is not possible to accurately assess the IV of the bonds. Therefore, historical volitility (HV) is used. HV provides a metric of the change in an asset over a predefined period of time (e.g., the past 180 days), as opposed to accounting for future changes in the asset. By determining how volatile the underlying asset (e.g. token) has been historically, we can provide an estimation of the price of the option.
