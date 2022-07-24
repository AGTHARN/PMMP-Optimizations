# AGTHARN's Optimization Theories
[![Hits](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations.svg?view=today-total&style=flat-square&label=views)](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations/)

## PLEASE READ! 23/7/2022
The sole purpose of this was only to provide some light over the experiments I have done on PMMP to my friends. It was never intended for the public to read this. Although all the comments I have gotten were negative, I will not let your comments influence my work.

This project was also **NOT MEANT FOR ANY PRODUCTION PURPOSES**. All of these methods can cause problems for your server, especially if your server requires PvP action. It is indeed undeniable that PlayerAuthInput is way better than PlayerMovement and I must accept that. **I only made this so as to document my findings after my experiments on PMMP**. Even if you used these methods, you MUST accept all the consequences involved! Overall, all these methods are entirely arguable.

### **THESE ARE EXPERIMENTS! DO NOT TURN THEM INTO IDEAS!**

## Why did I want to spend time on such experiments?
I myself run a PocketMine-MP (PMMP) server, and I've been dealing with the same problem since the server's inception - lag brought on by high player counts rendering PMMP servers virtually unplayable.

Many individuals have frequently used the argument that the problem is with the server's plugins or that PMMP is single-threaded. That's not totally true, but it's comparable.

One day, I pondered how much I could change PMMP in order to push it as far as it could go. The experiments I have produced offer favourable performance enhancements.

# 🌟 Table of Contents
| Type | Description |
| ----------- | ------- |
| [Reliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/RELIABLE.md) | Methods that should be safe as long as you have an idea of what you're doing |
| [Somewhat Reliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/SOMEWHAT_RELIABLE.md) | Methods that can be arguable at times and may require you to fix multiple problems |
| [Unreliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/UNRELIABLE.md) | Methods that are entirely questionable and will definitely break mechanics in your server |

# 💡 Timings

**Due to the player count, the findings may be skewed, however if necessary, you can perform your own computations.**

| [Before Modifications](https://timings.pmmp.io/?id=222286) |
| ----------- |
| ![before](https://user-images.githubusercontent.com/63234276/180207286-eb69ac8e-697e-4e0d-903d-bdaa6a023248.png) |

| [After Modifications](https://timings.pmmp.io/?id=227338) |
| ----------- |
| (player count is incorrect! it's a problem i have made on my end! however, since it is a skyblock server, the number of players is equivalent to the number of worlds loaded!) |
| ![after](https://user-images.githubusercontent.com/63234276/180207462-6a27702e-25f9-4731-bc7e-11b63d17b5d4.png) |

The modifications I've made are ones that a skilled developer could do with ease. Since they are not the finest, I do not intend to release a fork of these modifications. However, I'd like to see somebody else give it a go.