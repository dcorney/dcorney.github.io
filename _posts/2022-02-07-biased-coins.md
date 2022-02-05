---
layout: post
category: thoughts
title: Crowdsourced data and biased coins
---

Crowdsourcing relies on the wisdom of the crowd: combining the opinions of many ordinary people often gives very reliable data. But how many people do we need to ask? It turns out that this problem was solved more than 300 years ago in Switzerland by one [Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli).

At [Full Fact](https://fullfact.org/), we've recently started using crowdsourcing to get more training data for a [couple](https://fullfact.org/get-involved/robo-challenge/) [of](https://fullfact.org/get-involved/claim-challenge/) AI projects. We're fortunate to have many generous supporters who are keen to give a little of their time. To keep things as simple as possible, we only ask direct yes/no answers. We show each question to lots of people and combine their responses to decide a final answer to each question, which we then use to train our models. 

This raises an interesting problem: how many individual answers do we need before we can be confident in the final aggregate answer? Suppose we have 20 responses to a question and 19 people said "yes" while one said "no": we'd be happy to take "yes" as our final answer. We'd assume the other person mis-read the question or clicked the wrong button or something. And we would stop asking that particular question: a 21st or 22nd answer would provide us with no new information and so be wasted effort.

But suppose for another question that 12 of the first 20 responses are "yes" and 8 are "no". We could take a simple majority and label the example as "yes". Or we could say it's too close to call and label it as "don't know". But suppose we carried on collecting more answers from more people and after 40 responses, we had 30 "yesses" and only 10 "noes". We could then decide to take "yes" as the final answer with some confidence. We don't want to waste our supporters efforts, so we need to calculate **how few responses we need** to each question before we can decide the final answer with a high level of confidence. 

## Is this coin biased?

Perhaps surprisingly, this problem is equivalent to asking if a [coin is biased or not](https://en.wikipedia.org/wiki/Checking_whether_a_coin_is_fair). If after 20 tosses I've counted 19 heads and 1 tails, I'd be happy to say the coin is biased towards heads. But if it was 12 to 8, I might want to toss it a few more times before deciding. The analogy is as follows:
* *tossing a coin* is like *asking one more person to answer a question*.
* *the probability of a coin showing heads* is like *the probability that the next person to answer the question will say "yes"*.
* *a coin biased towards heads* is like *a question that most people would answer "yes" to, if we asked enough people*.
* *a coin biased towards tails* is like *a question that most people would answer "no" to, if we asked enough people*.
* *an unbiased coin* is like *a question to which as may people answer "yes" as answer "no", no matter how many we ask*.


This help us because investigating biased coins has a long history in statistics (along with dice and card games), so we can use well-established solutions to help us. The **binomial distribution**, defined by Jacob Bernoulli in the 18th century, is a statistical model of the likely outcomes of a sequence of yes/no events (called Bernoulli trials), such as coin tosses. A few simple equations can tell us things like:
* If I toss a coin 10 times, how many heads need to come up before I can be 95% confident that the coin is biased towards heads?
* What's the probability of seeing exactly 5 heads after 10 tosses, if the coin is biased and shows heads with a probability of 0.4?
* How many times will I have to toss this coin to have a 99% chance of seeing 5 heads?

So as we receive a steady stream of *yesses* and *noes* to a particular question, we now keep recalculating the probability that in the long run, the answer will converge to yes or no. And when that probability goes above a certain threshold of confidence, say 99%, we stop asking the question and move on to the next one.

This means we ask for lots of help with the difficult questions where there is disagreement, but quickly move on with the easy ones when everyone agrees.
 
## More formally...

Here is a very brief summary of the methods, with snippets of code to make things more concrete ('cos that's how *I* think best). But if you want to understand more, please do follow the links for more reading and let me know what you think.

Let's define:
<p style="line-height: 1.15;">
&nbsp; C<sub>y</sub> as the count of "yesses"<br>

&nbsp; C<sub>n</sub> as the count of "noes"<br>

&nbsp; <i>n</i> = C<sub>y</sub> + C<sub>n</sub> is the total number of trials<br>

&nbsp; <i>q</i> = 0.99 is our confidence bound<br>

&nbsp; <i>p</i> = 0.5 is the prior probability of a yes or a no
</p>

Then the *critical value* is smallest integer such that the cumulative binomial distribution equals or exceeds the confidence bound. This can be calculated from the inverse survival function of the binomial. 

Here's a concrete implementation of an example. Suppose we collect 25 answers, and 20 are "yes". Is this enough?

In [Python](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.binom.html), this critical value (cv) is calculated with:

    from scipy.stats import binom 
    cv = binom.isf(1 - 0.99, 25, 0.5)

In [Excel](https://support.microsoft.com/en-us/office/binom-dist-function-c5ae37b6-f39c-4be2-94c2-509a1480770c), it's
    
    =BINOM.INV(25, 0.5, 0.99)

And in [Matlab](https://www.mathworks.com/help/stats/binoinv) it's
    
    cv = binoinv(0.99, 25, 0.5) 

In each case, the critical value is 18, meaning if we see 18 or more "yesses" out of 25, that's enough to be 99% sure that "yes" is a good final answer. The equations are symmetric because our prior belief is 0.5, so seeing 18 or more "noes" is enough to be 99% sure that "no" is the final answer. So seeing 20 yesses is definitely enough.


## Further reading

[Checking whether a coin is fair](https://en.wikipedia.org/wiki/Checking_whether_a_coin_is_fair)

[Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli) - come for the maths, stay for the family feuds!

[Binomial distribution](https://en.wikipedia.org/wiki/Binomial_distribution)

[Hypothesis Testing for Binomial Distribution](https://www.real-statistics.com/binomial-and-related-distributions/hypothesis-testing-binomial-distribution/) - some useful worked examples (esp. in Excel)