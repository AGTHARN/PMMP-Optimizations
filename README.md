# AGTHARN's Optimization Theories
[![Hits](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations.svg?view=today-total&style=flat-square&label=views)](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations/)

## PLEASE READ!
**This is NOT MEANT FOR ANY PRODUCTION PURPOSES! All of these methods can cause problems for your server, especially if your server requires PvP action. It is indeed undeniable that PlayerAuthInput is way better than PlayerMovement. I only made this so as to document my findings after my experiments on PMMP. It was something I never intended to have negative comments about as this was never meant to be applied to PMMP's repository. Even if you used these methods, you MUST accept all the consequences involved! I will not be reponsible due to how this was documented only for my friends! Overall, all these methods are entirely argueable.**

## Why I wanted to experiment with these methods?
I myself run a PocketMine-MP (PMMP) server, and I've been dealing with the same problem since the server's inception - lag brought on by high player counts rendering PMMP servers virtually unplayable.

Many individuals have frequently used the argument that the problem is with the server's plugins or that PMMP is single-threaded. That's not totally true, but it's comparable.

One day, I pondered how much I could change PMMP in order to push it as far as it could go. The experiments I have produced offer fantastic performance enhancements.

**Due to the player count, the findings may be skewed, however if necessary, you can perform your own computations.**

| Before Modifications |
| ----------- |
| ![before](https://user-images.githubusercontent.com/63234276/180207286-eb69ac8e-697e-4e0d-903d-bdaa6a023248.png) |

| After Modifications |
| ----------- |
| ![after](https://user-images.githubusercontent.com/63234276/180207462-6a27702e-25f9-4731-bc7e-11b63d17b5d4.png) |

The modifications I've made are ones that a skilled developer could do with ease. Since they are not the finest, I do not intend to release a fork of these modifications. However, I'd like to see somebody else give it a go.

# ✔️ List of Contents
- [World Tick](#%EF%B8%8F-world-tick)
- [Movement System](#%EF%B8%8F-movement-system-playerauthinputpacket---playermovementpacket)
- [Unnecessary Entity Updates](#%EF%B8%8F-unnecessary-entity-updates)
- [Tick Skipping](#%EF%B8%8F-tick-skipping)
- [TPS Catch-up](#%EF%B8%8F-tps-catch-up)

### ➡️ World Tick
__**SERVER TICK ≠ WORLD TICK**__

A ticking system is a really great way to have more control over the processes in a server. It enables management of the actions carried out with each tick.

This system could be great, but it might also have unfavorable implications, including performance degradation. Yes, there would be numerous issues without the ticking system, but not every action must coincide with every tick.

One of those things would be the world tick. Now, compare these two results:

(before)
![before](https://user-images.githubusercontent.com/63234276/180412244-695a4f69-54e7-42f6-88d1-017edbf6ab83.png)

(after) \
![after](https://user-images.githubusercontent.com/63234276/180412693-c29d3ac2-606c-44a8-bb0d-ab5c2bb9701c.png)

In light of the aforementioned findings, it is evident that world ticking before my modification used more resources than world ticking after my modification.

How was this change implemented? Simply said, **only tick worlds at the tenth tick rather than the first**. The consequences of doing so, such as delayed block updates, delayed block placements and delayed entity updates, are fairly obvious.

You must be aware of how to rectify these consequences, which will take some time. You must accept this if you want to see such performance improvements. 

Is it worth? Yes.

### ➡️ Movement System (PlayerAuthInputPacket -> PlayerMovementPacket)
You might occasionally ponder how a player sends movement packets to PMMP.
Prior to being switched to PlayerAuthInputPacket in this [commit](https://github.com/pmmp/PocketMine-MP/commit/292827a311a8792718b6405975518ef923a47475), PMMP listened to PlayerMovementPacket. 

I'm not arguing that utilizing PlayerAuthInputPacket is bad since it really improves matters because it addresses more issues. But I believe that utilizing PlayerMovementPacket would greatly improve performance.

Since the packet is sent every tick, it "might cause some performance degradation," according to the commit. However, my analysis shows that it significantly influences performance, particularly when there are several players present. 

Compare these two results:

(before)
![before](https://user-images.githubusercontent.com/63234276/180415346-98236092-2110-49e7-9607-314aa352e3a7.png)

(after) \
![after](https://user-images.githubusercontent.com/63234276/180415383-eb7f01b4-7ecb-4408-97a6-2724333137ef.png)

As you can see, **adopting the old movement method again actually significantly boosts performance**. Since PlayerAuthInputPacket delivers many packets every tick, multiplied by the number of players on the server, it is more sluggish. Yes, PMMP has prevented additional movement updates if there has been no change in movement, however the entire process leading up to the check is significant enough to create delay.

With this change, the movement-related function of PlayerAuthInputPacket would be reversed. But is it worth it? Yes. 

### ➡️ Unnecessary Entity Updates
On my server, minions are present, and players enjoy piling them up. There are more entities to update/tick when more minions are placed. The performance of the server may suffer greatly as a result. 

Therefore, I removed pointless updates from the entity class's `onUpdate()` and `entityBaseTick()` functions. For instance, I don't anticipate that minions will have any motion so I had that removed from its updates. **Performance can already be enhanced just by eliminating unnecessary updates**. 

Is this worth it? Yes.

### ➡️ Tick Skipping
Actions on the server are slowed down along with lag. There is little you can do to prevent delays, but there are a few ways to partially resolve this.

Lag can cause the server to slow down by several ticks, which makes the server stagnate. Rather than the server waiting for a specified tick to be reached so that actions are performed on that tick. **We ignore the ticks that have been delayed for too long and consider it as lost**.

I am aware that skipping ticks isn't a great idea, however, it may provide room for other actions. 

Is this worth it? __**Not really and not recommended.**__

### ➡️ TPS Catch-up
This is entirely different from Tick Skipping. When the server is lagging behind in some ticks, the server will **tick even faster until its back on track**. This is a way to make the server act as though it is running late for school.

Is this worth it? Haven't tried but it is possible.
