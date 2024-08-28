---
layout: post
category: thoughts
title: Factuality, LLMs and fact checking
---


<img  src="/images/factuality/title_block.png" alt="Screenshot of paper heading: Nature Machine Intelligence. Factuality challenges in the era of large language models and opportunities for  fact-checking" width="400" align="right"/>


A few months after ChatGPT was launched, I joined a group of academics and practitioners with expertise in the intersection of disinformation, fact checking and AI. We were all concerned that making these new generative AI tools widely available would lead to a proliferation of false information online that would be hard to distinguish from reliable information. We spent some time discussing our worries but also our excitement at the possibilities that such models raise. Eventually, after much back and forth, we organised our ideas and polished our arguments, and I'm very proud that the resulting paper, "[Factuality challenges in the era of large language models and opportunities for fact-checking](https://rdcu.be/dRFy0)", has just been published in Nature Machine Intelligence. Rather than summarise the whole paper, I'd like to highlight just a few of the ideas.

## Nothing is new under the sun

<img  src="/images/factuality/shannon1948.png" alt="Extract from paper: In his pioneering work on information theory published in 1948, Claude Shannon proposed simple statistical language models based on letter and word frequencies capable of generating text that, although devoid of meaning, resembled human language." width="400" align="right"/>

ChatGPT was launched less than two years ago in November 2022 and instantly caught the public imagination. It's easy to use and produces fluent text in response to pretty much any prompt. It helped launch or accelerate dozens of similar projects and soon everyone was familiar with generative AI. But the core ideas go back to at least 1948 and Claude Shannon's work on statistical language models. What's new is the scale: scraping billions of web pages of text and training models with billions of parameters just wasn't practical until the price of cloud storage and computing dropped sufficiently. (There's new technology too, of course, but as always it's built on what was there before.) It's easy to get lost in the hype, but science really is an incremental, communal effort.



## It's not just the hallucinations

<img  src="/images/factuality/halo_effect.png" alt="Extract from paper: The proficiency of a model in addressing one topic might lead users to believe that it can excel in any open-domain conversation, an example of a cognitive bias known as the halo effect" width="400" align="right"/>

We all know that GenAI models hallucinate: while they answer many questions correctly and can be quite creative, they are often just plain wrong. While this is itself a problem, it's made worse by the fact that the output is *fluent* and reads like confident expert opinion, which means that it is easy to be misled. We also discuss the *halo effect*: if people start by asking a chatbot questions where the generated answer happens to be correct, they are more likely to believe it next time, leading to more (misplaced) trust. Add to this incomplete or out-of-date training data and exaggerated evaluation claims, and it's clear that genAI is prone to produce unreliable information and always will be. 
    
 
## GenAI does nothing but hallucinate

*The paper mentions "hallucinations" 40 times in 8 pages of prose.*

It's worth mentioning that the core of all genAI models is fundamentally the same: they predict the next word in a sequence, based on previous analysis of a very large collection of text. So given a prompt, such as a question, they produce a response where each word is relatively likely given the prompt and the rest of the response up to that point. It is not trying to find the response that is "true", but merely one that is "useful" and will satisfy the user. (Similarly, visual perception didn't evolve to show us what is *really* out there, but merely what is *useful* to be out there based on our history. I wrote about [illusions and genAI hallucinations here](https://dcorney.com/thoughts/2023/02/20/illusions-hallucinations.html)). So when we look at the output and say, "Oooh, it got that bit wrong, it's hallucinating!" the model is doing exactly the same as when we say, "Wow, it's passed this medical exam!". It's *all* made up, but some of it happens to be true.

## What's the worst that could happen?

<img  src="/images/factuality/bypassing-detection.png" alt="Extract from paper:  GenAI tools can generate infinite variations of the same claim. Even if each variant reaches a small number of people, the cumulative impact of these variants could add to that of a highly viral piece while remaining invisible to fact-checkers." width="400" align="right"/>

One of the easiest and most alarming parts of the paper to write was to list out the bad things that could happen. One that particularly concerns me in my role at [Full Fact](https://fullfact.org/) is the potential for propagandists to generate endless variations of the same claim and sharing them via many different channels. The cumulative effect is the same: lots of people see the misleading content and some are influenced by it. But the diversity makes it harder to detect this as viral content, as each version is only seen by a few people. So fact checkers (and social media companies) might find it harder to identify harmful, impactful content.



## What can we do to fix this?


<img  src="/images/factuality/provenance.png" alt="As synthetic text generated by LLMs becomes ubiquitous, fully human-written text may become more valuable. Technologies and standards for content authenticity and provenance already exist for video and image content." width="400" align="right"/>

Thankfully, it's not all doom and gloom. GenAI providers who don't want to mislead their users can use RAG models, especially if tied to up-to-date knowledge bases, to reduce some forms of misleading hallucinations. And while automatic recognition of AI generated content remains hard, steps are being taken to allow authentic content to be associated with provenance information, so people (and tools) know it is trustworthy. Or at least, human-generated.


## Fact checking in this brave new world

<img  src="/images/factuality/transcripts.png" alt="LLMs can transcribe speeches, debates, interviews, online videos and news broadcasts, summarize extensive documents and help to create concise lists of crucial claims." width="400" align="right"/>


And the best news is that fact checkers can make direct use of this new technology! While genAI can't tell us if a claim is true, misleading or false, it can be used to scale-up media monitoring. For example, finding harmful claims in long videos or podcasts can take fact checkers hours. While accurate transcripts are available, spoken word tends to be quite repetitive, meandering, unstructured and repetitive. GenAI can help by providing readable summaries of long transcripts suitable for further analysis. So instead of ploughing through hours of low-quality videos, fact checkers can use AI to help them focus on the most likely suspects.



## Dual-edge sword
<img  src="/images/factuality/landscape.png" alt="The landscape of factuality in LLMs presents a dual-edged sword, encompassing both formidable challenges and promising opportunities for the domain of fact-checking." width="400" align="right"/>

As we conclude in the paper, "the landscape of factuality in LLMs presents a dual-edged sword, encompassing both formidable challenges and promising opportunities for the domain of fact-checking." There is a lot of hype. There are serious concerns about the environmental impact of these tools, the way the training data is collected and processed and the pollution of the information space we all rely on. But perhaps there are glimmers of hope amongst the clouds.


