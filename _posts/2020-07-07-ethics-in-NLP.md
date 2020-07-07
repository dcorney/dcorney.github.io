---
layout: post
category: thoughts
title: Ethics in NLP and machine learning


---



I just read a paper [^1] on the ethics of [NLP](https://en.wikipedia.org/wiki/Natural_language_processing) systems which was very thought provoking. In fact, you're now reading some of the thoughts it provoked... The authors say that a NLP systems are now so widely used that they are having a real impact on society, and that this has crept up on us so swiftly that we haven't had a chance to come up with a proper ethical framework. 

Instead, new NLP tools go live and get lots of excited publicity, but few months or hours later, someone points out that it's massively racist, sexist, homophobic or otherwise unethical. A sort of milkshake duck for AI. Then one of the development team meekly steps up to apologise, says that was unintentional and blames biased data collection, or says that their model merely reflects the reality they found by random sampling.  [Some examples that spring to mind: [Amazon's racist recruiting](https://www.theguardian.com/technology/2018/oct/10/amazon-hiring-ai-gender-bias-recruiting-engine), [YouTube's sexist captioning ](https://www.aclweb.org/anthology/W17-1606/) ,  [Google's toxic speech detection](https://medium.com/the-false-positive/unintended-bias-and-names-of-frequently-targeted-groups-8e0b81f80a23) etc.] 

I've been working in machine learning and NLP for 20+ years, and with a few exceptions, ethics has only been seriously discussed in the last few years. So proposing general ethical frameworks feels like a step in the right direction.

Instead of re-inventing the wheel, the authors suggests we adopt or adapt existing philosophical ideas and they outline two: the generalization principle and the utilitarian principle. As a UCL alumnus, I am of course at least vaguely aware of [Jeremy Bentham](https://www.ucl.ac.uk/bentham-project/who-was-jeremy-bentham/auto-icon)'s *Utilitarianism*: a moral action is one that maximizes everyone's happiness or utility.  So a morally good NLP system might minimize the error of a model across an evaluation set, thus maximizing utility. And if this test set is large and representative, then we might end up with quite a complex model capable of accurate predictions. And if the data is truly representative of our target population, then it may even be "ethical", at least in the sense of not penalizing minoritized groups. 

The paper's description of the *generalization principle* confused me at first: it says moral actions are those that everyone would consistently take given the same evidence. The paper interprets this as a strong bias towards simple models as these are more likely to be consistent in their behaviours and to ignore extraneous information. In particular, this means that if we perturb inputs that are irrelevant to the model's target behaviour, then the output should be unchanged. When performing speech-to-text, the gender of the speaker is irrelevant, so changing it should not change the output. 

It's interesting that in this interpretation, we have two sides of the [bias variance tradeoff](https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff) (note the technical ML use of 'bias' here): we have either a very complex *utilitarian* model that risks 'overfitting' the task at hand and failing to generalise to new cases ("high variance"); or we have a very simple *generalizing* model that 'underfits' and... fails to generalise ("high bias"). Solving this tradeoff is the heart of most machine learning systems.

Put another way: suppose we have some NLP task such as topic detection of social media posts. And suppose we want our tool to behave ethically and be equally accurate in its predictions whether the author of the text is (say) a man or a woman. Then maybe we could build a model that is so simple that it has no way of modelling gender, even implicitly, and so cannot be misogynistic. Or we could build a model that is so complex that while it implicitly captures the gender of the author, it still performs well across the board (though this depends heavily on the data being balanced, of course). 

These potential parallels between ethics and machine learning are new to me and fascinating. But can they help us actually develop some framework for evaluating ethics? Both the systems described in the paper fail (in my eyes) for the same reason: they both rely on an exhaustive list of sub-populations who we wish to avoid prejudicing against. Is this system biased against women? Or black people? Or gay people? Even if we add appropriate test data from each sub-population, and confirm our model is "unbiased", we also need to test for [intersection](https://en.wikipedia.org/wiki/Intersectionality) bias: I once attended a seminar describing some of [Perspective API's](https://medium.com/the-false-positive/unintended-bias-and-names-of-frequently-targeted-groups-8e0b81f80a23) attempts to identify hate speech in message forums, and they were pleased when it could accurately detect racist speech and homophobic speech, so they went live. But then they received complaints from (among other groups) black lesbians who suffer from quite specific forms of hate speech that weren't in the training data. 

So: All models have errors. If those errors are in some way correlated with race, gender, sexual orientation etc., then this suggests the model has a problematic bias and more work is required. By this measure, a socially unbiased model is not error-free (that's too ambitious!) but has errors that are inexplicable, or "just noise".  But I'm not convinced that we need an ethical framework to help us decide whether to build more or less complex models.

<br>

<br>

*Postscript*: while typing the above words, I also came across the "[model cards](https://arxiv.org/abs/1810.03993)" proposal, which recommends keeping detailed records of a model's origin including data sources, annotators, algorithms and so on. I'm definitely going to start using these in my own work! It feels that being conscious of the potential for bias is a necessary part of reducing bias, even if not sufficient by itself.

See also [Data Feminism](https://mitpress.mit.edu/books/data-feminism) by Catherine D'Ignazio and Lauren Klein which I'll probably write about when I've read more of it. 



[^1]: S. Prabhumoye, E. Mayfield, and A. W. Black, ‘Principled Frameworks for Evaluating Ethics in NLP Systems’, *arXiv:1906.06425 [cs]*, Jun. 2019, Accessed: Jul. 03, 2020. [Online]. Available: http://arxiv.org/abs/1906.06425.

