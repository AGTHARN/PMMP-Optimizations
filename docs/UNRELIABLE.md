# 🔴 Unreliable Methods
Methods that are entirely questionable and will definitely break mechanics in your server.

# List of Contents
- [Multi Server Approach](#%EF%B8%8F-multi-server-approach)
- [Tick Skipping](#%EF%B8%8F-tick-skipping)

### ➡️ Multi Server Approach
Using only one server for a large number of player is typically not a good idea. It's advisable to divide the players among several servers, since this will lighten the load and minimize lag for your players.

However, in order to exchange data and communicate with other servers, numerous systems are needed. To ensure player data is stored appropriately, you will require an efficient and dependable database. For instance, you can utilize databases like MySQL and MongoDB. Additionally, a message broker will be needed for server-to-server communication. It will take a lot of effort to set up and manage each of these. 

This approach might not work for everyone, but it is a wonderful technique to ensure that the quantity of players won't have an impact on the server's performance. 

- **Efficiency** [✅✅✅]
- **Difficulty** [⭐⭐⭐❗]
- **Problems** [❓]
- **Safe** [❓]

### ➡️ Tick Skipping
Actions on the server are slowed down along with lag. There is little you can do to prevent delays, but there are a few ways to partially resolve this.

Lag can cause the server to slow down by several ticks, which makes the server stagnate. Rather than the server waiting for a specified tick to be reached so that actions are performed on that tick. **We ignore the ticks that have been delayed for too long and consider it as lost**.

I am aware that skipping ticks isn't a great idea which is why this is entirely unreliable. However, it may provide room for other actions. You may set-up some sort of priority list for specific actions that can be skipped and some that cannot.

- **Efficiency** [✅]
- **Difficulty** [⭐]
- **Problems** [🔥🔥🔥❗]
- **Safe** [❌]

<div align="right">
  <p>Done reading this section?</p>
    <a href = "https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/LAST_RESORT.md" target = "_self">FAQ ➡️</a>
</div>