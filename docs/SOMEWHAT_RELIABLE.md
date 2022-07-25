# Somewhat Reliable Methods
Methods that can be arguable at times and may require you to fix multiple problems.

# ✔️ List of Contents
- [World Tick](#%EF%B8%8F-world-tick)
- [Movement System](#%EF%B8%8F-movement-system-playerauthinputpacket---playermovementpacket)
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

How was this change implemented? Simply said, **only tick worlds at the tenth tick rather than the first** (it doesn't have to exactly be on the tenth). The consequences of doing so, such as delayed block updates, delayed block placements and delayed entity updates, are fairly obvious. You must be **aware of how to rectify these problems**, which will take some time. You must accept this if you want to see such performance improvements. 

- **Efficiency** [✅✅✅]
- **Difficulty** [⭐⭐⭐]
- **Problems** [🔥🔥🔥]
- **Safe** [❓]

### ➡️ Movement System (PlayerAuthInputPacket -> PlayerMovementPacket)
**UPDATE:** I must admit that this [commit](https://github.com/pmmp/PocketMine-MP/commit/01ca14c314f180441343bbdf6cff611064ebe330) along with other [commits](https://github.com/pmmp/PocketMine-MP/commits/5d9f78303726a6ba58cdda8231976f57a54a73c4) have helped to partially fix the problem. It does not, however, always stop or prevent initial sending of movement changes. I don't think that the changes made were an optimal one given that `handleMovement()` already checks for movement. 

You might occasionally ponder how a player sends movement packets to PMMP. Prior to being switched to PlayerAuthInputPacket in this [commit](https://github.com/pmmp/PocketMine-MP/commit/292827a311a8792718b6405975518ef923a47475), PMMP listened to PlayerMovementPacket. 

I'm not arguing that utilizing PlayerAuthInputPacket is bad since it really improves matters because it addresses more issues. But I believe that utilizing PlayerMovementPacket would greatly improve performance. It will affect how players move and using the old movement system is not always a good thing!

Since PlayerAuthInputPacket is sent every tick, it **"might cause some performance degradation"**, according to the commit. However, my analysis shows that it significantly influences performance, particularly when there are several players present. 

Compare these two results:

(before)
![before](https://user-images.githubusercontent.com/63234276/180415346-98236092-2110-49e7-9607-314aa352e3a7.png)

(after) \
![after](https://user-images.githubusercontent.com/63234276/180415383-eb7f01b4-7ecb-4408-97a6-2724333137ef.png)

As you can see, **adopting the old movement method again actually significantly boosts performance**. Since PlayerAuthInputPacket delivers many packets every tick, multiplied by the number of players on the server, it is more sluggish. Yes, PMMP has prevented additional movement updates if there has been no change in movement, however the entire process leading up to the check is significant enough to create delay.

With this change, the movement-related function of PlayerAuthInputPacket would be reversed. But is it worth it?

- **Efficiency** [✅✅]
- **Difficulty** [⭐⭐]
- **Problems** [🔥]
- **Safe** [✅]

### ➡️ TPS Catch-up
This is entirely different from [Tick Skipping](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/UNRELIABLE.md#%EF%B8%8F-tick-skipping). When the server is lagging behind in some ticks, the server will **tick even faster until its back on track**. This is a way to make the server act as though it is running late for school.

- **Efficiency** [✅]
- **Difficulty** [⭐⭐⭐]
- **Problems** [🔥]
- **Safe** [❓]

<div align="right">
  <p>Done reading this section?</p>
    <a href = "https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/UNRELIABLE.md" target = "_self">Unreliable Methods ➡️</a>
</div>