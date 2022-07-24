# Reliable Methods
Methods that should be safe as long as you have an idea of what you're doing.

# ✔️ List of Contents
- [Unnecessary Entity Updates](#%EF%B8%8F-unnecessary-entity-updates)

### ➡️ Unnecessary Entity Updates
On my server, minions are present, and players enjoy piling them up. There are more entities to update/tick when more minions are placed. The performance of the server may suffer greatly as a result. 

Therefore, I removed pointless updates from the entity class's `onUpdate()` and `entityBaseTick()` functions. For instance, I don't anticipate that minions will have any motion so I had that removed from its updates. **Performance can already be enhanced just by eliminating unnecessary updates**. You may do the same for any entity which you do not expect to be moving such as NPCs most of the time.

- **Efficient** [✅✅]
- **Problems** []
- **Safe** [✅]

