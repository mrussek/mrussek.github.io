---
layout: post
title: "Ruminating on the Economics of OSS LLMs"
date: 2024-01-04
---
_Epistemic status: Very rough thinking, not an economist_

I feel like, at my work, I should be able to make a compelling argument _against_ the success of open-source LLMs. Intuitively, it seems like OSS LLMs lack a lot of the advantages of other open-source projects, while inheriting the heavy capital investment required by LLM technology in general. However, I feel like I haven't been able to express my thoughts coherently enough for people to listen, so I may spend several blog posts fleshing out my thoughts.

# Why Open-Source Works in the First Place

Not all open source projects are guaranteed to be successful, obviously. However, it does seem that there are particular characteristics of successful OSS projects that predict their success. Most notably, open-source projects that are used directly by software developers in the service of other goals seem to be much more successful, on the whole. For instance, Python, Flask, Torch, etc, are used by several software development companies for developing applications, and are considered foundational infrastructure in many domains. However, I've never heard of an end-user focused note-taking app taking market share from OneNote, or GnuCash taking share from QuickBooks.

The reason, as far as I can tell, is that open source developer infrastructure has a lot of immediate advantages over proprietary software that user facing applications lack. Notably, when your users are developers, they tend to be more helpful in reporting bugs, suggesting features, and possibly developing pieces themselves, funded by their firms which are often invested in the success of the software as well. Additionally, it seems likely that developer infrastructure often requires less in the way of matters of taste and design, which are harder to communicate across a wide range of projects – just look at how different many GNOME applications look.

So developer infrastructure represents a good alignment of incentives; firms provide the development man-power and effectively socialize their costs to development. Why shouldn't this work with LLMs?

# Open-Source Advantages Fail to Apply to LLM Technology

The bulk of the reason, I suspect, is that LLMs are not merely a software artifact, but also compose two other often overlooked components - data and training. While data, roughly, can be sourced from the Web, training introduces an interesting complication in the open source development value chain.

Suppose that I'm an interested developer building on top of Llama-2. I deploy it, write some prompts, do some RAG, etc. But then, I realize that I can improve on some part of Llama's architecture, data, training scheme, etc (how I know this is another problem). While I could certainly contribute my insight to the Llama-2 team, that would not result in an immediate improvement in Llama-2 for me or for anyone else. Because we would have to _retrain_, which is prohibitively expensive to do for every potential contribution to an open-source project with a shoestring budget. The benefit of being open-source ceases to apply.

# Common Open-Source Rebuttals

When confronting this, I have seen many open source advocates start to rationalize and look for a way out. One common way, is that while we have to have some centralized retraining process, open-source would be better fit to crowd-source training data. This almost universally comes from people who have not had to maintain datasets before. Crowd-sourcing training data is almost always harder than people think. Just because some people are willing to contribute effort, doesn't mean the effort they contribute is of high quality. It's hard enough to get people who are _paid_ to produce high quality data to do it without cheating, let alone getting anonymous unpaid volunteers to do it.

Another objection I sometimes hear is that open-source will be able to quickly deliver innovation for models. But once they do so, proprietary vendors will be able to uptake these innovations without much problem. For example, the Mamba hype does not mean anything with regard to the success of open-source LLMs. Maybe Mamba is better than self-attention. If so, the proprietary players have almost certainly verified and progressed beyond open-source by now.

# Open-Source LLM Development Does Not Compose

Lastly, I do see people talking about decentralized AI and how we, as some sort of autonomous decentralized collective, will be able to develop LLMs that rival proprietary providers. Most of these people have more faith than evidence. But they all seem to make the same mistake, in my opinion. They assume that LLM development will be compositional in the same way that traditional software development is.

Here's the thing; if I develop a kick-ass open source AMD driver for Linux, and you do the same for NVIDIA, then, hell, we have both done! It's great. We've parallelized the work. But the thing is, that very much does not work with LLM technology. If I spend millions of dollars and train a kick-ass open source 7B LLM, and you do the same, we _cannot_ combine them to form an even better LLM. Our efforts do not compose. If anything, they are counterproductive. Just think of how many 7B models have been superseded at this point, without ever providing the return-on-investment for the compute they required.

Ultimately, LLM development doesn't feel to me to be the arena in which open source has sufficient advantage to play a role against large, directed proprietary efforts. The advantages of a closely aligned cohesive organization will always apply more in this domain than those in open-source. We can disregard the lamentations of open-source believers as being "cope", unwilling to address the severe disadvantage that we have all been dealt.