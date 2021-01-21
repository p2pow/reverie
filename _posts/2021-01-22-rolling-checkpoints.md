---
layout: post
title:  Rolling checkpoints is security theatre
categories: [Bitcoin]
---

Rolling checkpoints is security theatre. It's all relative to where the node sits on the network graph. Chaos would ensue if there were was ever sustained contention at the fork tip, with nodes all over the world "locking" themselves to random checkpoints. Nodes won't trust the honest chain even after the honest chain overtakes the attacker's chain.

Proof of social media would be required for everyone to "agree" on a valid "checkpoint", with all nodes having to manually roll back. The nodes would have to manually intervene and presumably issue rpc command invalidateblock prior to where it decided to checkpoint. Nakamoto consensus is supposed to be about trustless automation. The 10-block rolling checkpoint is just plain wrong.

BCH no longer follows the "longest proof-of-work chain as proof of what happened while they were gone". A coin using the same hash function as a larger coin simply has to accept the risk of being attacked (and defend it). This is a variation on Nakamoto concensus, but the fact that BCH exists, means alternative PoW chains are seemingly possible, albeit with risks involved.
