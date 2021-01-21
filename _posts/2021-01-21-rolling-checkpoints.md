---
layout: post
title:  Rolling checkpoints is security theatre
categories: [Bitcoin]
---

Rolling checkpoints is security theatre. It's all relative to where the node sits on the network graph. Chaos would ensue if there were was ever sustained contention at the fork tip, with nodes all over the world "locking" themselves to random checkpoints. Nodes won't trust the honest chain even after the honest chain overtakes the attacker's chain. 

In addition, for nodes that did not witness the chain divergence in real time (ie, caught up later), it is not possible to prove to them which is the 'honest' chain. New nodes will simply follow the longer (attacker's) chain. If the 'honest' chain eventually becomes longer... new nodes will still be on the attacker's chain.

Proof of social media would be required for everyone to "agree" on a valid "checkpoint", with all nodes having to manually roll back. The nodes would have to manually intervene and presumably issue rpc command invalidateblock prior to where it decided to checkpoint. Nakamoto consensus is supposed to be about trustless automation. The 10-block rolling checkpoint is just plain wrong.

Bitmex also had a blog post evaluating rolling checkpoints. They point out that if an attacker releases their 10-block secret chain immediately following a newly found (honest) block (which not all miners have yet seen).. some honest miners may see the attacker's chain as a 9-block reorg.. and thus accept (and checkpoint) it.

BCH no longer follows the "longest proof-of-work chain as proof of what happened while they were gone". A coin using the same hash function as a larger coin simply has to accept the risk of being attacked (and defend it). This is a variation on Nakamoto consensus. The fact that BCH still exists means alternative PoW chains are seemingly possible, albeit with risks involved.
