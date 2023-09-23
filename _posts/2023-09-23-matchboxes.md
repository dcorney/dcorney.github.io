---
layout: post
category: thoughts
title: matchbox thing
---

Over the last year or two, everyone has come across the phrase "large language models" and may have gasped at the thought that having 100 billion parameters is now seen as pretty standard. Well, I'm here to talk about small language models (SLMs) and one in particular that I've just built. I call it MESLaM, or Matchbox Educable Small Language Model. MESLaM consists of 35 white match boxes, each with a single word written on the top. Each box contains a few slips of paper and each slip has a single word written on it. The distribution of words in boxes was determined by the text of "Green Eggs and Ham" by Dr Seuss. And that's it: no computer, no wires, no AI. This model is not sentient. Let's look at the model and what it can do.


Here is a picture of MESLaM.
<img src="/images/matchboxes/35_match_boxes.jpeg" alt="35 white match boxes each with a word written on the top" width="250"/>

And here are some of the boxes opened to show their contents.

[ ] TODO photo some

## Generating text with MESLaM

One of the boxes is specially marked "\<start\>" and the slips of paper in this box show every word that can start a sentence, based on the training text. To generate a new sentence, we simply take a random slip of paper from this box and note the word. This is the first word of the new sentence. To generate each successive word, we open the box labelled with the current word and pick one slip at random. This continues until the new word also has a terminating punctuation mark (i.e. a full-stop, exclamation mark or question mark). 

Suppose the word drawn from the \<start\> box is "could". This defines the first word of the sentence. We then open the box labelled "could" to see what words can follow it, and pick one slip at random. Suppose we pick a slip labelled "not". That becomes the second word, and we need to open the "not" box to find what word can follow it. And so on. In the video below, the process continues until the slip labelled "anywhere." is drawn from the box labelled "them". The full-stop on the slip shows us it's the end of the sentence, giving us:

<font size="large">Could not like them anywhere.</font>

It's not going to win a [Geisel Award](https://www.ala.org/alsc/awardsgrants/bookmedia/geisel), but it is a proper sentence.

This is a preview

```markdown
[![Final video of fixing issues in your code in VS Code]
(https://img.youtube.com/vi/er3N7RB5-4Q/maxresdefault.jpg)]
(https://www.youtube.com/watch?v=er3N7RB5-4Q)
```

this is an embedding

{% include youtube.html id="er3N7RB5" %}


<br>
<br>

[^1]: fn1

[^2]: fn2