---
layout: post
category: thoughts
title: Does using LLMs as fact checkers make things better or worse?
---

TL;DR: Worse. 

I've been developing AI tools to support (human) fact checkers for several years now. The [tools that Full Fact produces](https://fullfact.ai/) are now used every day by fact checkers [around the world](https://fullfact.org/blog/2024/dec/full-fact-ai-supports-african-fact-checkers/) to help monitor the media and find claims that might be worth checking, and to find repeats of known falsehoods. This helps them hold to powerful people to account and to push back against misinformation. 

But one thing we have consistently avoided is using AI to actually check facts. With [hallucinations](https://rdcu.be/dRFy0), [bullshit](https://link.springer.com/article/10.1007/s10676-024-09775-5) and obscurity, it's hard to trust the output of ChatGPT (or its rivals) in a factual sense. They may or may not be useful for creative work, but if I don't already know the answer to a question then I'm not going to ask an LLM. Their output is limited to the statistically most likely sequence of words based on whatever websites they scraped, so every output should be prefaced with the phrase, "According to some random dude on Reddit..." 

I recently came across a new paper[^1] which directly investigates the use of LLMs as fact checkers. Many LLM papers depend on unreliable benchmarks so I was excited to read they recruited 2159 actual human participants for the study: real people using real tools, not just some indirect or arbitrary measure of performance.

The participants were shown a series of headlines, some true and some false. They were also shown related fact check articles, some created by human fact checkers and some by ChatGPT. The participants behaviour was modelled by asking them whether they believed the headline or whether they would be happy to share it on social media. (There's a lot more complexity to the methods used -- [read the paper, it's great!](https://arxiv.org/abs/2308.10800) -- but that's the gist of it.)

So what happened? From the abstract:
>...the AI fact-checker is harmful in specific cases: it decreases beliefs in true headlines that it mislabels as false and increases beliefs in false headlines that it is unsure about. On the positive side, AI fact-checking information increases the sharing intent for correctly labeled true headlines.
So while they sometimes help, ChatGPT directly encourages false beliefs. This is a Bad Thing, I hardly need say.

I think part of the issue is the psychology of uncertainty. [Bayesian probability](https://en.wikipedia.org/wiki/Bayesian_probability) quantifies beliefs on a scale from 0 ("I definitely believe this is false") to 1 ("I 100% believe this is true")[^2]. Suppose you read a headline that sounds a bit suspicious to you, and so you assign it a belief score of 0.1 (meaning you're 90% sure it's false). If a friend then says, "No actually, it's true!" you would update your belief, perhaps up to 0.7 or 0.8, depending on how much you trust your friend. But what if instead they say, "I don't know -- it might be true or it might not." It <i>seems</i> like there's no information there and so logically, your belief shouldn't change either way. But I think that often it's enough to make you doubt the strength of your initial skepticism. You think, "This friend says it <i>might</i> be true. Maybe they're right." And so your belief score goes up from 0.1 to maybe 0.2 or 0.3. So you're still skeptical but less sure.

And it works the other way: if you're pretty sure the original headline or claim is true and someone you trust says, "I don't know -- it might be true or it might not," that might be enough to sow a seed of doubt, reducing the strength of your belief, at least a bit.

So on one hand, it's great when AI tools can say "I don't know" instead of giving a false sense of confidence. But I think in this case, just introducing some uncertainty can pull people's beliefs towards the mean, a Bayesian 0.5. If people's original interpretation of a headline is roughly correct[^3], then a chatbot just shrugging its metaphorical shoulders will actively make things worse by reducing the strength of that initial belief. Taken across many people and many claims, it results it people being more likely to share claims they correctly believed to be false, and less likely to share claims they correctly believed to be true. So the information space gets a little bit worse.

Of course this is not a complete answer: human psychology is massively complicated, barely understood and varies widely. And the interaction of that complexity with the complexity of AI makes outcomes even harder to predict. But I feel my own belief that LLMs do not make reliable fact checkers has been strengthend by reading this paper.


<br>

----

[^1]: DeVerna, M. R., Yan, H. Y., Yang, K.-C., & Menczer, F. (2024). Fact-checking information from large language models can decrease headline discernment (arXiv:2308.10800). arXiv. [https://doi.org/10.48550/arXiv.2308.10800](https://arxiv.org/abs/2308.10800) (Currently under review at PNAS.)

[^2]: These scores are a convenient way to model the strength of a belief and not numbers that actually exist in anyone's head.

[^3]: and people are not stupid, generally 
