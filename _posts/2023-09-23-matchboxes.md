---
layout: post
category: thoughts
title: A <i>small</i> language model made from matchboxes
---

[draft post]

Over the last year or two, everyone has heard about "[large language models](https://en.wikipedia.org/wiki/Large_language_model)" and their use in tools like ChatGPT.  Well, I'm here to talk about small language models (SLMs) and one in particular that I've just built. I call it **MESLaM**, or **M**atchbox **E**ducable **S**mall **La**nguage **M**odel[^1]. MESLaM is a set of matchboxes, each with a word on top and each filled with little bits of printed paper. The set of words in each box was chosen to reflect the text of "Green Eggs and Ham" by Dr Seuss. And that's it: no computer, no wires, no AI. Let's look at the model and what it can do.

<img  src="/images/matchboxes/35_match_boxes.jpeg" alt="35 white matchboxes each with a word written on the top" width="250" align="right"/>

First, here is a picture of MESLaM. MESLaM consists of 35 plain matchboxes, each with a single word written on the top. Each box contains a few slips of paper and each slip has a single word written on it. 

Below are some of the boxes opened to show their contents.


|                                                                                                                                                                             |                                                                                                                                                        |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="/images/matchboxes/contents_green.JPG" alt="a matchbox with the word 'green' written on top, open to show the word eggs on multiple slips of paper" width="300"/> | The box *green* contains just the word 'eggs' over and over again because in our text, the word "green" is always followed by "eggs".                  |
| <img src="/images/matchboxes/contents_start.JPG" alt="a matchbox with the word 'start' written on top, open to show many words on slips of paper" width="300"/>             | *\<start\>* contains lots of different words, as the training sentences often start with "would" or "could" but some started with "I", "And" or "Not". |
| <img src="/images/matchboxes/contents_and.JPG" alt="a matchbox with the word 'and' written on top, open to show the word many words on slips of paper" width="300"/>        | The *and* box contains lots of "ham" but also "I", "on", "you" and others.                                                                             |
| <img src="/images/matchboxes/contents_a.JPG" alt="a matchbox with the word 'a' written on top, open to show the word many words on slips of paper" width="300"/>            | The word "a" is followed by lots of different nouns, including "mouse", "train", and "fox". Some appear multiple times.                                |
{:.narrow_table}


## Generating text with MESLaM

One of the boxes is specially marked "*\<start\>*" and the slips of paper in this box show every word that can start a sentence, based on the training text. To generate a new sentence, we simply take a random slip of paper from this box and note the word. This is the first word of the new sentence. To generate each successive word, we open the box labelled with the current word and pick one slip at random. This continues until the new word also has a terminating punctuation mark (i.e. a full-stop, exclamation mark or question mark). 

Suppose the word drawn from the *\<start\>* box is "I". This defines the first word of the sentence. We then open the box labelled "*I*" to see what words can follow it, and pick one slip at random. Suppose we pick a slip labelled "do". That becomes the second word, and we need to open the "*do*" box to find what word can follow it. And so on. In the video below, the process continues until the slip labelled "tree." is drawn from the box labelled "*a*". The full-stop on the slip shows us it's the end of the sentence, giving us:

> <i>I do not like them in a tree.</i>

It's not going to win a [Geisel Award](https://www.ala.org/alsc/awardsgrants/bookmedia/geisel), but it is a proper sentence and it was written by MESLaM.

And here's a video of MESLaM producing exactly that sentence:

{% include youtube.html id="KKVvI-7yiSA" %}


Here's another video of MESLaM generating the sentence ["Could not like them anywhere."](https://youtu.be/er3N7RB5-4Q).

And here's a much longer sentence it made, ["And I do so like them here they are so good, you may like them with a tree!"](https://youtu.be/tSH2fgwyB08).



## Training the model

In a later post, I'll explain the training process in plenty of detail, but the outline is simple enough. The goal is fill each box with the words that can immediately follow the word written on top of the box. The more copies of a word that are in a box, the more likely that word is to be selected as the next word.

To train MESLaM, I split the text of [Green Eggs and Ham](https://en.wikipedia.org/wiki/Green_Eggs_and_Ham)[^2] into sentences. The first word of each sentence went into the *\<start\>* box.  I also wrote that word on a new box, if there wasn't already a box with that label. Then into each box I put the word that comes next, working my way through each sentence in turn. So after training with the sentence:

> "Do you like green eggs and ham?"

the boxes look like this:

| Box label | Contents |
| :-------: | :------: |
| \<start\> |    do    |
|    do     |   you    |
|    you    |   like   |
|   like    |  green   |
|   green   |   eggs   |
|   eggs    |   and    |
|    and    |   ham?   |
{:.border_table}

Note that there is no box labelled "ham" because we haven't seen a word follow "ham" so have no information about what to put in the box. If we continued training with the sentence "Well, do you?" then the *\<start\>* box would contain "do" and "well" and the *do* box would contain "you" twice, once with a question mark. As shown in the photos above, every instance of the word "green" in our training data is followed by the word "eggs"; so the box **green** contains nothing but multiple copies of the word "eggs".

## Why did I do this?

My original motivation was concern that some people were so overwhelmed by ChatGPT that they genuinely believed it was sentient. Plenty of others have claimed it is at least a signficant step towards artificial general intelligence - you know, proper AI. I wanted to demonstrate that generating text, even fluent text, does **not** require any sort of intelligence. At all. 

Also, I am a nerd. Hello!

## Extensions

The text that MESLaM produces is rather less impressive than ChatGPT. How could it be made better? 

* n-grams
* more training data


<br>
<br>

[^1]: The name is a large nod to Donald Michie's MENACE, short for [Matchbox Educable Noughts and Crosses Engine](https://en.wikipedia.org/wiki/Matchbox_Educable_Noughts_and_Crosses_Engine). His [main paper on it](https://people.csail.mit.edu/brooks/idocs/matchbox.pdf) is from The Computer Journal, 1963. Yes, it's 60 years old! He demonstrated that a set of matchboxes with coloured beads could *learn* how to play a decent game of noughts and crosses (tic-tac-toe).

[^2]: The main reason for choosing "Green Eggs and Ham" is that it only has 50 words. Each matchbox defines the words that can follow it, and quite a few words only appear at the end of a sentence, so we end up with 34 boxes, including the extra \<start\> box.