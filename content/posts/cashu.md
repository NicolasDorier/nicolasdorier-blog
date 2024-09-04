+++
title = "The Rise of E-Cash: Maybe you don't need a Blockchain"
date = 2024-09-04T10:23:00+09:00
image = "/images/Exchange-Token-Header.webp"
images = ["/images/Exchange-Token-Header.webp"]
+++

## The Enterprise Blockchain era

![Enterprise Blockchain](/images/Corporate.webp)

I was involved in Bitcoin during 2016-2017. For those who weren't there or have forgotten, it was a time when every giant corporation wanted to include ~AI~ Blockchain in everything they were doing, even when it didn’t make sense.

Shareholders wanted to ride the next wave and wondered whether to sell stocks in "boring" companies to jump into ~AI~ Blockchain. Executives, loaded with stock options or bonuses tied to the stock price, were pressured to include the next cool thing in the company and passed the orders down to managers, who had to do something—anything, really, as long as it involved ~AI~ Blockchain.

There I was, working proudly in Blockchain (before the term lost its meaning), meeting with managers of financial institutions who suddenly took an interest in what a nerd like me was doing.

It was very clear that what excited me (Self-Sovereignty) wasn’t on the agenda of most of those managers, who just needed a narrative to sell to executives. From their perspective, executives decided something was cool, and they were as puzzled as I was about why they should care, but they had to find something to show for it.

Equipped with a hammer, in search of a nail, it became clear to me that they didn’t really need anything that Blockchain was built for. In an effort to fit a square peg into a round hole, they invented the concept of `Enterprise Blockchain`, which was actually no different from any ledger system that had existed since Mesopotamian merchants' clay tablets or an Oracle database. They decided the Enterprise Blockchain would be controlled by themselves. Every company with its own blockchain! Wow!

Some companies, like Blockstream, tried to make sense of it by proposing that at least a group of businesses could share the consensus, which might add some logic to the idea of Enterprise Blockchains. While this didn’t interest me, it attempted to restore some reason for using a blockchain in the first place: a way to reach consensus without a central party.

But no, most companies didn’t want any of that. They wanted **THEIR OWN blockchain**... sigh...

Having your own Blockchain is one thing, having ~somebody~ anybody to use and build on it is another. Billions of dollars wasted on Proof of Concepts later, the idea migrated to tokenization on a Blockchain which already had people on it, specifically on Ethereum.

## The Ethereum Token era

![Ethereum Era](/images/Unicorn.webp)

What a great idea! No need to maintain an in-house ledger when you can track assets on a blockchain. Sure, you can do the same with an in-house ledger, but then those assets can't be easily exchanged or traded for PEPE coins on ETH, or ride the wave of DApps developed by the crypto community. Fair enough, I’m not a fan of shitcoins, but I can't deny the appeal.

Ethereum's big selling point is that you don't have to be a genius to make a DApp, which led to a Cambrian explosion of ideas. Most of these were terrible, but I won't blame them. This is how evolution works: many ideas will fail, but a few great ones will emerge. In an evolutionary context, quantity often trumps quality—or perhaps it's better to say that quality eventually emerges from quantity. It's because so many people are born every day that we occasionally get a new Einstein.

Everything would have been great if this Cambrian explosion of bad ideas hadn't had the externality of polluting a data structure shared by all network participants—forever.

While almost nothing truly stuck from all those experiments, I must admit there were some discoveries along the way:
* The need for exchanging assets on unregulated and non-custodial exchanges is real
* Issuers want to control the asset without controlling the ledger.
* Issuers like that they don’t have to build infrastructure for their token themselves. They can just ride along with what DApp developers are doing for free and shift the blame when things inevitably go wrong.

With these insights internalized, and with it becoming clear that Bitcoin is the only blockchain with any long-term vision and traction, some decided to take these observations and apply them to Bitcoin.

## The Bitcoin Token era (version 2.0)

![Bitcoin Token](/images/WhatTheHellIsThis.jpg)

