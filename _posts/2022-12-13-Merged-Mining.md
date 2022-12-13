---
layout: post
title:  Merged mining is flawed
categories: [Bitcoin]
---

An entity that has significant hash rate (a farm of ASICs) might be willing to solo mine Bitcoin. For example, perhaps they expect to mine an average of 1 block per week. They are willing to wear the variance (could be 2 or 3 blocks in a week, or perhaps none!). They know this is healthy for the network (they validate, instead of pools). They also don't need to pay pool fees.

Imagine there are 100 small-cap altcoins all merge-mined with Bitcoin. Daily rewards for each are small.. say ~1% each compared to Bitcoin. Combined, however, they are worth as much as Bitcoin. If the solo miner ignores the 100 altcoins, he forgos 50% of revenue. Therefore, he is forced to run and maintain 100 nodes to remain profitable (vs someone else who will maintain all 100 altcoins).

But who has the resources and skillset to maintain 100 separate nodes? The answer = pools. BIG pools. Imagine if each altcoin had 100MB worth of block data every 10 mins! That's ~166Mbps! 1.4TB day of new disk space required. Remember, they can't prune! They're validating and maintaining the state of all 100 chains. The end result? Only very big pools validate. This would likely lead to even more pool centralisation compared to what we currently have. This scenario was pointed out by Peter Todd at some point.. years ago.

Smaller miners don't run nodes or validate.. they simply point their Bitcoin ASICs (with closed firmware) directly at the big pools. They only care about variance (short term self-interest). They are not validating as they are not running bitcoind. They are placing the protocol at risk by actively choosing the biggest pools to achieve lower variance.

There are many other problems with merge-mining. Just because you are mining the main parent "honestly", does not mean you have to mine the child chains honestly. Miners could collude and re-org the small-cap altcoins etc.

There is a shortcut to lowering overheads costs.. miners could header-mine all 100 altcoins.. resulting in empty blocks for all. No requirement to maintain state or listen for transactions. Only listen for headers (e.g., Bitcoin's headers are only *1 bit* per second). Altcoins have no fees anyway. Miners can just collect the inflation (block reward).

TL;DR - Merged-mining increases centralisation. It is also a de facto block size increase on the main parent (as the miners now also have to validate all child chains). It poses a systemic risk to the parent chain.
