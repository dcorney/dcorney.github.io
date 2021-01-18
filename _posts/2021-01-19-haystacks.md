---
layout: post
category: thoughts
title: How to find a needle in a haystack using machine learning
---

This is a bit of a rant about one problem I've been working on for a while: claim matching. But it applies to any task with very unbalanced data sets, such as rare event detection. And it's an exercise in stretching a metaphor to its limit to see what we learn along the way.


#### This sounds easy! 

Needle-finding is simple: just create a training set with lots of examples of needles (labelled positive) and bits of hay (labelled negative), train your favourite model, and let it loose on the haystack! Despite being small, needles have quite a few distinguishing features compared to hay -- colour, density, flexibility etc. -- so the decision boundary should be quite clear with a nice large margin. Any good [Kaggler](https://www.kaggle.com/) should be able to get 95% accuracy at least, surely?

#### Maybe not quite so easy!

Let's move this metaphor a little closer to reality, one step at a time.

Suppose that in our haystack there are a few short, sharp pieces of hay that may look a little bit needle-like. Or suppose that the needles come in a variety of shapes and sizes and some tend to look a bit like a piece of hay.  Well, any good machine learning model will produce a probabilistic prediction, so we could rank every item by its predicted probability of being a needle, and then apply a threshold. Any item with a large prediction is probably a needle. By tweaking the threshold, we can explore the trade-off between high precision (finding only needles, but maybe missing a few) and high recall (finding all the needles but mixed up with a few bits of hay). Problem solved!

But what is the best threshold? That depends on the use case. If it's really important to find *all* the needles, then we must set a low threshold and assume that any true needles are given a higher score. This leaves the end user with a lot of items to check, but if we've reduced "a million pieces of hay and a needle" down to "ninety-nine pieces of hay and a needle", then the work we've left the user isn't too hard (even if our precision is only 1%). Perhaps we can evaluate a series of possible thresholds against some criteria, and choose the best one? Just one more parameter to optimise...


#### Evaluation

To evaluate our needle-finding model and its threshold, we could spend a bit of time examining one haystack more carefully. Manually finding *every* needle in it, to verify that our model correctly found them all, might be infeasible. After all, we're trying to automate this task for a reason. But perhaps we can manually examine just a bit of the haystack -- a substack? --  and verify that the correct number of needles are being identified there. The problem is that if needles are very rare, then it's likely that any substack that is small enough to be manually assessed probably won't have any needles in it anyway. So we won't learn much about how the model is performing. (We might get some idea of precision, by looking at the false positive predictions, but we can't really set the threshold sensibly so even the precision is undefined. And we have *no idea* about recall.)

We could make our own toy haystack which we know has exactly 10,000 pieces of hay and exactly 10 needles. Then we can measure endless models against it, optimise the threshold for some combination of precision and recall (such as the [F1 score](https://en.wikipedia.org/wiki/F-score).) Such an artificial construction might be a useful way to test some ideas, compare some models, encourage Kaggle-style competitions or get a paper published. But it lacks ecological validity -- it doesn't reflect reality -- so it may be hard to apply what we learn when go back to the real world problem. (Assuming we ever go back there...) 

A final option is euphemistically called "user-centred evaluation": pick a model, deploy it and see how loudly the users complain. Or whether they just politely walk away. This can work fine for web-scale A/B testing or some academic scenarios. But if you have only a small band of users, then you'd better hope they have endless reserves of patience. And time. And then we're back in a fantasy world.

#### Lots. Of. Hay.

Let's generalise a bit more. We don't really care about any particular haystack: we're interested in a general needle-finding solution. Suppose we have an entire hillside covered in haystacks and we want to find the needles in all of them. But some haystacks have no needles in! Others have lots! Some haystacks have thousands of needle-like bits of hay, but no needles at all! Others have a few hay-like needles hidden amongst the regular hay! What to do?

Well, one option is to set the threshold differently for each haystack, depending on it's particular characteristics. At least we don't need to retrain the model for each stack, which saves creating and annotating endless data sets. But even just setting the threshold is hard, as discussed above. Also we've accidentally created a new problem: haystack characteristic prediction. 

#### Drifting haystacks 

Suppose by some combination of effort and luck we manage to build a sufficiently good needle-finder, and we've found a sufficiently good threshold so its predictions are useful. Time to sit back and relax with a cold drink! But even as we do so, we notice that as the farmer continues to make new haystacks, their nature subtly changes over time. Perhaps different rainfall patterns or insects have made the hay grow a bit thinner or greyer or more varied. Perhaps the needles that some fiend is adding to the haystacks[^1] have also changed - new ones are a bit thicker or longer or yellower. 

Reality doesn't stand still and however good our model is it'll probably need to be retrained from time to time  to correct for concept drift. Of course, given that evaluation is hard, picking a threshold is hard, labelling a big enough training set is hard and all these problems impact each other, it may well be impossible to ever determine *when* the model is performing less well than it used to.

#### Enough with they metaphors!

To wrap up, the problem I am (still!) working on is claim detection: after fact checkers, such as my colleagues at [Full Fact](https://fullfact.org), have investigated a claim and published their findings, other people may repeat the original claim. If that claim is misleading and potentially harmful, then we want to be able to quickly identify the repeats and (potentially) reach out and ask journalists, politicians and anyone of influence, to please stop spreading the misinformation. But new claims (the needles) are published every day, and the topics covered drift over time, reflecting changes in the world. And the media sources that we can monitor (the haystacks) are huge and ever-changing. They're also diverse: will a model that identifies repeated claims made in Hansard also find such claims in Buzzfeed? Or on Twitter? And if it works in the UK, will it work in Africa or South America?


---

[^1]: I mean, why would *anyone* put needles into a haystack? 
