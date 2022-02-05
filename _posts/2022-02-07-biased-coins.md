---
layout: post
category: thoughts
title: Crowdsourced data and biased coins
---

Crowdsourcing relies on the wisdom of the crowd: combining the opinions of many ordinary people often gives very reliable data. But how many people do we need to ask? It turns out that this problem was solved more than 300 years ago in Switzerland by one Jacob Bernoulli.

In my day job, we've recently started using crowdsourcing to get more training data for a couple of projects. We're fortunate at Full Fact to have many generous supporters who are keen to give a little of their time to help us improve our AI models. To keep things as simple as possible, we only ask simple yes/no answers. We show each question to lots of people and group their responses together to decide a single final answer to each question, which we then use to train our models. In this way, it doesn't matter if some people make a mistake (we all do!) as long most people give the correct answer most of the time.

This raises an interesting question: how many individual answers do we need before we can be confident in the final aggregate answer? For example, if we have 20 responses to one question and 19 people said "yes" while just one said "no", we'd be happy enough to take "yes" as our final answer. We'd assume the other person mis-read the question, clicked the wrong button or made some other mistake. And at that point, we would stop asking that particular question: a 21st or 22nd answer would provide us with no new information, and so be wasted effort.

But consider a second question, where 12 of the first 20 responses are "yes" and 8 are "no". We could stop and take the simple majority and label it as "yes". Or we could say it's too close to call, and label the example as "don't know". But if we carried on collecting more answers from more people, then perhaps after 40 responses, we'd have 30 "yesses" and only 10 "noes", and we could then decide to take "yes" as the final answer with more confidence.
We don't want to waste our supporters efforts, so we want to calculate **how few responses we need** to a question before we can decide the final answer with a high level of confidence. 

## Is this coin biased?

This problem can be reframed to make it equivalent to asking if a coin is biased towards heads or tails, or is unbiased. If after 20 tosses we've counted 19 heads and 1 tails, I'd be happy to say the coin is biased towards heads. But if it was 12 to 8, I might want to toss it a few more times before deciding. The analogy is as follows:
* tossing a coin is like asking for one more person to answer a question
* the probability of a coin showing heads is like the probability that the next person to answer the question will say "yes"
* a coin biased towards heads is like a question that most people would answer "yes" to, if we asked enough people
* a coin biased towards tails is like a question that most people would answer "no" to, if we asked enough people
and so on.

This help us because investigating biased coins (and dice) has a long history in maths, so we can use well-established solutions to help us. The **binomial distribution**, defined by Jacob Bernoulli is a statistical model of the likely outcomes of a sequence of yes/no trials (called Bernoulli trials). A few simple equations can tell us things like:
* What's the probability of seeing exactly 5 heads after 10 tosses, if the coin is biased and shows heads 25% of the time?
* How many times will I have to toss this coin to have a 99% chance of seeing 5 heads?
* If I toss a coin 10 times, how many heads need to come up before I can be 95% confident that the coin is biased towards heads?

So as we receive a steady stream of yesses and noes to a particular question, we can keep recalculating the probability that in the long run, the answer will converge to yes or no. And when the probability goes above a certain threshold of confidence, say 99%, we stop asking the question and move on to the next one.

## Further reading

[Checking whether a coin is fair](https://en.wikipedia.org/wiki/Checking_whether_a_coin_is_fair)

[Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli)

[Binomial distribution](https://en.wikipedia.org/wiki/Binomial_distribution)


 
## More formally

Let's define :

&nbsp; C<sub>y</sub> as the count of "yesses"

&nbsp; C<sub>n</sub> as the count of "noes"

&nbsp; *n* = C<sub>y</sub> C<sub>n</sub> is the total number of trials

&nbsp; *q* = 0.99 is our confidence bound

&nbsp; *p* = 0.5 is the prior probability of a yes or a no

Then the *critical value* is smallest integer such that the cumulative binomial distribution equals or exceeds the confidence bound. This can be calculated from the inverse survival function of the binomial. 

Here's a concrete implementation of an example. Suppose we collect 25 answers, and 20 are "yes". Is this enough?

In [Python](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.binom.html), this critical value (cv) is calculated by:

    from scipy.stats import binom 
    cv = binom.isf(0.01, 25, 0.5)

In [Excel](https://support.microsoft.com/en-us/office/binom-dist-function-c5ae37b6-f39c-4be2-94c2-509a1480770c), it's
    
    =BINOM.INV(25, 0.5, 0.99)

And in [Matlab](https://www.mathworks.com/help/stats/binoinv) it's
    
    cv = binoinv(0.99, 25, 0.5) 

In each case, the critical value is 18, meaning if we see 18 or more "yesses" out of 25, that's enough to be 99% sure that "yes" is a good final answer. The equations are symmetric because our prior belief is 0.5, so seeing 18 or more "noes" is enough to be 99% sure that "no" is the final answer. So seeing 20 yesses is definitely enough.
