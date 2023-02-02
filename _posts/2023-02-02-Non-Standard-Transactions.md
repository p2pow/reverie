---
layout: post
title:  Pools that include megabytes of non-standard transactions are at increased risk of losing block races
categories: [Bitcoin]
---

It is the best interest of all miners (and the damn pools) to do the following -

- Use libbitcoinconsensus (part of Bitcoin Core)
- Use BIP152 compact blocks (part of Bitcoin Core)
- Consider using the many other heavily-optimised features from the devs (Bitcoin Core)

TL;DR, almost certainly 99% of miners/pools are using recent releases of Bitcoin Core. Miners/pools are part of a larger dynamic set of miners. They are all incentivised to keep consensus with each other post-haste, or risk having their blocks dropped. Blocks can be dropped for any number of reasons, including -

- invalid formatting
- slow propagation

Invalid formatting is an easy fix - use libbitcoinconsensus (usually Bitcoin Core). There is no "finality" in Bitcoin, only probabilistic finality. Consensus is tricky business.

Slow propagation can be fixed by the following -

- low latency internet connection (receive other blocks quickly, and push your solved blocks out quickly)
- use BIP152
- don't include non-standard transactions

Bitcoin Core will not relay certain types of transactions. That said, if you can incentivise pools or harness sufficient hash power to mine a block with non-standard fees.. the protocol will not stop you. However, there are consequences..

Recall that 99% of miners are also using BIP152 (Compact Blocks). Last I checked, most new blocks nowadays only require ~20KB of data to propagate. This is due to nodes having similar mempools. BIP152 takes advantage of the fact that most nodes already have the transactions and their ids, and are able to "compress" the block down.

Early versions of the reference Bitcoin client would push the full block (e.g., potentially 1MB) out to *everyone* in the broadcast network. Block races early in Bitcoin's history were significantly higher compared to today. There is significant literature out there on this topic.

Pools pushing out 4MB of (previously unknown) transactions run the risk of a higher stale rate (losing to a block race). The reason for this is that the miner needs to push the entire 4MB of data out to the network (because no one else is aware of it yet). While this is happening, another miner might solve a competing block at the same height. This alternate block can propagate faster around the network at ~20KB. Pools engaging in such activity might need to price in such risks when they price these out-of-band transactions. This could be significant considering they also lose the block reward if their block is dropped.

There is another problem though. Many pools currently engage in "SPV mining" - they start empty-block mining on top of newly-solved block headers without fully validating the block first. This is non-standard behaviour - Bitcoin Core will not propose a block template on top of an unvalidated block header. Pools are using some sort of hack to accomplish this. We don't know how many pools are engaging in this practice, or under what conditions. This is not desirable as they have to forgo fees and only claim the block reward. Even worse - the block header the are mining on top of might even fail validation, thus invalidating their own work! Yuck. SPV-mining might be disincentivised in future as the block reward relative to fees declines.

There is a reason why Bitcoin Core is the reference implementation. The Bitcoin "spec" is a moving target. Bitcoin Core *is* the spec. It is difficult to put the "spec" into words. Words don't always translate to logic. The devs have been ruminating over attack vectors for well over a *decade*. We all benefit as a result.

The block space market is a real thing. Bitcoin's block space provides proof-of-publication and an ordering of events. Solving the double-spending problem is simply the primary use case. The protocol cannot stop other usage. The reference implementation can only discourage it.

There is no need to call for censorship or other nonsense. Having miners and pools coordinate outside of Nakamoto Consensus is a very dangerous thing. If people want to pay for other stuff in the blockchain, let them. Fees = security. Bitcoin needs fees in the long term. It is unfortunate that non-standard data in witness inputs gets a 75% discount over something like the more appropriate OP_RETURN, but nothing is perfect. Perhaps this can be fixed somehow too.
