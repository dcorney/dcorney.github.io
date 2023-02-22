---
layout: post
category: thoughts
title: Generative AI, hallucinations and illusions
---

I was struck recently by similarities between the way GPT-3 generates unreliable information and the way we perceive the world around us. Both are attempts to use probabalistic reasoning over ambiguous and incomplete data. Both work well, most of the time, at least superficially -- but sometimes lead to hallucinations (perceptions without sensory input) or illusions (misinterpretations of sensory input). 

## Optical illusions 

I did some research into optical illusions a few years ago -- what are they? why do we see them? how universal are they? -- in a visual & computational neuroscience lab. 
In [one paper](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.0030180), we argued that all visual stimuli are massively ambiguous, and that our visual systems (think "eyes + brain") work hard to resolve that ambiguity into the single interpretation that is most likely, based on our previous experience. We defined illusions as "the condition in which the true source of a stimulus differs from what is its most likely (and thus perceived) source." 

For example with the [simultaneous contrast illusion](https://en.wikipedia.org/wiki/Contrast_effect), the two inner grey blocks are physically identical, but the darker or lighter surrounding context makes them look lighter or darker, respectively. We trained some (very small) neural networks to estimate the brightness of grey blobs under different lighting conditions and despite achieving very high accuracy, they also showed consistent patterns of mistakes. We demonstrated that these were equivalent to the human perception of illusions.

<img src="https://upload.wikimedia.org/wikipedia/commons/0/0a/Simultaneous_Contrast.svg" alt="simultaneous contrast illusion" title="Simultaneous Contrast Illusion"   width="250" class="center"> 

Why do we see these illusions? When both humans and machine learning models see a mostly bright field of vision (like the bottom half of the image), it is consistent with a strong source of light. Under a bright light, the only way a surface can reflect only a modest amount of light is if it is a very dark, low-reflectance surface. So we perceive it as a dark shade of grey. Conversely, when we see a largely dark field of vision (the top half of the image), it's consistent with low light levels, and the only way something can still reflect plenty of light is if it is a very light, highly reflective surface - so we see the <i>same</i> grey pixels as if the were much <i>lighter</i>.

We use our past experience of resolving ambiguous scenes to make sensible estimates about what is actually in front of us. And when what is actually in front of us differs from the most likely explanation in our experience, that discrepancy is what we call an illusion.

## Hallucinating text

The tendency for text-generating AI models, such as ChatGPT and GPT-3, to produce content that bears little relation to the truth has been widely observed. Some ([including me](https://dcorney.com/thoughts/2023/01/15/gpt3-considered-harmful.html)) call the output "bullshit" while others, [including OpenAI](https://openai.com/blog/instruction-following/), prefer to call these "hallucinations". Carl Bergstrom argues that '[Your chatbot is not "hallucinating"](https://post.news/article/2Lr2DCy9lQz0pbzrVwrtgBD6I81)' because this behaviour isn't a pathology -- it's baked into the design of LLMs. 

So how do generative AI models produce text? Essentially, they repeatedly have to choose what word goes next in the sequence, over and over again to build up the output. They will choose the most probable word[^1] based on the preceding words and the wider context, based on their internal probability distributions. These are derived from their training sets and then encoded in the millions of parameters that form their neural network[^2]. 

Suppose that during training, the model read the sequence "love is all" 100 times from various sources. Suppose the next word was "around" 75 times, "you" 20 times and a full stop marking the end of a sentence 5 times. If this model is then used to generate text, and has to continue the sentence "Love is all ...," it will add the word "around" roughly three times out of four. There's no right or wrong word to add next: the model just considers all the words that might come next, and chooses one that seems likely[^3].


## It's disambiguation all the way down

Suppose we play a (very boring) parlour game, where I read out one word at a time from a book and you have to constantly guess the next word. If I say "The cat sat on the ..." you'd be very sensible to guess "mat". And you'd be right, 99% of the time. If you see a grey blob in a bright space, you'd be very sensible to guess it's almost black, and you'd be right 99% of the time. And when you (implicitly) ask GPT-3 what the next word in the sentence is, it is also "right", inasmuch as whatever word it chooses has been seen in that place in similar sentences in its past experience (i.e. its training data). 

But in the parlour game, if I then show my next word was actually "aeroplane", then sure, "mat" was the wrong guess, but no one can blame you for guessing it. It was a perfectly reasonable thing to guess. And optical illusions are not caused by inattention, inexperience or misbehaving neurons -- they're caused by the ambiguous nature of visual scenes and our attempts to disamiguate them. While we may be technically wrong in our perception, they are nonetheless perfectly rational.

So I'd say that GPT-3 does an amazing job of constructing fluent text, based on its past experiences and a given prompt. That's what it has been designed to do and it does it well. If we then choose to believe that text is true, then more fool us. What's not clear to me is how whether there are any patterns to the "hallucinations", when ChatGPT produces clearly false output. Are these triggered by particular prompts, such as trick questions or misleading context? Or do they also happen when responding to more organic or innocent prompts?


<br>
<br>


----

Related reading:

ChatGPT as ["blurry JPEGs"](https://www.newyorker.com/tech/annals-of-technology/chatgpt-is-a-blurry-jpeg-of-the-web)


[^1]: Either "most probable", or sampling according to the stored probability distribution to produce a more varied output.
[^2]: They probabilities can be stored in other ways, like a [bidrectional Markov Chain](https://dcorney.com/Posts/) - something I was playing with for text generation a few years ago.
[^3]: This is a massive simplification of course; modern large language models consider the vectorised semantics of words, and so will choose words that are highly probable in terms of both syntax and semantics. But the principle is the same.


