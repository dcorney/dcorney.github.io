---
layout: post
category: thoughts
title: "Bad information" is not the same as "bad writing"
---

I've lost count of the number of papers I've read that implicitly equate "bad information" with "bad writing", and each one makes me a little crosser than the last. 

The motivation is a good one: finding bad information (misinformation, disinformation, hyperpartisan content, hate speech etc.) so it can be flagged and avoided helps make everyone's information space cleaner[^1].  And the first thing we may notice when working in this space is that lots of low-quality content is very badly written. We've all seen clickbait headlines with lots of exclamation marks, badly punctuated hate speech, Conspiracy Theories with Weird Capitalizations and so on.

So the next step seems clear: we collect those examples and label them as "bad"; for the "good" information set, we just scrape a few thousand articles from trusted news sources, maybe the BBC, CNN, WSJ, NYT and so on. Then we train a model on that using various 'stylometric' features, such as frequency of stopwords, n-grams, PoS tags and so on. With the usual bag of tricks available in the NLP/ML space, we can easily built a model with pretty impressive accuracy on a hold-out test set. And with large language models we may not even know what features it's using.

But these models don't make it into production[^2] as far as I know -- please tell me if I've missed any! -- because they fail in both directions. They tag as "good information" anything that has been written by a skilled writer perhaps with the help of a skilled editor, even if it is full of (nicely worded) hate speech or (carefully written) disinformation. And the sloppy journalism-in-a-hurry that even the best outlets produce from time to time will also be tagged "good information". And coming the other way, a blog post or an article in a small trade magazine written by a domain expert that may not have been edited professionally and may have a few typoes and odd typography while still being perfectly reliable and conveying important information, will get tagged as "bad information". 


In effect, our model has just implicitly recreated the editorial style guides of major news outlets. This is NOT a reliable way to find bad information.

Thank you for reading. I feel better now.


----
[^1]: I'll acknowledge then skip over the important issue of censorship here.
[^2]: It's possible such models may have been effective about 10-15 years ago, but serious producers of bad information have quickly realised that they need to look good. Using a spell-checker and a modern web site design is a cheap way to gain a veneer of credibility.
