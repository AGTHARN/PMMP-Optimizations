# AGTHARN's Optimization Methods
[![Hits](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations.svg?view=today-total&style=flat-square&label=views)](https://hits.sh/github.com/AGTHARN/PMMP-Optimizations/)

This document includes arguable ways to optimize **PocketMine-MP** (PMMP) gathered from my research and experiments. 

I wanted to share this document with the community so that you could have a better understanding of why your server might occasionally be sluggish. You might have some unfavorable remarks, but I've categorized all of my findings separately.

The majority of these methods are ones I advise against utilizing, but I've included them nonetheless so as to be thorough. 

> ⚠️ **You should be cautious when using these methods for production purposes**. All of these methods will cause some sort of a problem for your server. Even if you used these methods, you MUST accept all the consequences involved! Overall, all these methods are entirely arguable. ⚠️

## Why would I want to spend time on such experiments?
I personally have run a PocketMine-MP (PMMP) server, and I've been dealing with the same problem since the server's inception - lag brought on by high player counts rendering PMMP servers virtually unplayable. This is especially visible for servers that have a lot of worlds loaded, and players constantly loading chunks and triggering events.

Many individuals have frequently used the argument that the problem is with the server's plugins or that PMMP is single-threaded. That's not entirely true, but it's definitely comparable.

One day, I pondered how much I could adjust the mechanics of PMMP in order to push it as far as it could go. The experiments I have produced offer favorable performance enhancements but may have unintended consequences.

# 🌟 Table of Contents
| Type | Description |
| ----------- | ------- |
| [Reliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/RELIABLE.md) | Methods that should be safe as long as you have an idea of what you're doing |
| [Somewhat Reliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/SOMEWHAT_RELIABLE.md) | Methods that can be arguable at times and may require you to fix even more problems |
| [Unreliable Methods](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/UNRELIABLE.md) | Methods that are entirely questionable and will definitely break mechanics in your server |
| [Frequently Asked Questions](https://github.com/AGTHARN/PMMP-Optimizations/blob/main/docs/FAQ.md) | Questions that you may have on this document |

# 💡 Timings
> ❗ **The `Average Players` shown in the images below are incorrect due to problems on my end. If you do think that the results are skewed, if necessary, you may perform your own computations after trying out some of the optimization methods.** The number of players is equivalent to the number of worlds loaded. ❗

| [Before Modifications](https://timings.pmmp.io/?id=222286) |
| ----------- |
| ![before](https://user-images.githubusercontent.com/63234276/180207286-eb69ac8e-697e-4e0d-903d-bdaa6a023248.png) |

| [After Modifications](https://timings.pmmp.io/?id=227338) |
| ----------- |
| ![after](https://user-images.githubusercontent.com/63234276/180207462-6a27702e-25f9-4731-bc7e-11b63d17b5d4.png) |

*Writer's Note: The modifications I've made are ones that a skilled developer could do with ease. Since they are not the finest, I do not intend to release a fork of these modifications. However, I'd like to see somebody else give it a go.*