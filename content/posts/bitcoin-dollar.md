+++
title = 'Bitcoin Dollar'
date = 2024-07-22T15:10:31+09:00
draft = true

+++

## Introduction

I will start by saying that I believe an innovation has been right in front of our eyes for a long time, and it has been our biggest mistake not to view it in the proper light.

Technically, there is nothing new about what I am about to say; the only thing I want to convey in this essay is the importance of looking at what we already know from another perspective that is better suited to contextualizing the innovation within our current economic technology.

I will start by mentioning that I am not a professional in macroeconomics, finance, or banking. Despite this, I believe the ideas presented are significant enough to merit consideration, as they propose a fundamentally different approach to how we can utilize financial instruments on Lightning Network.

My thesis is as follows:

Today, there are no barriers to prevent the creation of:

* An untrusted Bitcoin-Dollar, a superior form of Eurodollar that makes stablecoins obsolete
* Untrusted brokering

## Terminology

### Dollar in the US

The dollar is commonly known as the liability of the Federal Reserve (FED). However, in the US, dollar liabilities from US banks are also considered as dollars.

Practically, there is no fundamental limit on the amount of dollars that US banks can create. A bank's dollars are created when a loan is undertaken and destroyed when the loan is repaid.

While the FED imposes a fractional limit, this is not currently the limiting factor in loan creation.

### Eurodollar

Similarly, banks outside of the US can create US dollar liabilities. European banks, thus, create Eurodollars, and Asian banks create Asiandollars. These dollars are liabilities in US dollars held by foreign banks.

Unlike dollars in the US, they fall outside the jurisdiction of the U.S. Federal Reserve and other U.S. regulatory agencies.

### Stablecoin

Stablecoins, such as USDT, are quite similar to Eurodollars; stablecoins are liabilities of their issuer, where the issuer is a foreign entity (non-US). The main innovation of stablecoins is how these liabilities are tracked. Rather than using double-entry ledgers, they are represented by an asset that can be transferred via operations on a blockchain.

If you are interested, "Broken Money" by Lyn Alden goes deeper into the different ledger technologies in history.

Stablecoins do not change the concept of the Eurodollar; they are just using a different way to track and transfer them.

### Bitcoin Dollar

On the other hand, the Lightning Network, or more generally, real Layer 2 layers (defined as protocols that allow unilateral exit from the relationship) enable the creation of a completely new form of US Dollar, free of trust and liability.

I believe this represents a fundamental monetary innovation which, in hindsight, is obvious but has been overlooked due to an excessive focus on technology. This innovation is potentially even more fundamental than stablecoins.

While stablecoins only innovate on how the liabilities are tracked, the Bitcoin Dollar has no liability.

I believe this could make stablecoins obsolete. (Disclaimer: Our project, BTCPay Server, is proudly sponsored by Tether; this is not personal, we still love you!)

While I am discussing Bitcoin Dollar here, there is nothing specific to the dollar. The same principles can work with any asset, and I will address this subject later in this essay.

The rest of this piece will explore the economic mechanisms for this innovation, but will leave the specific technical methods aside.

## Structure

First, we will explore the concrete stability mechanisms of pegging the USD via Lightning and generalize it to the pegging of a portfolio, potentially with derivatives.

Then, we will examine the stability mechanisms involved in incoming and outgoing payments.

This will be followed by a short section highlighting the risks and limitations of our approach.

We will then conclude by enumerating the different costs involved for the entity providing such a pegging service (also called the `pegging provider`).


## Stability Mechanisms

This part focus on the detailed mechanism in how `Alice`, who doesn't necessarily want Bitcoin asset, interact with `Bob` to peg her channel's balance worth to one or, or a portfolio of several assets.

While this part focus on only two individuals, we will explore in the later section, how this can enable cross currency payment between two nodes on the Lightning Network.

Feel free to skip to the next section if you wish to skip over the calculations.

### Dollar pegging on Lightning

Let's imagine a merchant, `Alice`, wants to be able to receive Bitcoin payments that are pegged to the dollar. This merchant is connected to a Lightning Service Provider (LSP), `Bob`, providing such a service.

Let's assume the two Lightning nodes are connected by a channel and consider `A[BTC]` and `B[BTC]`, which keep track of the expected Lightning balance state between Alice and Bob, respectively.

| A[BTC] | B[BTC]  |
|---|---|
| 0.5  | 0.5  |

