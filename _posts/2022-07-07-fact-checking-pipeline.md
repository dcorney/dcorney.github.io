---
layout: post
category: thoughts
title: Fact checking is NOT a pipeline
---

Crowdsourcing relies on the wisdom of the crowd: combining the opinions of lots of different people often gives very reliable data. But how many people do we need to ask? It turns out that this problem was solved more than 300 years ago in Switzerland by one [Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli).


I work in the automated fact checking area: using AI and NLP to develop tools to support fact checkers, in my case at [Full Fact](https://fullfact.org).
Over the last few years, I've read many papers and blog posts about the field, and written one or two myself. 
In many pieces, the scene is set by talking about the "fact checking pipeline". This model breaks down the task of fact checking, as carried out by expert fact checking journalists, into a series of discrete steps, with the aim of making it all easier to understand and potentially to automate, step by step. This is a laudable aim and is really useful for motivating research work in each area in turn.

But I'm increasingly convinced the pipeline is an oversimplification and that at some point, it will lead researchers up the wrong hill.


## The pipeline 

Here's my version of the fact checking pipeline, which subsumes plenty of examples I've seen. (An appendix below lists some specific examples with references.)

|<img src="/images/pipeline1.png" alt="fact checking as a pipeline" width="50%"/>

From the top: 
1. we collect some media which we'll assume is text (could be newspaper articles, FB posts, tweets, TV/radio transcripts, manifestos...).
2. Then we find *claims* in the text, meaning statements about the world that are either true or false.
3. Then we select or rank these claims for "checkworthiness", a clumsy but useful word, to prioritize which claims are actually worth fact checking.
4. Next is finding evidence related to the claim, from the web, Wikipedia, government data portals, private databases or wherever you trust. This may include deciding on the "stance" of a piece of evidence: does it support or contradict the claim?
5. Then the big one: deciding if the claim is actually true or false (or partly true, or mostly false or some other category.)
6. And finally, publishing the result and encouraging people to read it.

## Missing arrows

As always, reality is more complicated than this pipeline suggests. The temptation is to believe that by automating or scaling up one step, then the whole process gets a bit faster and a bit better.
But I believe that many of these stages depend on each other.

For example, one critical factor in deciding if a claim can be checked is the availablity of evidence. If there is no evidence with which to test a claim, it can't be tested. An experienced fact checker will often dismiss a claim as being not worth spending time checking because they know that suitable evidence is unavailable. So you can't just begin evidence gathering after deciding a claim is worth checking, but rather may need to revisit that decision. 

Many versions of the pipeline I've seen omit the last step completely, seeing "publish" as a trivial task that existing tools have already solved (email, blog posts, CRMs, etc). But fact checkers are journalists aiming to tell stories that communicate complex issues to a broad audience. It’s not just a case of clicking "post": checkworthiness and explanation are both influenced by the nature of the audience: is this for the general public? For a specific community? For interested or motivated parties, who already have a lot of background knowledge? Knowing who the audience is for this particular fact check will influence whether it is worth checking at all, and perhaps what kind of evidence is required.



