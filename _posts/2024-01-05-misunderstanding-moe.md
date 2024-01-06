---
layout: post
title: "Mixture-of-Experts Misinformation"
date: 2024-01-05
---

In [yesterday](https://mrussek.com/2024/01/04/economics-of-oss-llms.html)'s post I mentioned that LLM technology does not neatly decompose into tasks that can be accomplished by teams running in parralel. In a brief addendum to that, I wanted to address what seems to be a somewhat common misunderstanding (although I could have misunderstood myself; if you are knowledgeable and that seems to be the case, please email me and let me know).

[Mixture-of-Experts](https://arxiv.org/abs/1701.06538) is a technique often used in Transformer language models. A brief summary of what it does is it replaces some number of the MLP layers in a transformer architecture with "MoE" layers, which involve evaluating each sequence item with a gating network and then using the results to route to some number of "expert" feed-forward layers. The benefits are that you are able to scale the number of parameters available to the network while not increasing the cost of inference.

Now let's talk briefly about some things Mixture-of-Experts is _not_. It is _not_ an ensemble of entire networks that have been trained on human recognizeable subject areas. For instance, I see a lot of talk about there being a "biology" expert or a "legal" expert in an MoE model. While that _could_ be true, we would discover it after the MoE is trained, and it would probably be a fuzzy match. This is because the data was not split neatly into different subject areas and then sent to different networks, at least not as far as I'm aware.

Why do I mention this in the context of decomposing the work of training LLMs? Because some people seem to believe that we should be able to split up the work as follows:

1. Team 1 trains a 7B parameter model on medical data
2. Team 2 trains a 7B parameter model on legal datas
3. Team 3... you get the idea.

Then, as a part of some final, magical step, we ensemble the models together using "Mixture-of-Experts" as it is misunderstood above. This allows us to break up the work efficiently and proceed in parallel.

Maybe the above technique works? It could be so. But the important thing to note is that it is _not_ MoE and it is _not_ relevant to either models such as Mixtral nor due to the [rumored architecture](https://twitter.com/soumithchintala/status/1671267150101721090?lang=en) of GPT-4.