The `expected balance` may differ from the `actual balance` on the Lightning channel. The difference between them is referred to as `unsettled funds`.

The price is `$100,000 USD` per BTC, and `Alice` announces that she wants to peg her bitcoins to the USD with `Bob`.

Their channel then becomes a `peg relation`. Alice is a `peg consumer`, while Bob is the `peg provider`.

From now on, we will keep track of Alice's `virtual balance`, $A_v[USD]$.
| A[BTC] | $A_v[USD]$ | B[BTC]  |
|---|---|---|
| 0.5  | 50,000| 0.5  |

Now, what we really want is to maintain the following invariant:  $$A_V[USD]=A[BTC] * R[USD]$$

If `BTC` goes to `$110,000 USD`, then 
$$
50,000=A[BTC]*110,000 \\
A[BTC]=\frac{50,000}{110,000}=0.45454545
$$

Then it means that the `unsettled funds` increased by $0.5 - 0.45454545 = 0.04545455$ in `Bob`'s favor; the expected balances reflect the change.

The new state will be 

| A[BTC] | $A_v[USD]$ | B[BTC]  |
|---|---|---|
| 0.45454545  | 50,000| 0.54545455 |

`Unsettled funds` can become settled periodically or immediately by simply sending a lightning payment between `Alice` and `Bob` to make the actual channel balance match the expected one. (This mechanism is called a `Stable Channel`)

### Portfolio pegging

Now, imagine that `Alice` wants to balance her Lightning channel's BTC into the following assets, with the corresponding weights:

| $A_w[BTC]$ | $A_w[USD]$ | $A_w[NVDA]$ |
|---|---| --- |
| 60%  | 10%  | 30% |

And the conversion rates to BTC are as follows (assuming `100 USD/NVDA`):

| R[BTC] | R[USD] | R[NVDA] |
|---|---| --- |
| 1 | 100,000  | 1,000 |

> Note that `R[NVDA]` is `NVDA/BTC`, so: $R[NVDA] = R[USD] * (\frac{USD}{NVDA})^{-1}$

Alice's `virtual balance` thus becomes $$A_v[X]=R[X]*A_w[X]*A[BTC]$$

This results in the following state:

| A[BTC] | $A_v[BTC]$ | $A_v[USD]$ | $A_v[NVDA]$ | B[BTC] |
|---|---|---| --- | ---|
| 0.5 | 0.3 | 5,000  | 150 | 0.5 |

Now, imagine the new rates are:

| R[BTC] | R[USD] | R[NVDA] |
|---|---| --- |
| 1 | ~~100,000~~ -> 110,000  | ~~1000~~ ->500 |

Alice's Bitcoin expected channel balance `A[BTC]` needs to be updated:

$$A[BTC]=\sum_X\frac{A_v[X]}{R[X]}$$

The new `virtual balance` becomes:

| A[BTC] | $A_v[BTC]$ | $A_v[USD]$ | $A_v[NVDA]$ | B[BTC]  |
|---|---|---|---|---|
| ~~0.5~~ -> 0.64545455 | 0.3 | 5,000  | 150 | ~~0.5~~ -> 0.35454545 |

The `unsettled funds` increased by `0.64545455 - 0.5 = 0.14545455` to `Alice`'s favor.

### Portfolio rebalancing

The initial portfolio composition is unlikely to remain the same as the rates fluctuate.

Alice may, or may not, want to preserve this initial portfolio allocation by rebalancing the assets.

Rebalancing a portfolio is an operation that doesn't require any Lightning payments, just an update of the peg relation between `Alice` and `Bob`.

For example, in our previous example, the rates changed, and thus the composition became:

$$A_w[X]=\frac{\frac{A_v[X]}{R[X]}}{\sum\frac{A_v}{R}}$$

| $A_w[BTC]$ | $A_w[USD]$ | $A_w[NVDA]$ |
|---|---| --- |
| ~~60%~~ -> 46.5%  | ~~10%~~ -> 7%  | ~~30%~~ -> 46.5% |

To rebalance and maintain the original composition, we simply need to perform the same operation as we did in the previous section, but with `A[BTC]=0.64545455` and the new rates:

$$A_v[X]=R[X]*A_w[X]*A[BTC]$$

| $A_v[BTC]$ | $A_v[USD]$ | $A_v[NVDA]$ |
|---|---| --- |
| ~~0.3~~ -> 0.38727273 | ~~5000~~ -> 7100.00005 | ~~150~~ -> 96.8181825 |

