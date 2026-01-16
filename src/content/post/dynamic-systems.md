---
title: "Dynamic Systems"
description: "Looking into dynamic systems, and being a bit weird in the connections I make"
publishDate: "16 November 2025"
tags: ["Thoughts"]
draft: true
---
> [!NOTE]
> This is not a polished post but a simple illustration of connections I find interesting.
> This post is not meant to shed light on a deep revelation (there is none) but rather encourage 
> the reader to explore these ideas as I have done. Maybe email me to encourage me to think too :)

# For a lack of a better term: Dynamic systems
While reading [On the distance between two neural networks and the stability of learning](https://arxiv.org/pdf/2002.03432) by Jeremy Bernstein et al. (2020), I got stuck thinking about a point they make briefly when discussing how GANs are trained. A GAN is really two networks interacting in an adversarial way. We frame these as the *Discriminator* (D) and the *Generator* (G). The discriminator tries to tell whether data is real or generated, and the generator tries to fool it.

It got me thinking about another notorious dynamic system: financial markets. When a big player makes a trade, every other player incorporates that information into their decisions before acting. It’s this higher-order reasoning that makes markets so volatile and unpredictable.

Another example could be natural ecosystems. In cases where an intervention, like introducing or removing a species, has changed how the other species behave, it often leads to cascading and sometimes extreme outcomes.

Then there’s the double pendulum. The perfect example of a fully deterministic but chaotic system. Here, the rules of the game don’t change over time at all, but the interaction between the two arms creates this interesting sensitivity making small changes explode into totally different outcomes. It’s along the same lines as the three-body problem: add just one more interacting piece.

All of these systems have the common property of instability. But there’s also a pattern running through every one of them: you have different parts of a system interacting with each other, bouncing signals back and forth, sometimes amplifying them and sometimes damping them. G pushing on D, predators pushing on prey, one pendulum arm pushing on the other. That constant feedback is what creates the instability.

And this is basically where the original GAN point loops back in. The way GANs are trained offers a glimpse of how we deal with these dynamic systems in practice. We don’t try to solve the whole system at once. Instead, we train one network close to its optimum, freeze it, and then nudge the other network to fool that almost-optimal version, slowly, iteratively, back and forth. What’s interesting is that each network’s forward and backward passes *depend on the other network’s current state*. So the optimization isn't happening on a fixed landscape. The loss surface isn’t a nice set of static peaks and valleys but it’s more like a shifting sea of waves. Every time you think you’ve reached the bottom, the ground moves (very poetic I know). But by taking small steps and freezing one side at a time, the whole thing becomes just stable enough to work.

Finally I have to mention calculus as it is our defacto standard tool for dealing with these systems, and its methods show clearly how we solve these systems. When we study how functions change, we don’t try to understand everything at once. Instead, we “freeze” all other variables and look at the effect of a small perturbation. We zoom in a wildly nonlinear curve until it becomes locally linear and therefore manageable. In other words, we temporarily simplify the system by holding everything else fixed. This is weirdly similar to how we train GANs. We freeze one network, optimize the other as if the world stopped moving, and then switch. The global system is messy and dynamic, but locally and under small updates it is manageable.

Thank you for reading! I know it must have felt like I just connected many different topics all together but that is for me the fun of thinking :)
