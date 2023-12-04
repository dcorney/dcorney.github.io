---
layout: post
category: thoughts
title: What makes a claim worth checking?
---


As a species, we tell stories and share information all the time. But when we're given bad information, we make bad decisions. 
So when a statement made in public is wrong it may be worth considering for fact checking, especially if it may cause harm. My fact-checking colleagues at [Full Fact](https://fullfact.org) spend time every day deciding which claims to focus on. We fact check around [800 claims per year](https://fullfact.org/latest/), which is to be celebrated -- but covers only a tiny fraction of all the questionable claims being made.

Given the scale of the problem, factchecking is an obvious candidate for [automation including AI](https://fullfact.org/about/ai/). Here I want to explore some of the differences between human fact checking and automated fact checking, and in particular to consider what "check-worthy" means in different contexts.

## What makes a claim check-worthy?

Whenever I ask fact checkers how they decide what to check, they always give the same answer: "It's complex!" But the most common factors include the potential harm of the bad information; the believability of the claim; the potential reach of the claim; the audience interest in reading a fact-check article; and the time it would take to check the claim. These are all quite nuanced factors and rely on the expertise of fact checkers to judge. It's not a simple question of how many shares a claim has received or how many followers the claimant has. Nor can they wait to see the impact of bad information - part of the goal is to slow or stop it spreading in the first place.

For automated fact checking, it's a bit different and depends heavily on the goals. For example, some tools are designed to check the output of AI chatbots and search engines. If someone has asked ChatGPT a question, then the answer is presumably important to them - and so any claims in it are worth checking by definition. The same applies to search engine results: if a search engine only links to or summarises information that is verified as true, then that would serve its users greatly. The truth is that someone, somewhere probably cares about almost any claim that has been made. 

But not every bit of text can be checked by machines or humans. Predictions about the future; claims about someone's personal beliefs; and statements that aren't making any claim about the world, do not have any accessible "truth value" and so are unverifiable.


##  How many claims can be checked?

It takes hours, or even days, to fully investigate and write about a single claim if the result is going to be trusted. Depending on the claim, it may be necessary to find and speak to experts; find and read official reports and data; carefully examine complex arguments; perform reverse image search etc. To carry out that research, and then explain it clearly so that the audience can understand it and form their own opinions, requires skill and time. Of course, some claims are relatively trivial to investigate or are common knowledge, in which case fact checkers would tend to focus elsewhere. 

Some claims can be checked by simple reference to a trusted document or website. The [ONS](https://www.ons.gov.uk/) can provide current and historic rates of inflation; the Academy can tell you who won which Oscar in which year. So to the extent that fact checking can be fully automated, then these types of claim can often be checked in the time it takes to perform a few web or database queries, and spin a few CPU cycles. With ever cheaper cloud computing, thousands or even millions of these claims can be checked every second. But is this useful?

One of the guiding principles of fact checking organisations like Full Fact is to be absolutely reliable: we don't speculate or guess or go with our instincts, nor do we make assumptions about our readers' prior knowledge. Instead, we rigorously examine evidence and present the facts as clearly as we can and let our readers make their own minds up. Everything is double- or triple-checked for errors, biases, ambiguities that may mislead. In contrast, the best automated systems continue to make mistakes. Errors can creep in at any stage, such as trusting an incorrect website or misinterpreting complex statements. Even if such a system was 90% accurate, it might still make millions of mistakes every day, so its output could never be quite trusted. Perhaps it doesn't really matter if a tool insists that [It’s a Wonderful Life](https://www.oscars.org/events/its-wonderful-life-1946)  won 5 Oscars or that [Mahatma Gandhi never met Charlie Chaplin](https://www.newhamheritagemonth.org/records/chaplin-gandhi-canning-town/). But if it also tells you that covid vaccines are dangerous or that you're not eligible to vote, then the consequences could be serious.


## What claims can be checked and how?

A skilled journalist performing fact checking can be aware of claims that are misleading due to missing context, or are technically correct but misleading, perhaps by cherry-picking the evidence. They can ask an expert for their opinion, ask the person making the claim what they really meant, identify the implications of ambiguous statements and predict the likely harm of bad information on ordinary people.

For automated fact checking tools to work, they need access to some ground truth. This could be a pre-defined internal database of known truths, or a list of trusted sources such as Wikipedia. Or they can rely on a web search and attempt to consolidate a variety of answers and derive the agreed stance: do most people say this claim is true or false? This has obvious limitations, especially when it comes to breaking news, when multiple news sources might be relying on the same source or sharing the same speculation. 

## What about ChatGPT and generative AI?

These continue to be hot topics of research and are already having a [massive impact on the information available online](https://arxiv.org/abs/2310.05189).
One of the biggest weaknesses of text-generating AI are what the industry refer to as "hallucinations" and what used to be called "mistakes". By the very nature of generating novel text, the output will often contain errors. And as noted above, performing reliable fact checking requires skilled people (who would probably be better at writing the output in the first place...). So some people are developing AI chatbots whose answers are limited to pre-defined sets of verified statements, essentially making the chatbot an easy-to-use interface to a traditional search engine. And others are developing tools to [automatically verify, and even correct, the output of ChatGPT](https://arxiv.org/abs/2311.09000). While this will no doubt improve, it's hard to see how a general statement on any topic can ever be 100% reliably verified by any form of AI.


## Conclusion: horses for courses

The gold standard of trustworthy, informative and impactful fact checking, as carried out by Full Fact and similar organisations (including other members of the [IFCN](https://www.poynter.org/ifcn/)), requires significant skill and time. It makes sense to focus these efforts on the most complex, nuanced claims and those most likely to cause harm. Automated fact checking remains a subject of active research, where the best results are not quite reliable and claims whose answers can't be found on the open web can't be checked at all. 

I believe that automated fact checking will become increasingly important to improve the quality of search engine results and the quality of output from genAI tools including ChatGPT. But for the foreseeable future, the work of human fact checkers will remain vital to hold politicians to account and to help protect us all from harmful bad information.

So the question of "is this claim worth checking?" can never have a universal answer: it depends on the resources available and what the goals of fact checking are.

