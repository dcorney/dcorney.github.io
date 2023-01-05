---
layout: post
category: til
title: TIL - Symbol Grounding in Large Language Models
---

In their new essay [<i>Some remarks on Large Language Models</i>](https://gist.github.com/yoavg/59d174608e92e845c8994ac2e234c8a9), Yoav Goldberg reflects and expands on many recent ideas in the field. One part that caught my eye was a discussion of the [symbol grounding problem](https://en.wikipedia.org/wiki/Symbol_grounding_problem), namely how symbols, such as words, get their meaning. 

When people hype up LLMs as "intelligent", a common rebuttal is that they're just manipulating symbols with no <i>understanding</i> of what they mean. BERT may be able to predict the missing word in sentences like, "She turned to the next ____ in the book," as well as any human can. But the human will also have a host of related ideas and experiences about what paper feels like between their fingers, what their favourite book is, how much a book weighs, [how far one can throw a book](https://quoteinvestigator.com/2013/03/26/great-force/) and so on. 

So can large language models ever link symbols to their meaning? Yoav describes "instruction tuning" of LLMs, a form of supervised learning, and gives the example of prompting a model to "summarise this text" and then providing some text <i>and</i> a target summary. The meaning of the symbol "summarise" is captured by the training example, so arguably, the LLM could acquire a grounded symbol: it has direct experience of the symbol and its meaning. Nice!

So I'm now at least half-convinced that LLMs can ground symbols such as "summarise", "translate", "paraphrase" etc. -- symbols about textual manipulation. Presumably, it could learn to ground symbols such as "font" or "colour" or "blue" with suitable representation too. And that's a big step forward in symbol grounding! But is it a step towards a general grounding solution? Can supervised learning help an LLM to ground the symbol "floor" or "chair" or "dog"? Other than linking those symbols to pictures of the objects (which are just other symbols), I still can't see a way, other than a still sci-fi-like robot with AGI. Maybe one day...

