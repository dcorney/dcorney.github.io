---
layout: post
category: thoughts
title: Why are some NLP tasks so hard?

---

*[Updated below](#update)*

Computers are now really good at [some](https://voicebot.ai/2020/07/09/facebook-builds-speech-recognition-engine-combining-51-languages-in-one-model/) [NLP](https://towardsdatascience.com/machine-translation-a-short-overview-91343ff39c9f) [tasks](https://www.theverge.com/2020/6/11/21287966/openai-commercial-product-text-generation-gpt-3-api-customers) but still struggle with others. 

They have an advantage over us mortals when it comes to speed or memory or concentration, so do well at tasks that need these skills and only these skills. But many NLP tasks require something else: a common-sense knowledge of the world around us. It's easy for a machine to "read" a thousand books or a million books,[^lms] but to "understand" what they read - to associate the words with the real world - is much harder [^problems].

I'm currently interested in deciding if two claims mean essentially the same thing. When my [fact checking colleagues](https://fullfact.org) respond to some bad information online, we want to know if someone else repeats that bad information so we can respond quickly when appropriate. This turns out to be really hard - but why? 

Consider the statements, "I'm allergic to cats" and "I'm allergic to dogs." These are very similar claims, and any NLP language model will know that cats and dogs are often talked about using the same kind of language (pets, fur, vets etc.). This means that a computer could respond to them in the same way, such as recommending pet allergy treatments. 

But now consider "[Leicester is going back into lockdown](https://fullfact.org/online/leicester-5g-no-connection-covid/)" with "Edinburgh is going back into lockdown[^not]". Knowing that Leicester and Edinburgh are both cities in the UK, have similar populations[^pop]  and have both had Covid-19 cases DOES NOT mean that the sentences are equivalent: for these claims, the specific location matters, for example. The significance of knowing that they are different cities, hundreds of miles apart, is implicit, so language models will ignore it. Having checked one claim doesn't mean we know the validity of the other. To sensibly respond that these are two different claims, albeit related, we need more than a typical language model can provide. Maybe a knowledge base, maybe some entity recognition or maybe something else [^answers].

#### The Curse of Knowledge   

So why do we humans find it so easy to interpret most statements correctly? Well, we learn how to communicate from a very young age and we continuously interact with the world.  It's often hard to separate objects and concepts from the language we use to describe them, as language is so central to our experience. We quickly grasp the intended purpose of each piece of communication, which helps us latch onto the critical bits of information. It's very hard to imagine what it's like to not have that skill. 

Common-sense knowledge may be hard to encode in machines, but it's also hard for us to appreciate how powerful and hard-won it is. Until we understand this better, I think machines will continue to struggle with many everyday NLP tasks.



### Update  

(July 20, 2020) 

Shortly after posting the above, I came across a new paper by Emily Bender and Alexander Koller[ "Climbing towards NLU: On Meaning, Form, and Understanding in the Age of Data](https://www.semanticscholar.org/paper/Climbing-towards-NLU%3A-On-Meaning%2C-Form%2C-and-in-the-Bender-Koller/02eaaf87f9cae34cca398fed146079e6eeb1f868?p2df)". This says a lot of what I was thinking, but with far greater precision, confidence and supporting evidence (not surprising, given that it's written by two professors of linguistics!). A couple of points that particularly struck me:

They contrast *form* as the expression of language, whether written, spoken or signed; versus *meaning*, which defines "the relation between the form and something external to language," including communicative intents. However much one analyses expressions in a language, one never acquires knowledge of how the language is used in practice. And this is why language models cannot model the significance of particular words in a particular context.

A second idea from the paper distinguished two modes of research. First, "bottom-up" research, which is incrementally improving existing tools: climbing the hill you find yourself on. And second, "top-down" research, which is choosing which hill to be on in the first place. Language models are incredibly powerful, and getting better all the time. But where are they leading us? (Other than ever better GLUE benchmark scores?) And when will we realise we're on the wrong hill?

Well worth a read.



---

Footnotes:

[^lms]: NLP has made huge advances in recent years with the widespread adoption of language models such as [BERT](https://github.com/google-research/bert) and [GPT-3 ](https://github.com/openai/gpt-3). These are trained on millions of line of text and learn which words and sentences tend to follow each other. But they have no deeper model of the world around them.
[^problems]:But there are plenty of NLP tasks that computers [still struggle with](https://ruder.io/4-biggest-open-problems-in-nlp/), many of which fall under the heading of "natural language understanding". 
[^not]:Edinburgh is not going into lockdown as far as I know! (July 2020)

[^pop]: Around half a million
[^answers]: Answers on a postcard. Seriously, please [tell me](<mailto:dpacorney@gmail.com>) your ideas!


