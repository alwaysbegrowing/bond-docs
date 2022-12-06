# Auctions

## Summary

Auctions allow borrowers to set a minimum price for their bond sales and allow market demand to set the final price. Setting a minimum price also sets a maximum interest rate the borrower is willing to pay.

## Market-driven bond pricing

Auctions are implemented as batch auctions where lenders submit public bids with their desired amount and interest rate. Bids are included in the order of lowest interest rate to highest with a higher bid amount breaking ties. At auction end, the minimum interest rate required to reach the funding threshold is determined. This is the final rate for all participants. Lenders who specified an interest rate lower than or equal to the final clearing interest rate receive bonds at the clearing interest rate. Lenders that specified an interest rate higher than the final clearing interest rate do not receive any bonds and have their funds refunded.

![](<../../.gitbook/assets/image (44).png>)

If the funding threshold is not surpassed, there is no auction settlement and lenders’ funds are returned.

{% hint style="info" %}
Auctions are powered by Gnosis Auction. For more details, [read their docs](https://gnosis-auction.eth.link/#/docs#topAnchor).
{% endhint %}

## Auction details

Once you click on an ongoing auction under the “offerings” tab, you will see the auction details with all the necessary information available.

![Screenshot 2022-12-06 at 15 30 53](https://user-images.githubusercontent.com/112566599/205860129-23223a61-903f-4dd0-a641-ed7906989fc5.png)

As seen in the screenshot above, you will find the following information.

Offering amount: The total amount of bonds offered during this auction

Current bond price: The current price you can purchase the bond for. The price might change depending on the total order volume.

Total order volume: This amount shows the total amount of USDC already deposited for the offered bonds.

Current bond YTM (Yield to maturity): The number shows what annualized yield you will receive in total if participating in the offering. It reflects the delta in-between the bond price and the face value.

Min. Funding threshold: If the total order volume did not reach this threshold, the auction failed. All deposits will be returned. The threshold needs to be reached within the auction period.

Min. Bond price: The DAO offers the bond for that price at the beginning auction. The minimum bond may be lower than the current bond price if the auction is over-subscribed.

Max bond YTM: The maximum yield to maturity is the total delta in-between the minimum bond price and the face value at maturity. The shown YTM is an annualized rate and is similar to the term “APY” in defi.

## Place an order

To place an order, enter the amount of USDC you would like to lend out.

Define your maximum acceptable bond price and therefore minimum accepted yield for the offering.

![](https://user-images.githubusercontent.com/112566599/205862297-64cf00b6-8c42-4c46-b562-202791b5e915.jpeg)

If the current bond price at the closing of the auction is lower than your accepted maximum bond price, your order will get filled. You can claim your bonds after the auction.

Please find a video with a walk-through [here](https://youtu.be/GtH\_fnBuBV4):

