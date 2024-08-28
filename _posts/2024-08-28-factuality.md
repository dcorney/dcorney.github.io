---
layout: post
category: thoughts
title: Factuality, LLMs and fact checking
---


Factuality paper link: https://rdcu.be/dRFy0
(Maybe add screen shots of snippets from the actual paper! Including title/author block)

A few months after ChatGPT was launched in late 2022, I joined a group of academics and practicioners with expertise in intersection of disinformation, fact checking and AI. We were all concerned about the likelihood that making generative AI tools widely available would lead to a proliferation of false information online that would be hard to distinguish from reliable information. We spent some time discussing our worries but also our excitement at the possibilities that such models raise. Eventually, after much back and forth, we organised our ideas and polished our arguments, and I'm very proud that the resulting paper, "[Factuality challenges in the era of large language models and opportunities for fact-checking](https://rdcu.be/dRFy0)", has just been published in Nature Machine Intelligence. Rather than summarise the whole paper, I'd like to highlight just a few of the ideas.

## Nothing is new under the sun

ChatGPT was launched less than two years ago in November 2022 and caught the public imagination. It's easy to use and produces fluent text in response to pretty much any prompt. It launched or accelerated dozens of similar projects and soon everyone was familiar with generative AI. But the core ideas go back to at least 1948 and Claude Shannon's work on statistical language models. What's new is the scale: scraping billions of web pages of text (and images) and training models with billions of parameters just wasn't practical until the price of cloud storage and computing dropped. (There's new technology too, but as always, it's built on what was there before.)

<img  src="/images/factuality/shannon1948.png" alt="Extract from paper: In his pioneering work on information theory published in 1948, Claude Shannon proposed simple statistical language models based on letter and word frequencies capable of generating text that, although devoid of meaning, resembled human language." width="250" align="right"/>


## It's not just hallucinations

<img  src="/images/factuality/halo_effect.png" alt="Extract from paper: The proficiency of a model in addressing one topic might lead users to believe that it can excel in any open-domain conversation, an example of a cognitive bias known as the halo effect" width="250" align="right"/>

We all know that genAI models hallucinate: while they answer many questions correctly and can be quite creative, they are often just plain wrong. While this is itself a problem, the fact that the output is *fluent* and reads like confident expert opinion means that it is easy to be mislead by it. We also discuss the *halo effect*: if people start by asking a chatbot questions where the generated answer happens to be correct, they are more likely to believe it next time, leading to more (misplaced) trust. Add to this incomplete or out-of-date training data and exaggerated evaluation claims, and it's clear that genAI is prone to produce unreliable information. 
    
 
## It's nothing but hallucinations

(The paper mentions hallucinations 36 times in 8 pages of prose.)
It's worth mentioning that the core of these models is fundamentally the same: they predict the next word in a sequence, based on previous analysis of a very large collection of text. So given a prompt, such as question, they produce a response where each word is relatively likely given the prompt and the rest of the response up to that point. It is not trying to find the response that is "true", but merely one that is "likely". (Similarly, visual perception didn't evolve to show us what is *really* out there, but merely what is *likely* to be out there based on our history. I wrote about [illusions and genAI hallucinations here](https://dcorney.com/thoughts/2023/02/20/illusions-hallucinations.html)). So when we look at the output and say, "Oooh, it got that bit wrong, it's hallucinating!" the model is doing exactly the same as when we say, "Wow, it's passed this medical exam!". It's *all* made up, but some of it happens to be true.

## What's the worst that could happen?

(threats) - personalized attacks / impersonation / lack of detection / fake profiles

## What can we do to fix this?
RAG / self-checking / updating knowledge basees / indentifying generated content / provenance

## Fact checking in this brave new world

Better summaries so wider monitoring; claim matching/NLP to support fact checking; domain-specific verification - make it easier to find reliable information from potentially complex sources.



