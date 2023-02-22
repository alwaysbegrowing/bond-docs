# Orderbook

The orderbook allows investors to buy and sell active bonds from previous auctions, acting as a secondary marketplace. It follows the  [classic bid-ask model](https://www.investopedia.com/terms/o/order-book.asp) and uses the limit order framework of [1inch protocol](https://app.1inch.io/#/1/simple/swap/ETH/DAI). 1inch is one of the largest DEX aggregators and has [battle-tested code](https://github.com/1inch/limit-order-protocol) allowing Arbor to integrate the orderbook feature directly into our pre-existing UI.



**How to use the orderbook?**

You can find the orderbook here: [https://app.arbor.finance/orderbook](https://app.arbor.finance/orderbook)

Orders are listed as "Sell orders" to sell bonds or "Buy Orders" for USDC offered for bonds. All orders are considered limit orders.&#x20;

Select the bond you are interested in buying or selling from the dropdown menu on the right side of the orderbook table:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 22.02.53.png" alt=""><figcaption></figcaption></figure>

Connect your wallet to continue. To buy a bond, select the "Sell" tab to find available bonds listed in the market. To sell a bond, select the "Buy" tab to find potential offers for your bonds.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 22.01.21.png" alt=""><figcaption></figcaption></figure>

Once you identify an appropriate offer, complete the token approval process and fill the order to trigger the transaction from within your connected wallet. Each order can be filled partially or completely. The necessary funds must be in your connected wallet at the time the transaction is submitted to settle the transaction.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-21 at 20.25.15.png" alt=""><figcaption><p>Fill the limit order after approval</p></figcaption></figure>

