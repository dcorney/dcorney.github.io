---
layout: post
category: explanation
title: Introduction
---

This project is a chance for me to explore and improve my knowledge of Python and some of its libraries, especially around AWS access and text analysis.

The first version here is centered around a bi-directional Markov chain process. This is created by analysing a number of pieces of English text: for each word, we extract the preceding few words and the following few words and count how often each sequence appears. We insert special tokens at the start and end of each sentence to mark the boundaries. To generate text, we can then start with an arbitrary word and add words before it and after it to build up a full sentence, stopping when we reach one of the special start/end sentence tokens. 

