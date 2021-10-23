---
layout: post
title:  "Memory is the Missing Component in Deep Learning."
date:   2021-10-23 14:10:01 -0700
categories: jekyll update
published: false
---

Current deep learning training is more akin to classical conditioning than it is to teaching by experience. You run the network over hundreds or thousands of very similar training examples, each time slightly updating all the weights in the network in an attempt to force the network to have the same knee-jerk reaction to similar inputs as in the training set.

In people, experiences lead to episodic memories which can be recalled explicitly; the past experience can be re-simulated with modifications giving way to reasoning (e.g., one can wonder what would happen if they said or did `this` instead of `that`).

Networks, even most "generative" nets can't explicitly recall training experiences, and nothing that I know of is close to being able to reason from past experience by explicit recall and counterfactual reasoning. Current nets are more like a dog trained to rollover at the sound of a bell in order to get a treat. It isn't clear that the dog can explicitly recall the past times it heard the bell and got the treat; the whole operation seems to arise from the subconscious. 

People can learn via classical conditioning in addition learning from higher order experience. You can "teach" yourself the compulsion to pick up your phone when it dings, without conscious thought involved. A lot of rapid skills, like riding a bike or playing a barre chord on the guitar are internalized subconsciously. Coincidentally, these are exactly the type of tasks deep nets seem to excel at. Andrew Ng has famously said ""If a typical person can do a mental task with less than one second of thought, we can automate it using AI …"

The "higher order reasoning" stuff that people do mostly seems to rely heavily on episodic memory. For example, one can observe the actions of a handyman repairing their sink and have the ability to do the same repair "one shot" next time the sink has a problem by explicitly recalling what they did to repair the sink.

One assumes that it requires a certain level of "intelligence" in order to form episodic memories and reason based on them. Simple creatures like insects probably don't ever think in terms of counterfactuals, but there is some evidence other, more intelligent animals like Crows have episodic memory (https://www.nature.com/articles/26216). However, besides scale.

It generally feels like gradient descent is maybe not a good model for episodic memory. 

