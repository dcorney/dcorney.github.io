---
layout: post
category: thoughts
title: Does Generative AI hallucinate or perceive illusions?
---

I was struck recently by similarities between the way GPT-3 generates unreliable information and the way we perceive the world around us. Both are attempts to use probabalistic reasoning over ambiguous and incomplete data. Both work well, most of the time, at least superficially -- but sometimes lead to "hallucinations" or illusions.

## Optical illusions 

I did some research into optical illusions a few years ago -- what are they? why do we see them? how universal are they? -- from a computational neuroscience perspective. 
In [one paper](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.0030180), we argued that all visual stimuli are massively ambiguous, and that our visual systems (think "eyes + brain") work hard to resolve that ambiguity into the single interpretation that is most likely, given our previous experience. We defined illusions as "the condition in which the true source of a stimulus differs from what is its most likely (and thus perceived) source." 

For example with the [simultaneous contrast illusion](https://en.wikipedia.org/wiki/Contrast_effect), the two inner grey blocks are physically identical, but the darker or lighter surrounding context makes them look lighter or darker, respectively. We trained some (very small) neural networks to estimate the brightness of grey blobs under different lighting conditions and despite achieving very high accuracy, they also showed consistent patterns of mistakes. We demonstrated that these were equivalent to the human perception of illusions.

![simultaneous contrast illusion](https://upload.wikimedia.org/wikipedia/commons/0/0a/Simultaneous_Contrast.svg)    

When both humans and machine learning models see a mostly bright field of vision, it is consistent with a strong source of light. Under a bright light, the only way a surface can reflect only a modest amount of light is if it is a very dark, low-reflectance surface. So we perceive it as a dark shade of grey. Conversely, when we see a largely dark field of vision, it's consistent with low light levels, and the only way something can still reflect plenty of light is if it is a very light, highly reflective surface - so we see the <i>same</i> grey pixels as if the were much <i>lighter</i>.

We use our past experience of resolving ambiguous scenes to make sensible estimates about what is actually in front of us. And when what is actually in front of us differs from the most likely explanation we come up with from our experiences, that discrepancy is what we call an illusion.

## Hallucinating text

The tendency for text-generating AI models, such as ChatGPT and GPT-3, to produce content that bears little relation to the truth has been widely observed. Some ([including me](https://dcorney.com/thoughts/2023/01/15/gpt3-considered-harmful.html)!) call the output "bullshit" while others, including OpenAI, prefer to call these "hallucinations". Carl Bergstrom argues that '[Your chatbot is not "hallucinating"](https://post.news/article/2Lr2DCy9lQz0pbzrVwrtgBD6I81)' because this behaviour isn't a pathology - it's baked into the design of LLMs. 

How do generative AI models produce text? Essentially, they repeatedly have to choose what word goes next in the sequence, over and over again. They will choose the most probable word[^2] based on the preceding words and the wider context, based on their internal probability distributions. These are encoded in the millions of parameters that form the neural network[^3], and derived from their training sets. 


## Disambiguation

Suppose we play a (very boring) parlour game, where I read out one word at a time from a book and you have to constantly guess the next word. If I say "The cat sat on the ..." you'd be very sensible to guess "mat". And you'd be right, 99% of the time. If you see a grey blob in a bright space, you'd be very sensible to guess it's almost black, and you'd be right 99% of the time. And when you (implicitly) ask GPT-3 what the next word in the sentence is, it is also "right" 99% of the time, in as much as the word it guesses comes next has been used in that place in similar sentences in it's past experience (i.e. its training data). But in the parlour game, if I then show my next word was actually "aeroplane", then sure, "mat" was the wrong guess, but no one can blame you for guessing it. It was the rationally optimal thing to guess. And optical illusions are not caused by inattention, carelessness or inexperience - they're caused by the ambiguous nature of visual scenes and our attempts to disamiguate them. While we may be techically wrong in our perception, they are nonetheless rationally optimal.

So I'd say that GPT-3 does an amazing job of constructing fluent text, based on its past experiences. If we then choose to believe that text is true, then more fool us.
ß

<br>
<br>


----

[^1]: Though Carl Bergstrom argues that '[Your chatbot is not "hallucinating"](https://post.news/article/2Lr2DCy9lQz0pbzrVwrtgBD6I81)' because it isn't a pathology - it's baked into the design of LLMs.



[^2]: Either "most probable", or sampling from the probability distribution to produce a more varied output. Probably.
[^3]: They probabilities can be stored in other ways, like a [bidrectional Markov Chain](https://dcorney.com/Posts/) - something I was playing with for text generation a few years ago.

Related reading:

ChatGPT as ["blurry JPEGs"](https://www.newyorker.com/tech/annals-of-technology/chatgpt-is-a-blurry-jpeg-of-the-web)

