---
layout: post
category: thoughts
title: Automated fact checking
---

I've spent quite a bit of time recently thinking about fully-automated fact checking. In particular, given a sentence, can we extract enough information from it to be able to verify this claim against some trusted data source? This is certainly possible in at least some cases: we have a working prototype at Full Fact, but it has a limited range.

So this raises a question: what are the theoretical limits of automated fact checking? Setting aside the possibility of general AI, how many claims made in public could be verified against trusted sources, if we had a "perfect" NLP/information extraction tool? 

One way to think about this is to consider the reverse process. Instead of algorithmically going from a textual claim, to extracted information, to verification against trusted data, what happens if we start from trusted data, add information and produce a textual claim? This is robo-journalism! And it's been around for a few years.

So the number of potential automatable fact-checks can be seen as (approximately) equivalent to number of potential robo-journalist articles. While good results can be achieved generating articles from sports results, weather reports, earthquake reports, some finance/business results, one wouldn't necessarily expect good robojournalism articles about more complex stories, or ones which require a lot of background knowledge or commmon sense to understand.  