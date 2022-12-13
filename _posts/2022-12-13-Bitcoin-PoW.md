---
layout: post
title:  Bitcoin/PoW can maintain consensus @ ~2bps
categories: [Bitcoin]
---

<center><a title="User Thomas H. White on en.wikipedia, Public domain, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Thesos.jpg"><img width="340" alt="Thesos" src="https://upload.wikimedia.org/wikipedia/commons/1/10/Thesos.jpg"></a></center>

Bitcoin/PoW can maintain consensus @ ~2bps. That's two BITs per second.

Scenario: nuclear apocalypse. The internet is down. How can the network maintain consensus?

Fortunately, PoW allows for block header propagation via untrusted intermediaries. It cannot be tampered with. Further, PoW verification is self-evident and independent of state [1].

Bitcoin's block headers are 80 bytes in size (640 bits). This equates to 1.066 bits per second (over 10 minutes). If miners temporarily only collected the block reward (no transactions), bandwidth requirements could be significantly reduced [2]. In theory, this might be as low as 2bps with a heavily optimised doomsday protocol. Such speeds could even be sent via morse code! The ionosphere is known to be able to bounce signals almost halfway around the world! Who needs Starlink?

Granted, the above scenario might not work as well in a future where block rewards are much lower (relative to fees). Perhaps the telegraphers could even include a transaction or two? Still, food for thought.

PoW FTW!

[1] You might not know the state of the blockchain initially. However, you know that *someone* decided the block header was valuable enough to perform a lot of *work* on it. A double SHA-256 hash is applied to the block header (the pre-image). The PoW target ("difficulty") is defined in the block header itself (the 4-byte "Bits" field). This allows for PoW to be verified in *isolation*.. independent of blockchain state! This is, of course, what Bitcoin Core uses for its initial headers-only sync.

PoW can be thought of "paying" for its own postage as block headers propagate around the network. PoW *cannot be censored* as Bitcoin uses a broadcast network. Among a sea of dishonest nodes, it only takes a *single* honest node to help you discover the most-accumulated chain of work. This is a form of [Sybil-resistance](https://en.wikipedia.org/wiki/Sybil_attack).

[2] For example, BIP 152 (compact blocks) allows for the coinbase/generation transaction to be prefilled. This allows for the miner's payout address and any extra nonces etc. BIP 34 also needs to be considered.

[https://twitter.com/p2pow](https://twitter.com/p2pow)
