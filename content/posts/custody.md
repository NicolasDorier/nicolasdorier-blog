+++
title = "Erosion of the Meaning of Custody"
date = 2024-12-03T12:46:00+09:00
image = "/images/custody.webp"
images = ["/images/custody.webp"]
+++

## Introduction

The loose use of the term custody is, in my opinion, very dangerous. If you strongly value the freedom Bitcoin provides, you should fight to preserve its meaning. Broadening its definition risks inviting regulations that could eventually ban non-custodial solutions.

We’ve seen this pattern before: first, a law targeting terrorists, then a gradual expansion of the definition until, one day, someone saying something offensive online is labeled a terrorist under the new terms.

Interestingly, this push to broaden the definition of custody isn’t even coming from regulators—it’s being driven by overly zealous protocols attempting to define what a `Layer 2` solution is, hoping to associate themselves with the success of the Lightning Network.

So, here it is: a strict, uncompromising definition of custody.

## The definition

Imagine going to a shopping mall. It's your wife's birthday, and she wants to buy a new bag. You decide to pay, you take your wallet from your pocket then hands out the cash to the cashier.

In this case, it’s obvious that no one would claim your wife is a custodian. Why? Because you **CAN** still use your wallet without needing her permission.

Now, consider a different scenario:
You don’t want to carry your wallet, so you hand it to your wife, who puts it in her bag. Later, you pass by a store and see a bottle of wine you’d like for tonight. You ask your wife for the wallet and then use it to pay the cashier.

Here, your wife is undeniably a custodian. You **CAN'T** use your wallet without first asking her. The fact that she might always agree to give it back is irrelevant. The key point is that you **CAN'T** spend without her consent. This lack of independent control means there is no `unilateral exit`, as Bitcoiners would put it.

As [Calle wrote](https://x.com/callebtc/status/1863621499057291640):

>  Either you have unilateral exit to the chain or it's custodial, sometimes a sugar-coated version of it.

Unilateral exit implies non-custody. Non-custody implies unilateral exit. Those are synonyms.

Those who use the term `Layer 2` to include custodial solutions are essentially implying that your Kraken account is also a `Layer 2`. This dilutes the term to the point of rendering it meaningless, much like the term `blockchain`, which became a red flag after being misused and overhyped by shitcoiners for years.

There is no such thing as `semi-custody`.

## There is no ambiguity

[Lightcoin replied to Calle](https://x.com/lightcoin/status/1863693594629898294):

> what do you call a statechain, which has unilateral exit and the operator can collude with a prior key holder to steal?

To which [Calle answered](https://x.com/callebtc/status/1863703277839266176):

> Non-custodial.
> Similarly LN force close with mempool pinning attack or bad fee spike etc. 
> My pedantic definition includes an "almost always" for unilateral exit.

I strongly disagree with this response. While the conclusion is correct, the reasoning is not and would lead to a diluted meaning of custody.

We need to address the two points separately:
1. Protocols allowing third-party collusion to steal funds
2. Protocols that may fail under external circumstances (high fee spike, pinning attacks)

## About third party collusions

What about protocols like `Statechains` or even `Ark`? Are they really non-custodial if collusion might lead to the theft of funds?

The answer is an uncompromising **YES**.

Let’s consider a real-world analogy: You know that Netflix can raise its subscription price without asking your permission. Every month, you continue paying unless you cancel. They don’t need your consent to withdraw funds once you’ve subscribed.

Would anyone claim that Netflix is a custodian because it has the ability to charge your account?
Is there a unilateral exit? No, there isn’t. Of course, you can ask Netflix to stop charging your account or instruct your bank to block payments, but you **CAN'T** stop it without asking someone.

If there is no unilateral exit, by our definition, there must be a custodian. The subscription involves three parties: you, your bank, and Netflix. There’s no unilateral exit because custody exists, and the custodian is your bank.

> Once again: When there is no unilateral exit, there is custody. If there is custody, there is no unilateral exit.

Now back to `Bitcoin`. If a protocol like `Statechains` or `Ark` allows theft through collusion as part of its security model, does that imply custody?
No, because unlike the Netflix example above, there is a unilateral exit. Therefore, there cannot be a custodian.

## About external circumstances

Unilateral exit might become impossible due to factors like:
* Server downtime
* Network congestion
* High fees
* Attacks (e.g., mempool pinning)
* Accidental key loss (e.g., your cat erasing keys)


Let’s revisit the shopping mall analogy:

You have your wallet in your bag and decide to store the bag in a locker at the mall, keeping the key. Later, you try to pay at a shop but realize your wallet is in the locker—and worse, you've lost the key.

At this moment, the coin locker owner effectively becomes a custodian. You now depend on them to grant you access to your wallet. Without their help, you cannot retrieve your funds. Regardless of the security protocols in place, this situation is functionally no different from relying on a bank’s vault.

The loss of unilateral access transforms the relationship. Custody now exists because you no longer have the ability to act independently.

**Fundamentally**, non-custody means the user retains full sovereignty over their funds. This inherently includes the ability to transfer or lose that sovereignty, whether voluntarily or not. Even mechanisms like covenants cannot entirely prevent this, as sovereignty implies ultimate control, including the choice (or mistake) to relinquish it.


Back to Bitcoin: While a protocol may be non-custodial, circumstances can still reintroduce custody. This stems from the very nature of ownership.

The only thing we can objectively evaluate is whether the protocol itself is non-custodial. As we’ve established, so long as a unilateral exit exists, the protocol is non-custodial. External circumstances should not factor into this determination, as ownership is always alienable by definition.

As a libertarian would argue, the only truly inalienable ownership is over your body and will, but I disgress.

## Custodial implementations

As we’ve seen, it isn’t possible to prevent the use of a non-custodial protocol in a custodial way, due to the very nature of ownership.

An interesting argument compares a custodial implementation (`Wallet of Satoshi`) to a non-custodial one (`Phoenix`). The claim is that, in both cases, if the servers behind `Phoenix` or `Wallet of Satoshi` disappear, the funds become unspendable. Thus, `Phoenix` is argued to be as custodial as `Wallet of Satoshi`, even though it stores keys locally on your device rather than on a server.

It might be tempting to counter this argument by pointing out that `Phoenix` allows you to back up the seed or channels. However, I believe this is the wrong approach. If `Phoenix` were the only implementation capable of interpreting those backups, and it became inaccessible, users would still be unable to recover their funds.

The correct argument lies in the **possibility** of a unilateral exit, even if the servers go down. Even if Phoenix didn’t provide an export option for backups, as long as all necessary data remains on the user’s phone, it is still `POSSIBLE` to achieve a unilateral exit. This distinction is critical, and it’s why I’ve emphasized the word **CAN** in earlier examples.

The capacity for unilateral exit is what defines non-custody. Whether the user has the technical knowledge to execute it is irrelevant—what matters is that they can, or that someone else could assist them in doing so.

## Conclusion

I hope I’ve successfully made the case for a strict and uncompromising definition of custody.

With this article, I hope to encourage you to confidently call out anyone misusing terms like `custody` or `Layer 2`. Attacks on language often pave the way for broader confusion or manipulation, so it is crucial to stand your ground and defend clarity.

Being aware of the security model of those protocol is still important, because as we have said here, non-custody doesn't mean that you can't lose control of the funds. But this is another big topic, and I only wanted to cover the definition of custody.