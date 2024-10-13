---
layout: post
category: thoughts
title: What cognitive science teaches us about AI and vice versa
---

I recently came across a paper[^1] making a bold claim: that machine learning will never lead to actual artificial intelligence. It's bold because it flies in the face of big announcements in recent years from OpenAI, Google and many others, who claim that as machine learning is used to build bigger and bigger models, that human-like intelligence will emerge. 

Below are some choice quotes from the paper and my reflections on them.

## "A person can not only play a game of chess, but reason about why their opponent has angrily left the room, and later draw on that event when writing a novel."

This nicely captures the lack of ambition of so much current AI work. Computers can beat people at chess (and Go and many other games). I asked ChatGPT why my oponent "angrily left the room", and it did its job extremely well: it returned, in fluent English, a list of 5 reasons why someone might behave that way. "It sounds like your opponent was frustrated or upset by the outcome of the chess game. There could be several reasons for their reaction: 1. Emotional Investment: Chess can be intense, and some players invest a lot of energy and focus into the game. Losing, especially in a game they believed they had under control, can lead to emotional reactions...." Like all the output from LLMs, this nicely paraphrase and summarises the kind of things people have said online. I don't think this is hallucination, and it's not a bad answer. But of course, ChatGPT has absolutely no insight into the state of mind of my (hypothetical) bad loser. It can only give a slightly bland, "average" answer about what people say about how people behave.

## [Consider] "pursuing the kind of ML approach claimed to inevitably lead to AGI. By studying the engineering task that they have set themselves through a formal, mathematical lens we are able to construct a proof of intractability."  

In other words, machine learning cannot lead to AGI. This is the bold claim at the heart of the paper. 

One slight criticism of the paper though: this is a specific claim, that AGI cannot be simply learned from data sets. Intuitively, this makes sense: the behaviours people produce are boundless in many dimensions, so any sample of those behaviours will capture a trivially small part, requiring the ML model to magically extrapolate to new, unseen areas. But of course, there's more to AI than ML (despite that being the dominant paradigm and worthy of multiple Nobel prizes, apparently.) I don't know if we could achieve AGI by plugging ML components inside a non-ML architecture, but I don't think this paper addresses that possibility. The narrow claim is AGI cannot be learned, not that AGI cannot be programmed in some sense. But later on, this distinction gets muddled.

## "Hence, contrary to intuition, one cannot extrapolate from the perceived current rate of progress to the conclusion that AGI is soon to be attained."
- new AI models coming out of OpenAI and the rest are getting better and better at what they do - but what they do isn't AGI.

- Bender & Koller (2020) and paraphrased here. Original quote: "NLP is currently in the process of rapid hill-climbing. Every year, states of the art across many NLP tasks are being improved significantly... and tasks that seemed impossible not long ago are already old news. ... the question is whether the hill we are climbing so rapidly is the right hill."

## "That is, if you think your AI is very human-like, then you are not testing it critically enough"

- General point: if you use a simulation to design a new bridge, before you spend a lot of time actually building it, you'll want to test your ideas. But who do you ask? A simulation expert? No - a bridge expert, aka a structural engineer.

- So if you build an algorithm that you believe has human-like intelligence, do you ask a computer scientist to test it? No - ask an intelligence expert, aka a psychologist (or cognitive scientist)


<br>
----
[^1]: Rooij, I. van, Guest, O., Adolfi, F. G., Haan, R. de, Kolokolova, A., & Rich, P. (2023). Reclaiming AI as a theoretical tool for cognitive science. OSF. https://doi.org/10.31234/osf.io/4cbuv
