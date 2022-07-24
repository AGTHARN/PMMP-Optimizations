# Reliable Methods
Methods that should be safe as long as you have an idea of what you're doing.

# ✔️ List of Contents
- [Asynchronous Explosion Calculator](#%EF%B8%8F-asynchronous-explosion-calculator)
- [Unnecessary Entity Updates](#%EF%B8%8F-unnecessary-entity-updates)

### ➡️ Asynchronous Explosion Calculator
On PMMP, the explosion computation is not asynchronous. Given that you would be dealing with concurrent calculations, this assignment may prove to be difficult.

For this method, simply put, the computation of explosions ought to be done on a separate thread from the main thread. You would have issues if there were multiple explosions at the same chunk. For instance, it would be challenging to modify a chunk given how many computations were still being performed on it.

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