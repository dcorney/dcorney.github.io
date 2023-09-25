---
layout: post
category: thoughts
title: Traing a small language model made from matchboxes
---

Recently, I taught a pile of matchboxes to generate novel sentences and demonstrated it working. Here's a bit more about how I trained the model in the first place.



Here is some pseudocode showing the learning. Let's assume we've chosen some text, split it into sentences, and then split each sentence into a list of words. This function then puts the words into the appropriate matchboxes.

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

- [ ] insert video here + talkthrough of it