---
layout: post
category: explanation
title: Story generation vs. Text generation
---

Having spent some time playing with Markov chains for text generation, I thought I'd go back to the theory a bit to broaden my knowledge. I'd been hoping to generate a story, but wasn't sure of my next steps... I started by reading "A survey on story generation techniques for authoring computational narratives" [^1] which I found both readable and useful! One of the first things I realised is that all the work I've been doing on this project has been limited to generating the final surface-level form of the text, which is (roughly speaking) *discourse generation*. There's a whole set of other aspects that I'd been ignoring, such as: plot generation (a set of events); space generation (a set of characters, locations, props etc.); story generation (which is basically plot + space, i.e. events happening to particular characters in particular locations); and finally narrative generation (which is a story plus the *discourse*, i.e. the particular telling of a story). 

There are also references to many other papers that I now plan to track down and read, as and when time permits. But I already have a clearer, broader set of goals and I can start to see some data structures and functions I'll need, even if they're a bit hazy. For example, the *space* is basically a set of entities. I've already used Spacy.io (and Stanford's NER tools) to do named entity recognition, and store lists of people, organisations and places. I'll need to define 'props' somehow, but that should't be too hard. (Perhaps using POS tagging on some existing text, and extracting common nouns that are associated with people and active verbs??) 

I'll need functions to generate *events*, which may either be from fixed templates I can write, or I can try event extraction from novels, replacing the named entities with placeholders. Perhaps a function that parses the text and returns a template like **\<PERSON-1> gave \<ITEM-1> to \<PERSON-2> in \<LOCATION-1>**, where \<ITEM-1> is anything from a list ['bunch of flowers', 'suitcase full of cash', 'loaded gun'...]. It might be easier to extract such patterns from plot summaries on Wikipedia, rather than directly from the text...

Finally, I'll need functions that convert events (and other filled-templates) to the final surface-form of the text (*discourse generation*). Here's where the Markov-chain-based text generation I've done so far will be useful, but I'll need to add rather more contraints to the process.

Overall, this all strikes a chord with me, namely the need to combine both low- and high-level processes to generate interesting art. When dabbling with creative image generation years ago, I generated some nice patterns using some nature-inspired algorithms, but without high-level structure, the images got boring very quickly. Similarly, just generating text from Markov chains produces (almost!) readable sentences, but the text gets boring very quickly. Adding a sequence of events, consistent characters, ideally with motivations explaining their behaviours and so on will define the high-level structure which is as necessary as the low-level surface generation.




[^1]: Kybartas, B & Bidarra, R (2016). A survey on story generation techniques for authoring computational narratives. IEEE Transactions on Computational Intelligence and AI in Games.