While transferring tokens on Bitcoin is a very old idea that was in production before (e.g., Counterparty, Spells of Genesis), it has recently resurfaced. The main difference now is the experience gained from Ethereum between 2017 and today in terms of infrastructure, services, and the social dynamics surrounding this domain.

This renewed interest has led to the development of new protocols on top of Bitcoin, such as `BRC20` and `Taproot Assets`. Some members of the Ethereum community became excited to find a new "wild west" to conquer, armed with the lessons learned on Ethereum but without the same level of competition. They began building infrastructure, services, and communities around these ideas. This effort is on a different level compared to when Counterparty existed, as there are now far more developers in the crypto space than before. Additionally, what works and what doesn’t have been more or less established on Ethereum and can now be re-applied on Bitcoin.

Meanwhile, there's also an attempt to combine successful experiments on Bitcoin (like Lightning) with successful experiments in tokens, using protocols like `Taproot Assets`.

At the same time, freed from the enterprise blockchain era, some developers were finally able to focus on what really matters: you don’t necessarily need a Blockchain. This realization has led to the emergence of e-cash projects such as `Cashu`, `Fedimint`, and `Webcash`. I believe this is a fundamental observation that might eventually move digital assets out of the realm of blockchains and into bearer assets.

## The e-cash era

![e-cash](/images/Exchange-Token.webp)

Satoshi wanted to create an e-cash that cannot be controlled—hence, the Blockchain. But what if you want an e-cash that can be controlled? In that case, you don’t need a Blockchain.

The three key advantages discovered on Ethereum don’t actually require a blockchain. What’s needed is a common protocol, a compatibility layer.

* **With a common protocol**: An unregulated and non-custodial exchange can be built.
* **With a common protocol**: Issuers can define the rules for the emission and redemption of their tokens.
* **With a common protocol**: Issuers don’t need to build the infrastructure and services interacting with their token. They can leverage the work of open-source developers and shift the blame if something goes wrong. (No sarcasm here—this is a genuine need.)

These advantages are real, but there are additional benefits:

* **Cheap transfers**: Without a blockchain, there are no spam issues or fees.
* **Great UX**: No block confirmations, no congestion.
* **Cambrian explosion of ideas**: The protocol is simpler than blockchain, lowering the barrier to entry for exploring new ideas.
* **No externalities**: Bad ideas don’t leave any trace on a shared data structure.

When you think about it, what you need for digital assets with centralized issuers isn’t a blockchain but a compatibility layer.
Such layer seldom emerge from established players, and instead really thrive on Open Source, due to the ease of developing on top of it without permission. (See TCP/IP's history)

There are three types of ledger technology with which we track assets: Bearer assets, centralized ledgers, and Blockchains.

In our modern life, with the ability to communicate instantly over long distances, bearer assets have taken a backseat to centralized ledgers. E-cash is attempting to bring bearer assets back to the forefront of technological advancement.

I’m not a prophet, but e-cash protocols seems to be ground zero for a new Cambrian explosion of money experiments, particularly in the domain of `Private Money`.

I define `Public Money` as money that can be used by a wide community of people—examples include fiat money, Bitcoin, and stablecoins.

`Private Money`, on the other hand, is an asset used in a limited area, for a limited time, by a limited group of people, or for a specific purpose:
* Gift cards
* Loyalty points
* Gift points
* Area-limited money
* Event-limited money (e.g., food tickets at a conference)

These areas are easier to navigate from a regulatory perspective and are a natural fit for bearer e-cash, as they typically involve low amounts that wouldn’t be economical to exchange over a blockchain or centralized ledger.

I believe these types of money have been underserved because they couldn't make use of blockchain as a compatibility layer due to its cost relative to the value exchanged.

E-Cash isn't Bitcoin, and it doesn't need to be to remain appealing. However, formalizing some basic integration with Bitcoin in the wallet's user experience—such as the ability to easily purchase tokens through Bitcoin to the mint—reinforces Bitcoin's role as the only true global money. **Bitcoin uses the blockchain so other money doesn't have to.**.