---
layout: post
title:  "What is the Mean Victoria 3 Game?"
date:   2024-01-07
---
I'm trying, and failing, to get into _Victoria 3_. Mostly because I lack the time, and the patience, to play what appears to be a detailed economic history simulator. But it does make me wonder; to what extent are the dynamics in _Victoria 3_ actually the dynamics of history? And how could we figure this out?

I had a few ideas to explore this. Nominally, _Victoria 3_ is moddable and so I figure it should be amenable to being controlled by a script that produces rollout of an environment. Furthemore, it should allow AI players to control all countries. So, it should be in principle possible to simulate several thousand games of _Victoria 3_ and see what the progression of the average game entails. How close would this history be to our own? What variance would it exhibit? Are the bulk of games "plausible", historically? It does seem that this is a genre of [Youtube video](https://www.youtube.com/watch?v=WGRkdchoWjs), but I would be curious in a more systematic sampling. The video is revealing though. It does not deviate very far from actual world history, which supports a few observations: the mean _Victoria 3_ game is actually quite close to world history, and that deviations from world history are largely due to player choice.

I have searched for someone doing the work of creating a reinforcement learning environment for _Victoria 3_, but that appears to have not yet been done. Personally, performing RL in an historical environment seems like it might either reveal play imbalances that seem to break the game, or, more interestingly, historical strategies that reveal more of the underlying politics that underly the games mechanics.

The second case is also interesting to consider. While I haven't played much of the game, it seems interesting that so many of the strategy guides I have consulted seem...ruthlessly capitalistic? Not even in a bleeding heart concern-for-the-downtrodden way – apparently much of the early game strategy revolves around dispensing with Aristocrats. The optimal strategy for _Victoria 3_ would likely be to promote capitalism heavily, to the expense of every other goal. Granted, this depends on the reward function in the RL environment, and I guess similiarly, the chosen objective in the game. But still, I would be curious to see what types of behavior are latently encouraged by it's ruleset.

Obviously this extends to other games as well, but _Victoria 3_ seems particularly interesting. It would be fascinating to see the developers latent values expressed through the game mechanics (perhaps with unintended consequences), as well as to perform a type of "empirical" counterfactual history. Alas, this will have to wait until I can actually mod the game and make it headless. 


