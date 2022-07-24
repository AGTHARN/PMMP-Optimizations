# Reliable Methods
Methods that should be safe as long as you have an idea of what you're doing.

# ✔️ List of Contents
- [Asynchronous Explosion Calculator](#%EF%B8%8F-asynchronous-explosion-calculator)
- [Unnecessary Entity Updates](#%EF%B8%8F-unnecessary-entity-updates)
- [XP Orbs](#%EF%B8%8F-xp-orbs)

### ➡️ Asynchronous Explosion Calculator
On PMMP, the explosion computation is not asynchronous. Given that you would be dealing with concurrent calculations, this assignment may prove to be difficult.

**For this method, simply put, the computation of explosions ought to be done on a separate thread from the main thread**. You would have issues if there were multiple explosions at the same chunk. For instance, it would be challenging to modify a chunk given how many computations were still being performed on it.

There are, of course, a few approaches to resolving this problem, such as a queue where explosion calculations are queued in accordance with the chunk(s) they blast. Another approach is to stop the modification of chunks while a new explosion is being computed. 

- **Efficient** [✅✅]
- **Difficulty** [⭐⭐⭐]
- **Problems** []
- **Safe** [❓]

### ➡️ Unnecessary Entity Updates
On my server, minions are present, and players enjoy piling them up. There are more entities to update/tick when more minions are placed. The performance of the server may suffer greatly as a result. 

Therefore, I removed pointless updates from the entity class's `onUpdate()` and `entityBaseTick()` functions. For instance, I don't anticipate that minions will have any motion so I had that removed from its updates. **Performance can already be enhanced just by eliminating unnecessary updates**. You may do the same for any entity which you do not expect to be moving such as NPCs most of the time.

- **Efficient** [✅✅]
- **Difficulty** [⭐]
- **Problems** []
- **Safe** [✅]

### ➡️ XP Orbs
As XP orbs are frequently used by servers, they are unquestionably a must for PMMP servers. But what if someone had left hundreds of XP orbs on their base in an effort to slow the server? If you haven't tried it yet, it significantly increases lag because these XP orbs must constantly move in the direction of a player. Without a doubt, these XP orbs will ultimately de-spawn, but does it address the lag issue at its root? Like any other entity, XP orbs have motion updates that create lag when there are a lot of them present. 

**The ways of solving this issue will remove features!**

The ****motion updates on XP orbs can be eliminated**** as a potential solution to this problem. However, I believe it would be much better if you allowed your players the autonomy of being able to produce XP orbs.

There is also the option to **split XP to only ONE orb**. For instance, using a Bottle of Enchanting would cause the XP to be divided into many orbs, which is a default behavior. I do not believe that this is necessary, though, unless you are concerned that the XP orb would disappear for whatever reason.

The final option would be to prevent the spawning of any XP orbs with Bottle of Enchanting. As an alternative, it would **immediately go to the player's XP level**.

- **Efficient** [✅✅]
- **Difficulty** [⭐]
- **Problems** [🔥]
- **Safe** [✅]