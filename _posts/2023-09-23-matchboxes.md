---
layout: post
category: thoughts
title: A small language model made from match boxes
---

Over the last year or two, everyone has heard about "[large language models](https://en.wikipedia.org/wiki/Large_language_model)" and their use in tools like ChatGPT.  Well, I'm here to talk about small language models (SLMs) and one in particular that I've just built. I call it MESLaM, or **M**atchbox **E**ducable **S**mall **La**nguage **M**odel. MESLaM consists of 35 plain match boxes, each with a single word written on the top. Each box contains a few slips of paper and each slip has a single word written on it. The distribution of words in boxes was determined by the text of "Green Eggs and Ham" by Dr Seuss. And that's it: no computer, no wires, no AI. Let's look at the model and what it can do.

% You may have even gasped at the thought that having 100 billion parameters is now seen as pretty standard.

Here is a picture of MESLaM.
<img src="/images/matchboxes/35_match_boxes.jpeg" alt="35 white match boxes each with a word written on the top" width="250"/>

And here are some of the boxes opened to show their contents.

[ ] TODO photo some: "a" - lots of nouns; "green" only ever 'eggs'; + one other

## Generating text with MESLaM

One of the boxes is specially marked "\<start\>" and the slips of paper in this box show every word that can start a sentence, based on the training text. To generate a new sentence, we simply take a random slip of paper from this box and note the word. This is the first word of the new sentence. To generate each successive word, we open the box labelled with the current word and pick one slip at random. This continues until the new word also has a terminating punctuation mark (i.e. a full-stop, exclamation mark or question mark). 

Suppose the word drawn from the \<start\> box is "could". This defines the first word of the sentence. We then open the box labelled "could" to see what words can follow it, and pick one slip at random. Suppose we pick a slip labelled "not". That becomes the second word, and we need to open the "not" box to find what word can follow it. And so on. In the video below, the process continues until the slip labelled "anywhere." is drawn from the box labelled "them". The full-stop on the slip shows us it's the end of the sentence, giving us:

> <i>Could not like them anywhere.</i>


It's not going to win a [Geisel Award](https://www.ala.org/alsc/awardsgrants/bookmedia/geisel), but it is a proper sentence and it was written by MESLaM.

[![Final video](https://img.youtube.com/vi/er3N7RB5-4Q/0.jpg)](https://www.youtube.com/watch?v=er3N7RB5-4Q)

or:

{% include youtube.html id="er3N7RB5-4Q" %}

direct embedding version

<iframe width="560" height="315" src="https://www.youtube.com/embed/er3N7RB5-4Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Training the model

In a later post, I'll explain the training process in plenty of detail, but the outline is simple enough. Each box should end up with all the words that can follow the word written on the box. The more copies of a word that are in the box, the more likely that word is to come next.

To do this, you'll need some training text, divided into sentences with each one on a strip of paper. You'll also need a pile of blank, empty matchboxes. Write "\<start\>" on one of these.

Then for each sentence:

1. Put the first word into the special "\<start\>" box. 
2. Find a box with this word on the label. If there isn't one then write it on a new, empty matchbox.
3. Put the next word into this box.
4. If the word ends the sentence, stop. Otherwise go back to step 2.

So after training with the sentence:

> "Do you like green eggs and ham?"

the boxes should look like this:

| Box label | Contents |
| :-------- | :------- |
| \<start\> | do       |
| do        | you      |
| you       | like     |
| like      | green    |
| green     | eggs     |
| eggs      | and      |
| and       | ham?     |

Note that there is no box labelled "ham" because we've never seen a word follow "ham" so have no information about what would go in the box.

## Why did I do this?

My original motivation was concern that some people were so overwhelmed by ChatGPT that they genuinely believed it was sentient. Plenty of others have claimed it is at least a signficant step towards artificial general intelligence - you know, proper AI. I wanted to demonstrate that generating text, even fluent text, does **not** require any sort of intelligence. At all. 

## Extensions

I know that the text MESLaM produces is rather less impressive than ChatGPT. How could it be made better? 

* n-grams

## Background reading

Donald Michie's [Menace](https://people.csail.mit.edu/brooks/idocs/matchbox.pdf)


<br>
<br>

[^1]: fn1

[^2]: fn2