### Derivatives

While our example deals with `USD` and `NVDA` as assets, nothing prevents the creation of any derivative.

For example, we can imagine a `BTC2X` asset whose rate is

$$
RATE[BTC2X] = RATE[USD] * 2
$$

In this case, the `peg consumer` could be exposed to twice the volatility of BTC.

Additionally, it is possible to create assets such as bonds, which provide interest payments to the consumer over time.

## Payments Mechanism

### Receiving payments

Now imagine that `Alice` connects to `Bob` (LSP), who connects to `Carol`.

`Carol` wants to pay for a burrito to `Alice` via Lightning.
As a reminder, here is the desired portfolio composition of `Alice`:

| $A_w[BTC]$ | $A_w[USD]$ | $A_w[NVDA]$ |
|---|---| --- |
| 60%  | 10%  | 30% |

And let's assume the following state

| A[BTC] | $A_v[BTC]$ | $A_v[USD]$ | $A_v[NVDA]$ | B[BTC]  |
|---|---|---|---|---|
| 0.75  | 0.3 | 30,000  | 150 | 0.25 |

And rates

| R[BTC] | R[USD] | R[NVDA] |
|---|---| --- |
| 1 | 100,000  | 1,000 |

`Alice` creates an invoice for `10 USD` (a Lightning invoice of 10/100,000 BTC) to `Carol` for the burrito.

When Carol pays the Lightning invoice, as the payment passes through Bob, the new state will need to be updated.

$$
Value_{btc}=Value/R[Currency] \\
A_v[X]+=Value_{btc}*R[X]*A_w[X]$$

New state:

| A[BTC] | $A_v[BTC]$ | $A_v[USD]$ | $A_v[NVDA]$ | B[BTC]  |
|---|---|---|---|---|
| ~~0.75~~ -> 0.7501 | ~~0.3~~ -> 0.30006 | ~~30,000~~ -> 30,001  | ~~150~~ -> 150.03 | ~~0.25~~ -> 0.2499 |

### Sending payments

Sending payments involves the same operation as receiving payments:

`Alice` first decides on the portfolio composition to use to pay the Bitcoin value to `Carol`, then the $A_v$ balances are decreased proportionally to the chosen portfolio composition.

### Cross-Currency Payments

Notice that with this construct in place, it becomes possible for two individuals, `Carol` and `Alice`, to transfer funds between themselves, using their own local currencies.

The conversion is thus automatically handled by state updates occurring between the LSP and their respective users.

Nothing prevents the LSPs from also having peg relations between themselves, and everything is abstracted away from the perspective of `Alice` and `Carol`.

## Risks and limitations

### Peg relation closure

If the peg cannot be maintained, peers must determine whether they need to close the `peg relation`.

The maximum loss for a peer is the difference between the expected balance and the actual balance of the lightning channel (`unsettled funds`) at the time the `peg relation` is closed.

Following closure, the assets will cease to be pegged to the value of the consumer's portfolio; the only loss is the unsettled funds.

However, the peg can be re-established inexpensively, and the `unsettled funds` from the previous peg can be transferred to the new `peg relation`.

### The stable channel approach

For simplicity, we explained the pegging system through what we call a stable channel, which involves periodic settlements made by sending BTC back and forth between peers engaged in the peg relationship.

The risk with this approach is that, since rates always fluctuate, there are always `unsettled funds`.

This is particularly problematic when `Alice` is not always online, so the differences cannot be settled.

We expect that `Bob` is a well-connected and widely-known entity. As such, one potential solution is for `Bob` to require a refundable deposit from `Alice` to protect against this risk. Another solution is for Bob to terminate the peg relation and request that `Alice` pay for the difference when they establish a new peg relation.

When the difference in unsettled funds becomes too high, either `Alice` or `Bob` may choose to unilaterally terminate the peg.

Breaking a peg relation does not require closing the channel, so re-establishing a peg is a cost-effective operation.

The stable channel approach also suffers from assets that fluctuate significantly over time. For example, an asset representing a bet on a football match will fluctuate too dramatically if a goal is scored, resulting in a significant, sudden and excessive rise in unsettled funds before the peg can be broken.

As such, stable channels are not suitable for betting or over-leveraging.

### Discreet Log Contracts over Lightning approach (DLCs)

