# Somewhat Reliable Methods
Methods that can be arguable at times and may require you to fix multiple problems.

# ✔️ List of Contents
- [World Tick](#%EF%B8%8F-world-tick)
- [Secondary Ticking System](#%EF%B8%8F-secondary-ticking-system)
- [Movement System](#%EF%B8%8F-movement-system-playerauthinputpacket---playermovementpacket)
- [Making Use of Timings Report](#%EF%B8%8F-making-use-of-timings-report)
- [TPS Catch-up](#%EF%B8%8F-tps-catch-up)

### ➡️ Delaying World Tick
__**NOTE: SERVER TICK ≠ WORLD TICK**__

A ticking system is a really great way to have more control over the processes in a server. It enables management of the actions carried out with each tick.

This system could be great, but it might also have unfavorable implications, including performance degradation. Yes, there would be numerous issues without the ticking system, but not every action must coincide with every tick.

One of those things would be the world tick. Now, compare these two results:

(before)
![before](https://user-images.githubusercontent.com/63234276/180412244-695a4f69-54e7-42f6-88d1-017edbf6ab83.png)

(after) \
![after](https://user-images.githubusercontent.com/63234276/180412693-c29d3ac2-606c-44a8-bb0d-ab5c2bb9701c.png)

In light of the aforementioned findings, it is evident that world ticking before my modification used more resources than world ticking after my modification.

How was this change implemented? Simply said, **only tick worlds at a later tick rather than the first** (I have used the tenth tick). The consequences of doing so, such as delayed block updates, delayed block placements and delayed entity updates, are fairly obvious.

You must be **aware of how to rectify these problems**, which will take some time. You must accept this if you want to see such performance improvements. 

- **Efficiency** [✅✅✅]
- **Difficulty** [⭐⭐⭐]
- **Problems** [🔥🔥🔥]
- **Safe** [❓]

### ➡️ Secondary Ticking System
Based on PMMP's server ticking system, specific operation such as world ticking, explosions, set/destroyed blocks, movement updates or entity ticking can be put in a respective queue. 

This system restricts the number of actions that can be performed per tick, which is a great way to avoid lag as it slows down the actions.

An overflow or a memory leak would be among the few problems that could arise. I was able to address this problem by making the limitation proportional to the quantity of actions in the relevant queue. 

Another problem is that it can result in a longer period of lower TPS since the operations in the queue may be delayed for a lengthy time. This is a drawback, although it does stop a sudden drop in TPS. 

- **Efficiency** [✅✅]
- **Difficulty** [⭐⭐⭐]
- **Problems** [🔥🔥]
- **Safe** [❓]

### ➡️ Movement System (PlayerAuthInputPacket -> PlayerMovementPacket)

You might occasionally ponder how a player sends movement packets to PMMP. Prior to being switched to PlayerAuthInputPacket in this [commit](https://github.com/pmmp/PocketMine-MP/commit/292827a311a8792718b6405975518ef923a47475), PMMP listened to PlayerMovementPacket. 

I'm not arguing that utilizing PlayerAuthInputPacket is bad since it really improves the handling of movement as it addresses more issues. However, I believe that utilizing PlayerMovementPacket would improve performance. It does not really affect how players move but this legacy movement system may be neglected in the future.

Since PlayerAuthInputPacket is sent every tick, it **"might cause some performance degradation"**, according to the commit. However, my analysis shows that it significantly influences performance, particularly when there are many players present. 

Compare these two results:

(before)
![before](https://user-images.githubusercontent.com/63234276/180415346-98236092-2110-49e7-9607-314aa352e3a7.png)

(after) \
![after](https://user-images.githubusercontent.com/63234276/180415383-eb7f01b4-7ecb-4408-97a6-2724333137ef.png)

As you can see, **adopting the old movement method again actually significantly boosts performance**. Since PlayerAuthInputPacket delivers many packets every tick, multiplied by the number of players on the server, it is more sluggish. 

I must admit that the handling of the PlayerAuthInputPacket is a lot better now as of 25 July 2022. PMMP has prevented additional movement updates if there has been no change in movement or rotation, however the entire process leading up to the check is significant enough to create delay.

With this change, the movement-related function of PlayerAuthInputPacket would be reversed back to the PlayerMovementPacket.

- **Efficiency** [✅✅]
- **Difficulty** [⭐⭐]
- **Problems** [🔥]
- **Safe** [✅]

### ➡️ Making Use of Timings Report
Timings are a wonderful technique to assess your server's performance. It enables you to identify the server components that are generating lag. Large player or plugin counts are common causes of lag.

Repeated tasks, especially those that run every tick, might contribute to lag. It is a good idea to look at your server's timings to determine if any repeating tasks are generating lag. If so, I suggest that you optimize the code, extend the interval, or remove the task.

Event listeners are potential contributors to lag. Due to how frequently events like PlayerMoveEvent and PlayerJoinEvent are triggered, plugins that listen to such events are probably what's lagging the server. You could make every effort to optimize your code. 

It's challenging to eliminate lag caused by PocketMine-MP itself because you might need to make changes to the source code. You can use some of the techniques in this document to fix lag issues with PocketMine-MP directly.

I personally wouldn't suggest you to make any changes to the source code because it is unlikely to be safe and could result in unpleasant surprises, especially if you are a novice developer. The server ticking system and players are usually at blame for the majority of the lag in PocketMine-MP, which I have both described in this document. 

You may receive a formatted timings report by entering `timings paste` in your server's console. You can then use the link given to analyze the report.

- **Efficiency** [✅✅]
- **Difficulty** [❓]
- **Problems** [❓]
- **Safe** [❓]

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