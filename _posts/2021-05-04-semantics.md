---
layout: post
category: thoughts
title: When NOT to start an NLP project
---


Some problems are easier to solve than others, which shouldn't be news to anyone.
But how much can we predict this in advance, and choose not to try and solve unsolvable problems?

Advances in NLP in recent years are genuinely exciting, but a few recent (and not so recent!) papers have reminded us to be cautious. 

Language can be analysed at multiple levels, e.g.:
* phonology - basic set of sounds
* morphology - unit of meaning, components of words
* syntax - converting words into phrases and sentences
* semantics - meaning
* pragramtics - speech as acts
(see [this nice introduction to linguistics](https://courses.lumenlearning.com/boundless-psychology/chapter/introduction-to-language/))

Given a (possibly large) set of well-formed sentences, computers can analyse things like word frequences, co-occurences and so on. They can 'learn' that dog and dogs refer to the same animal, just varying in number. Or that the words X,Y or Z can fill the slot  in the sentence ".... ___ ..." and produce an acceptable sentence.

But they struggle with grounding - the relationship of words to the real world. We (humans) know what it's like to pick up an egg, to crack an egg, to eat an egg. But an NLP tool, when from Open AI, Stanford or Google, will only know that the word "egg" is often associated with "crack", "yolk", "delicate" and so on. 

Sometimes that's enough to "fake" understanding enough to solve the task. Some tasks can be solved without deep understanding - including, much to my surprise, machine translation. But it's not realistic to expect a NLP tool to have even the most basic experience of the real world, so if your task relies on that, you'd better wait until general AI is solved. And, as always, that's about 30 years away...