Discreet Log Contracts over Lightning might remove the need to send BTC back and forth to settle differences.

This would potentially allow `Alice` to stay offline longer without risking the peg relation breaking.

However, we are not sure at the moment if it would allow `Alice` to easily rebalance her portfolio as described before.

On the other hand, unlike stable channels, DLCs do not suffer from assets fluctuating strongly in price. It isn't possible for a malicious party to take advantage of a sudden change in the price of an asset.

More input on this matter is needed to reach a conclusion.

### Lack of funds

If the channel capacity becomes too low to cover the consumer's assets, the peg can no longer be assured, and the peg relation will break.

## Cost model

### Advanced cost

The costs enumerated in the following section may be impossible for `Alice` to pay if she lacks sufficient Bitcoin in her lightning channel.

Advanced costs are costs advanced by `Bob` that need to be recouped in the future.

These costs can be reflected by a negative expected balance (`A[BTC]`) from Alice.

### Capital cost

We expect `Alice` to not have any balance when the lightning channel is created, so `Bob` needs to provide lightning liquidity to `Alice`.

Since the money used by `Bob` for this purpose could have been used for other, more lucrative endeavors, `Bob` should expect to be compensated for this loss of opportunity.

While it would be theoretically possible for `Alice` to settle with `Bob` every second for the time value of his money, it wouldn't provide a great user experience: `Alice` would see her assets being depleted slowly in near real-time in imperceptible increments.

Instead, we propose a monthly compounding plan with interest settled monthly by updating the state.

The process would be as follows:

First, `Bob` selects a target `APY`, say `2%`.

Convert this APY into an APR compounded monthly:
$$
APY=(1+\frac{APR}{p})^p - 1 \\
APR=((APY+1)^{1/p} - 1)*p \\
APR=((2\% + 1)^{1/12} - 1)* 12=1.98\%
$$

Calculate the average BTC balance on Bob's side over this period and charge the APR over it.

For example:

| 1 to 10 | 11 to 15 | 16 - 20 | 21 - 30 |
|:---:|:---:|:---:|:---:|
|0.7|0.3|0.4|0.45|

First, calculate the average balance:
$$ AverageBalance=\frac{10 * 0.7 + 5 * 0.3 + 5 * 0.4 + 10 * 0.45}{30}=0.5 $$

Then the interest for the number of days in the month:
$$
Interest=AverageBalance * Rate * \frac{30}{365}=0.5 * 2\% * \frac{30}{365}=0.00082192
$$

In this example, Alice will owe `0.00082192 BTC` to Bob at the end of the month.

Note that the balance on Bob's side changes with every transfer, so it may be better to have a granularity down to the second rather than daily.

Also, keep in mind that BTC shouldn't have the same cost of capital as USD. While USD can be invested in T-Bills, with the T-Bill rate representing the cost of capital, BTC appreciates due to the lack of monetary inflation. As such, the cost of capital should be lower.

### Hedging cost

When `Alice` wants to peg her balance to USD, `Bob` ends up with a leveraged position in BTC.

* If `Bob` is also a peg consumer to `Olivia`, he can rebalance his portfolio to have more USD, effectively shifting the risk to Olivia.
* If `Bob` can't shift the risk to somebody else or needs to pay for it, he should be able to charge Alice to compensate.

In the second case, `Bob` could borrow USD and charge Alice the interest rates for it. Alternatively, `Bob` could borrow USD, invest in T-Bills, and charge Alice only the difference between the yield and the interest rate.

This domain is quite complex, and we are not professionals, so please take these suggestions with a grain of salt.

### Service cost

This is the cost of operating the service. It may be a one-time cost charged during channel setup or periodic like the cost of capital.

While this cost could be hidden in the channel cost and the cost of capital, it may be preferable to state it separately for better clarity.

### Channel setup cost

Opening a channel incurs a cost for `Bob`. This cost could be settled out of band or as part of the advanced cost.

## Conclusion

My hope with this essay is to convince you that there is untapped potential for a new kind of asset management without custody.

This is made possible thanks to the high latency of settlement provided by Lightning.

This has the potential to allow anybody to become a de facto broker and provide any derivative without having to assume custody of funds, while severely limiting the potential loss of the consumer.

While intermittent connection may pose a problem for `Alice` by breaking the peg, I do not believe this is a significant issue, as re-establishing it is a cheap operation.