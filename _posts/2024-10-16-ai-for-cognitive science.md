---
layout: post
category: thoughts
title: What cognitive science teaches us about AI and vice versa
---

I recently came across a new paper[^1] making a bold claim: that machine learning will never lead to actual artificial intelligence. Not just that AGI is hard, but rather that it is provably impossible to achieve through ML. It's a bold claim because it flies in the face of so many big announcements in recent years from OpenAI, Google and many others, who claim that as machine learning is used to build bigger and better models, that human-like intelligence will emerge. ([These](https://openai.com/index/planning-for-agi-and-beyond/) [claims](https://www.forbes.com/sites/jodiecook/2024/07/16/openais-5-levels-of-super-ai-agi-to-outperform-human-capability/) are [everywhere](https://www.dwarkeshpatel.com/p/shane-legg#details), but the details always seem very sketchy. DeepMind has at least tried to [define AGI](https://arxiv.org/abs/2311.02462) operationally.)

Below are some choice quotes from the paper and my reflections on them.

### "A person can not only play a game of chess, but reason about why their opponent has angrily left the room, and later draw on that event when writing a novel."

This nicely captures the lack of ambition of so much current AI work. Computers can beat people at chess (and Go and many other games). I asked ChatGPT why my oponent "angrily left the room", and it did its job extremely well: it returned, in fluent English, a list of 5 reasons why someone might behave that way. 

##### (ChatGPT:) "It sounds like your opponent was frustrated or upset by the outcome of the chess game. There could be several reasons for their reaction: 1. Emotional Investment: Chess can be intense, and some players invest a lot of energy and focus into the game. Losing, especially in a game they believed they had under control, can lead to emotional reactions...." 

Like all the output from LLMs, this nicely paraphrase and summarises the kind of things people have said online. I don't think this is hallucination, and it's not a bad answer. But of course, ChatGPT has absolutely no insight into the state of mind of my (hypothetical) bad loser. It can only give a slightly bland, "average" answer about what people say about how people behave.

### [Consider] "the kind of ML approach claimed to inevitably lead to AGI. By studying the engineering task that they have set themselves through a formal, mathematical lens we are able to construct a proof of intractability."  

In other words, machine learning cannot lead to AGI. This is the bold claim at the heart of the paper. The proof is quite abstract, though not terribly complicated. I can't see anything wrong with it, but it does rely on a few assumptions, so it's not quite clear (to me) how much of "machine learning" is covered. 

One slight criticism of the paper though: this is a specific claim, that AGI cannot be simply learned from data sets. From the earlier informal discussions, this makes sense: the behaviours people produce are boundless in many dimensions, so any sample of those behaviours will capture a trivially small part, thus requiring the ML model to magically extrapolate to new, unseen areas. But of course, there's more to AI than ML (despite that being the dominant paradigm and worthy of [multiple](https://www.nobelprize.org/prizes/physics/2024/hinton/facts/) [Nobel](https://www.nobelprize.org/prizes/physics/2024/hopfield/facts/) [prizes](https://www.nobelprize.org/prizes/chemistry/2024/hassabis/facts/), apparently.) 

I don't know if we could achieve AGI by plugging ML components inside a non-ML architecture, or whether some form of embodiment is necessary for cognition -- but the paper doesn't address or rule out such possibilities. The narrow claim is that AGI cannot be *learned*, not that AGI is *impossible*. But later on, this distinction gets muddled. For example in the conclusion, they state that making human-level cognition is computationally intractable but the rest of the paper has only (attempted to) test one path to a computational solution. 



### "Hence, contrary to intuition, one cannot extrapolate from the perceived current rate of progress to the conclusion that AGI is soon to be attained."

The paper paraphrases a good line from Bender & Koller (2020)[^2]: "NLP is currently in the process of rapid hill-climbing. Every year, states of the art across many NLP tasks are being improved significantly... and tasks that seemed impossible not long ago are already old news. ...the question is whether the hill we are climbing so rapidly is the right hill."

It seems that every week, new AI models are coming out of OpenAI, Google and the rest, and that they are getting better and better at what they do. With ever larger training sets, new algorithms and bigger computers, they can tackle a wide range of language tasks very successfully. 

But what they do isn't AGI. 


### "[I]f you think your AI is very human-like, then you are not testing it critically enough"

Suppose you use a computer simulation to design a new bridge. Before you spend a lot of time and money actually building it, you'll want to test your ideas. But who do you ask? A simulation expert? A programmer? No: you need a bridge expert, aka a structural engineer.

And so if you build an algorithm that you believe has human-like intelligence, do you ask a computer scientist to test it? A machine learning engineer?
No: you need an expert in intelligence, aka a psychologist or cognitive scientist. 

And when you do that, you rapidly find that generating the correct answer to a law exam, medical exam or Jeopardy quiz questions. (Remember [Watson](https://en.wikipedia.org/wiki/IBM_Watson)?)


# Some conclusions

Treating human behaviour as a black box, where one can only see the input (stimulus) and output (behaviour) was the core of [behaviorism](https://en.wikipedia.org/wiki/Behaviorism). While not disproven or abandoned, behaviorism was largely replaced by cognitive psychology from the 1950's, which has lead to huge leaps in our understanding of minds and how they work.

LLMs are primarily trained on next-word-prediction and next-sentence-prediction from a given context. This is modelling human behaviour by only considering the input (context) and output (the next word or sentence produced), and ignoring aspects such as memory, perception, motivation and metacognition. It's (sometimes) fun and (sometimes) useful -- but it's not a road to intelligence of any kind.

<br>

----

[^1]: Van Rooij, I., Guest, O., Adolfi, F., de Haan, R., Kolokolova, A., & Rich, P. (2024). Reclaiming AI as a theoretical tool for cognitive science. Computational Brain & Behavior, 1-21. https://link.springer.com/article/10.1007/s42113-024-00217-5

[^2]: Bender, E. M., & Koller, A. (2020, July). Climbing towards NLU: On meaning, form, and understanding in the age of data. In Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics (pp. 5185-5198).