---
layout: post
title:  "Net Present Value, Mark-to-Market Profit and Loss"
categories: Risk
tags: Risk PnL NPV 
comments: true
---
Mark-to-Market Profit and Loss (MTM PnL) is the process of ascribing a fair value of goods and comparing to the agreed cost of goods. Although this is a simple idea there are a host of subtleties to arriving at a fair value - especially for physical commodities.

<!--more-->

## A Fair Value
The first question is how do you arrive at a fair value for a physical commodity and who should make this determination? The second part of the question is the simplest to answer - it should be the middle-office Risk team that assigns a value. Why? Because we need an independent measure of PnL that does not depend on the details of the deal done to purchase the goods. If the Front Office were to determine the value then this indepence would be lost. Off course, the Front Office should agree with Risk's valuation and disagreements will lead to robust discussions from both sides.

The first part of the question what is a fair value for goods. The factors at play are:
* The physical nature of the goods, clearly copper and gold have very different valuations but, in addition, there are other physical factors:
    * The chemical/physical charactertics of the commodity, e.g. energy content in coal, sulphour content in iron ore or purity for a precious metal
    * The physical form of the commodity, e.g. palladium is traded as ingots and sponge. The latter is more useful for manufacturing (e.g. catalytic converters) and hence carries a premium over ingots. Copper can be in plate or rod form and consequently of more or less value for different manufacturing processes
    * Brand concepts - although we think of 'commodities' trading as being immune for branding there are brand like concepts. E.g.thermal coal from a particular mine may have a brand presence in the market that might command a premium and some certification authorities can assign a 'brand' to a commodity as a short hand for it's form and other characteristics, e.g. LME approved copper.
* The location of the goods. In general goods in different locations command different values, e.g., thermal coal in South Africa is worth considerably less than identical coal in Amsterdam, Rotterdam and Antwerp (the ARA region). The difference can be partly ascribed to the freight cost of moving the goods from a supply region to a demand region but the price relationships are usually complex. In addition to location we need to consider contract terms, e.g. incoterms:
    * a Free-on-Board (FOB) term means you're paying for goods as they cross the ship's rail (assuming bulk commodities). The cost of moving the goods is the buyers reponsibility. However, a Cost of Insurance and Freight (CIF) term could apply to goods bought in the same location but include the cost of shipping them to a destination. Free-along-side (FAS) terms mean the price for loading or discharging goods onto a vessel at sea and clearly this price will be less than the cost of having the goods delivered to the quayside.
    * Some goods have a global price that is largely independent of the location they're held. For example, fungible precious metal ingots are treated like cash and it doesn't matter if they are held in Hong Kong or London as the goods can be instantaneouly swapped for goods of equal value between locations.
* When the title of the goods changes hands. Some goods are seasonal, e.g. natural gas in the Northern hemisphere will cost more in the winter, when there is more demand, than in the summer and some goods have cyclical demand (e.g. iron ore for steel making to satisfy a building boom in China) that mean the forward estimate of these goods might be in contango for the next few years.

The above can be summarized as the fair value should be determined from 'what it is', 'where it is', and 'when it is'.

## Net Present Value
When we discussed fair value in the previous section we were talking about assigning a 'future value' to the goods. But in order to work out a PnL useful for making trading descisions we need to assign a 'net present value' (NPV) to the both the value of the goods and the costs we've agreed to pay for them.

In some Commodity Trading Risk Management (CTRM) systems the PnL for a physical delivery is described per delivery along the lines of:

$quantity * (value - cost) * discount factor$

where $discount factor$ is a fraction determined by the estimated interest rate curve and the 'due date' of the exchange of cash.

Let's take an example to see what's problematic with this approach. Say, I agree to buy 100,000MT of Iron Ore for $130/MT for delivery in 3 months time and payment terms of 30 days after delivery. Assume that our risk team has assigned fair future value to the Iron Ore of $129.50/MT. Futhermore, assume a flat interest rate of 5% for the forseeable future (obviously we would have a changing forward estimate for interest rates but this factor isn't germain to the discussion).

At first glance this deal doesn't look so good, we've paid 50 cents more per MT than the Iron Ore is worth so our future value PnL is $100,000 * (129.50 - 130) = -50,000$ dollars. But what if we take the net present value? The terms say we pay 30 days after delivery which is 3 months in the future so we calculate an discount factor of approximately $0.98343$. Our NPV PnL is now $-50,000*0.98343 =  -49,171.49$ dollars. Still not a good deal.

The problem with this MTM PnL is we're discounting the value of the goods using the same date as the exchange of cash. There's two problems with this:
* It's wrong - we receive the goods 30 days before we pay for them and we might be planning to sell them immediately wtih more favourable terms.
* The independence of the MTM valuation is broken - we're now taking into account the trader's contract terms into our fair value net present value.

A better way to calculate the PnL is to treat the cost and the value separately. If we do this then we need a 'due date' for the exchange of goods and the title/delivery date is a good first staring point. 

The discount factor for the delivery date is 3 months from now and is approximately $0.98742$ and our new NPV PnL calculation is:

$100,000 * 129.50 * 0.98742 - 100,000 * 130.00 * 0.98343 = 2,507.46 
$ dollars.

Now, our deal that looked like a $49k loss is actually a $2.5k gain - thanks to the favourable payment terms negotiated by the trader.

In our new model we've used title transfer as the 'due date' for the calculation of the NPV of the goods. There is a good argument for saying that, just like the future fair value, the due date should be a function of the what/where/when properties of the goods. I.e. the MTM value should represent a 'replacement value' the payment terms of buying or selling the same goods which depend on the nature of the goods, their location and when the transation is taking place (at least for seasonal markets).

## Intermediate Cash Flows
In the previous section we refined our PnL model for a physical delivery to be 

$quantity * value * df_v - quantity * cost * df_c$ where $df_v$ is the discount factor for the valuation of the goods and $df_c$ is the discount factor for the cost.

In many physical commodity markets the PnL is not this simple, as the cost of the goods is paid for with intermediate cash flows - i.e., prepayment or provisional payments. A prepayment would be a payment before the goods change hands and a provisional payment would be an estimated payment a short time after the title transfer but using esimated final prices, quantities or lab analysis. Intermediate cash flows allow the seller to manage their credit risk and cash flows in a more controlled way.

If we return to the previous deal we said that the trader had agreed payment, in full, 30 days after delivery. A more likely scenario, when a lot of money is changing hands, is that the deal would include a provisional payment, probably based on some bench mark price, payable 5 days after title transfer. Let's assume that the bench mark price is $129 (i.e. a little less than the estimated forward price of the goods). If we work out the discount factor for the provisional payment we get $df_p = 0.98675$ and our new NPV PnL calculation is:

$quantity * value * df_v - quantity * price_p * df_p - quantity * (price_f - price_p) * df_f$ where $df_f$ is the final payment discount factor and $price_f$ and $price_p$ are the final and privisional prices respectively.

i.e.

$100,000 * 129.50 * 0.98742 -100,000 * 129 * 0.98675 - 100,000 * (130.00 - 129.00) * 0.98343 =  -40,363.06$ dollars.

With these less favourable payment terms the deal is now a significant loss.

## Summary
MTM seems like a simple concept but we've seen that determining a fair future value is not a simple task and that a model for net present value needs careful consideration. The points made about net present value and discount factors also apply to FX conversions done for reporting purposes. If you're reviewing your model for PnL then ensure the MTM NPV fair value is independent of the contract's price and payment terms and check whether your system or processes take intermediate cash flows into account for both discounting and FX reporting. If not, your PnL could be giving you the wrong signals.

