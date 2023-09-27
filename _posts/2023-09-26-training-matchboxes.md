---
layout: post
category: thoughts
title: Training a small language model made from matchboxes
---

Recently, I taught a pile of matchboxes to generate novel sentences and [demonstrated it working](https://dcorney.com/thoughts/2023/09/23/matchboxes.html). This post provides more detail about how I trained the model in the first place. The end goal of training is to have a set of matchboxes, each representing one word from the training text. Each box contains the words that can immediately follow the word the box represents. The more copies of a word there are in a box, the more likely that word is to follow the box's word. Once trained, we can use the boxes to generate new text[^1].


## Getting going

First, I chose my training data. I picked the text of "Green Eggs and Ham" because it's quite short and has a famously small vocabulary of just 50 distinct words[^2]. Training by hand was always going to be a bit fiddly, and I didn't want to overdo it.

Second, I had to separate the text into sentences and into words. This is mostly as straightfowrard as it sounds, though I did decide that "Sam-I-Am" is one word rather than three, and that "Eat them! Eat them!" is two complete sentences, and even that "Say!" is a single sentence by itself. I then printed out the text and cut each sentence out as a single strip of paper.

Third, I found a set of empty matchboxes that [my wife](https://emmabyrne.net/) had left over from some earlier craft project. The same effect could be achieved with a set of envelopes to hold the slips of paper, but [matchboxes are canonical](https://en.wikipedia.org/wiki/Matchbox_Educable_Noughts_and_Crosses_Engine). I wrote **\<start\>** on one box and left the rest blank for now.

And then the fun can begin! I took the first sentence of the text, which happens to be: "I am Sam." I cut off the first word, "I", and put it into the **\<start\>** box. I then took the next blank box and wrote "I" on the top. The word "am" comes after "I", so I cut off "am" and put it in the **I** box. And I took another blank box and wrote "am" on it. I put the last word, "Sam" in the **am** box, because "Sam" comes after "am" in the sentence. And because "Sam" is followed by a full-stop, I stopped. First sentence complete!

At this point, if I wanted to generate a sentence using this model, I would proceed as follows: open the **\<start\>** box and take out a single word -- there's only one it there, "I". So I then go to the **I** box and take out one word -- it has to be "am". So I then go to the **am** box and take out one word -- "Sam." It has a full-stop, so we've finished, and our sentence reads "I am Sam." This is an exact copy of our training sentence, which is not very interesting. But it is reassuring that the boxes have "remembered" the sentence that they've been trained on.

I then went to the second sentence, which happens to be a repeat of the first. So after a bit more cutting and box-stuffing, the **\<start\>** box now has two slips reading "I", the **I** box has two copies of "am" and the **am** box has two "Sam."s in it. 

Then a little variety with sentence three: "Sam I am." I cut each word in turn, with "Sam" going in the **\<start\>** box, "I" going into a new box that I labelled **Sam**, and "am" going in the **I** box. 

If we look in the **\<start\>** box now, we'll find three bits of paper: two saying "I" and one saying "Sam". This is because two of our three sentences begin with "I" and one begins "Sam". But it also means that if we keep generating new sentences, two out of three would begin "I" and the rest with "Sam". We can now produce two novel sentences: "I am." and "Sam I am Sam." 

## Moving on

I carried on with the rest of the text, quickly reaching the classic line "Do you like green eggs and ham?" The video below shows me training MESLaM on this sentence, including labelling several news boxes.

{% include youtube.html id="fANs-il6XCI" %}

The next clip shows a later sentence being added, "Would you, could you, in the dark?":

{% include youtube.html id="ZAX8QkS9xCw" %}



## The training algorithm

If you prefer a more abstract view, here is some pseudocode showing the learning. Let's assume we've chosen some text, split it into sentences, and then split each sentence into a list of words. This function then puts the words into the appropriate matchboxes.

```
FUNCTION process_sentence(words) 
    i = 0
    DO
        this_word = words[i]
        IF i = 0
            INSERT this_word INTO box['start']
            next_word = words[i+1]
        ELSE
            IF NOT EXISTS box[this_word]
                WRITE this_word ONTO a new box
            INSERT next_word INTO box[this_word]
    UNTIL (this_word ENDS_WITH_ONE_OF [.?!])
```


## Putting it all together

It took me several hours (spread over several weeks) to process the entire book and train MESLaM, though I did get faster with practice. The film I made of myself cutting each word in turn and sticking them into the right boxes lasts about 2 hours. It is torture to watch! 
Instead, the final video here shows the entire training process, unedited, but sped-up to be about 5 minutes long. Enjoy!

{% include youtube.html id="MZ9S80wGPas" %}

<br>
----
[^1]: Or even to estimate the likelihood that a sentence is valid -- the defining characteristic of a language model. Lena Voita provides a clear explaination of calculating [How likely is a sentence to appear in a language](https://lena-voita.github.io/nlp_course/language_modeling.html). And going back a while, see also "The Series of Approximations to English" section in "[A Mathematical Theory of Communication](https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf)" by Claude Shannon, Bell Systems Technical Journal, 1948. 

[^2]: and 49 of them are monosyllabic!
