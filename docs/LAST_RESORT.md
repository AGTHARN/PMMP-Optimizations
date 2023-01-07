# 🏳️ A Last Resort
You can enhance the performance of your server using any of the techniques I've listed in the document.

However, if you feel that PocketMine-MP (PMMP) is simply too sluggish for you or applying these techniques is impossible because of your limits, you may want to consider utilizing an alternative software.

Here are a few server applications that I believe deserve to be mentioned. Although I haven't really fully evaluated these applications myself, you might find them an area of interest. 

*If you need a full list of active/inactive server softwares, you can check out [this](https://wiki.bedrock.dev/servers/server-software.html) list maintained by the Bedrock OSS Organization.*

### 🖥️ [PowerNukkitX (Java)](https://github.com/PowerNukkitX/PowerNukkitX)
> "PowerNukkitX is a branch version based on PowerNukkit, developed and maintained by PowerNukkitX."

**✅ Advantages:**
- **Java** - Java is a more mature than PHP with a much larger ecosystem and is a statically-typed language. This means that there are more developers who can help you with your issues.
- **Less CPU-intensive** - Java is generally considered to be faster and more efficient than PHP, especially when it comes to CPU-intensive tasks.
- **More plugins** - There are more plugins available for Nukkit than for PMMP. This would allow you to choose from a wider variety of plugins.

**❌ Disadvantages:**
- **Java** - Java has slightly less features than PHP and may require you to do more work to achieve the same results. Java also has no support for features like operator overloading.
- **More RAM-intensive** - Java is generally considered to be more RAM-intensive than PHP which means that you will need more RAM to run your server.
- **More difficult to set up/maintain** - Java is a more complex language to learn and apply as compared to PHP. This may make it more difficult to set up and maintain your server.

### 🖥️ [Dragonfly (Go)](https://github.com/df-mc/dragonfly)
> "Dragonfly is a heavily asynchronous server software for Minecraft Bedrock Edition written in Go. It was written with scalability and simplicity in mind and aims to make the process of setting up a server and modifying it easy. Unlike other Minecraft server software, Dragonfly is generally used as a library to extend."

**✅ Advantages:**
- **Go** - Go has a strong standard library that includes a wide range of useful functions and packages, which can make it easier to build certain types of applications. It has a simple and easy-to-learn syntax, which can make it a good choice for developers who want to quickly build applications without having to learn a lot of complex syntax.
- **Ease of concurrency** - Dragonfly makes use of Go's built-in support for concurrent programming, which means that it is easy to write tasks that happen simultaneously.
- **Fast and efficient** - Dragonfly is considered to be a fast server software since Go is a compiled language as it is compiled into machine code that can be directly executed by the processor. This also reduces the amount of RAM that is required to run the server.

**❌ Disadvantages:**
- **Go** - Go is a relatively new language and has a smaller ecosystem than PHP. Go does not have support for operator overloading, which means that developers cannot define custom behavior for operators like `+` or `-`.
- **No plugins** - Dragonfly does not support plugins, which means that you will have to write your own code to extend the functionality of your server. You may make use of [Saddle](https://github.com/saddlemc/saddle).

### 🖥️ [LiteLoaderBDS (C++, JavaScript(NodeJs), Lua, .NET)](https://github.com/LiteLDev/LiteLoaderBDS) (possible interest)
> "`LiteLoaderBDS` is an unofficial plugin loader that provides basic API support for `Bedrock Dedicated Server`, with a massive API, lots of packed utility interfaces, a rich event system and powerful basic interface support.
> 
> `LiteLoader` provides a massive API, a powerful event system and a large number of encapsulated development infrastructure interfaces, providing a solid foundation for extending the Bedrock Edition BDS with more gameplay and functionality. With plugins, it is easy to extend the functionality of BDS, the associated development is easy to learn, and the development approach is flexible.
> 
> Writing plugins in **C++, JavaScript, Lua, C#** and other languages, which allows developers to easily extend and customize **BDS** functionality, making it easy to learn and extremely flexible."

**✅ Advantages:**
- **C++, JavaScript, Lua, .NET** - These are widely used languages with a large ecosystem. They all have a large number of libraries and frameworks available that can help developers to build applications more quickly and easily. With many languages supported, you can choose the language that you are most comfortable with.
- **Extension of BDS** - LiteLoaderBDS extends the functionality of BDS. BDS is maintained by Mojang and does not have any compromises in vanilla gameplay. LiteLoaderBDS allows you to add new features to your server, and is more secure and stable as compared to BDS.

**❌ Disadvantages:**
- **C++, JavaScript, Lua, .NET** - These can all be difficult to learn and more difficult to debug than some other languages.
- **More Resource Intensive** - C++, JavaScript, Lua, and .NET can use more memory and CPU, which can make them less efficient than some other languages.