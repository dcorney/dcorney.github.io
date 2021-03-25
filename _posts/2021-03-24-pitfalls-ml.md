---
layout: post
category: thoughts
title: How NOT to use machine learning to diagnose Covid-19*
---
<i>*or to do anything, really</i>.

As Covid-19 spread round the world in the first months of 2020, people from many walks of life wanted to help fight back. This is wonderful from a humanist perspective: people want to support and help others in need, using whatever talents they have. Slightly closer to home, this included many machine learning practitioners who answered the call to arms and attempted to improve diagnosis of Covid-19 though medical image analysis. Even as specific PCR assays were being developed, it had been suggested that chest x-rays could help diagnose severe cases, especially in parts of the world where x-ray machines were more available than PCR labs.

So many hundreds of papers were published through 2020 describing new machine learning (ML) tools to diagnose Covid-19 from chest x-rays, but did any prove reliable enough to be used in clinics? (*Narrator: they did not*.) A recent paper in Nature Machine Intelligence [^ref] presents a systematic review and thorough evaluation of these papers carried out by a mixture of clinical and ML experts. The paper is fascinating and well worth a read for anyone interested in applied ML, whether they work with medical images or not.

## Show your working!

The paper itself is a model of clarity and detail, allowing anyone who cares to to reproduce their work. And that is one of their key criticisms of many of these diagnostic ML papers: the descriptions of methods and results were simply insufficient to allow anyone else to reproduce the work. And without that detail, it’s impossible to have much confidence in the results.

Suppose, without providing evidence, I claim that my classifier achieves 80% accuracy on some task. You’d have little reason to believe me. (Hey, I'm a nice guy! Trust me! But you should probably demand more than just my say so.) If I provide more and more details about how I chose the training data, how I evaluated the model, what steps I took to avoid overfitting, how I optimised the hyperparameters and so on, then (hopefully!) you would trust my result more and more. This demand for reproducibility is a pretty basic idea across the sciences, but I often overlook it when deadlines are close, or I get excited and want to share my findings, or simply run out of time and need to move on to the next project. But without those details, there’s always a chance that I made some mistake and that my quality estimate is optimistic. 


When I read this paper, I felt frustrated to read about so many “failures” and also a little embarrassed to be reminded of many of the mistakes I’ve made myself. So I decided to go through the paper and see how many of the weaknesses they identified could be applied to machine learning practice in general. I hope it will encourage others to think carefully about their habits too.

## Children are to adults as... tanks are to trees?

One eye-catching example is that many papers used the same “Kermany” dataset of pneumonia chest x-rays as a control group. This was collected in 2018, so we can be sure that none of the examples represent Covid-19 -- tick! Unfortunately, the data comes from a paediatric clinic and all the patients were 5 years old or younger whereas the set of Covid-19 x-rays came from adults. So a sophisticated machine learning model might appear to perform very well, even on previously unseen examples, when it’s actually just learned to classify whether a patient is a kid or a grown-up.

This highlights a trap that is very easy for any ML practitioner to fall into: learning spurious correlations that are only present in the data due to the way it was collected. This reminds me of the [classic urban legend](https://www.gwern.net/Tanks) about a neural network that appeared to be good at finding tanks in complex images: here’s a tree with a tank behind it, and here’s a tree without a tank. It looked good until someone realised the tanks were photographed in the morning and non-tank control set of photos were taken  in the evening. All the system had learned to do was estimate time-of-day -- very much not what was intended. 

In both cases, more care was needed around the curation of datasets. It's not enough to just download some public collection and start training without also understanding where the data came from and how it was collected.


## Internal vs external validation

Common practice in machine learning is to work with a single collection of "development" data. We then split the data into two parts and use one for training and the other for testing and to estimate the quality of the final model. This is known as "internal validation". If all the data come from one source, there is a risk that this only captures the essence of that sample and not the wider target population. Unless we understand exactly how the sampling took place, and are happy that it is truly representative, we may overestimate future performance.

Cross-validation, where multiple partitions of the development dataset are used to generate a series of evaluation scores gives a better estimate of quality than a simple train/test split, but is still only internal validation and so less reliable than it could be. 

External validation requires the use of a separately collected data set for the final evaluation. While this is more effort to arrange, external validation gives much greater confidence in the quality of the model as there is less risk of overfitting. Of course, using both internal and external can give even greater insight. 

Of the 62 ML papers reviewed in depth by Roberts at al[^ref], only 12 used external data for validation. It seems that one further team thought that they had, but had inadvertently included the external set in their training data, again highlighting the need for careful curation of data. 

If a model is to be genuinely useful, it has to perform well on novel data. The best way to predict that is to evaluate on a  well-curated external dataset that truly represents the target.


## More takeaways

There's a lot more in the paper than I can summarise here, but here's a few other quick ideas:

* Make sure you know how and why the labels were generated when using public data sets. Otherwise you may be blindly learning the wrong thing
* Be really careful when using data from different sources. Are you sure there’s no leak from “training set” to “test set”? Are you sure there’s no spurious correlations between data source and label?
* Beware of dependencies between training records. If two x-ray images come from one patient, both should be in the same data split. In past projects, I’ve dealt with multiple leaves coming from one tree, multiple sentences coming from one writer, and multiple descriptions of protein-protein interactions coming from one paper. In each case, I’ve tried to minimize leakage by making sure related records are in the same train/test split, or removing such records.
* Predictions need confidence intervals or other statistical validation. When you claim an accuracy of *x* or an F1 score of *y*, how certain are we?
* Consider tools like CLAIM (“checklist for artificial intelligence in medical imaging“) to reveal potential pitfalls in modelling or gaps in reporting. CLAIM criteria include: clear data sources; clear data pre-processing steps; detailed model description; details of training hyperparameters; final model selection; and model performance metrics.
* Peer-review should probably be tighter, but asking ML experts to review papers in specific domains won’t always reveal these kinds of issues.
* Talk to domain experts throughout the stages of a project.

This last point is really important! ML practitioners (including me, I confess) really need to spend more time talking to domain experts, such as clinicians when interpreting x-rays. Otherwise it's too easy to make assumptions, maybe without even noticing, and just assume that "more data" or "more parameters" will make everything OK. We also need to be a bit more humble. It's easy to get carried away with our own hype around AI, ML and NLP but they are never a solution by themselves.

## Being suitably confident

It's easy to justify cutting corners, especially around evaluation and data curation. Like everyone, I sometimes say "this is just an initial exploration", "further research is required" or "this is only a proof-of-concept". And that's all fine, but when I do this, my results are only tentative. I can't say both "this is a quick, initial study" AND "the model definitely got 88.7% accuracy". Either it's: 
* "this is a quick study and we got somewhere around 80-90% accuracy" 

or 

* "we definitely reached 88.7% accuracy and here's the details of the carefully-curated evaluation". 

Anything else and we're just fooling ourselves.

Of course, sometimes a paper can still help move a field forward and show what might be possible, even if it is not useable by domain experts. But I've read too many papers that claim to solve some problem but only “solve” a version that is so simplified and removed from reality that it has no practical value. If you want to help solve a real-world problem, GO TALK TO DOMAIN EXPERTS before, during and after the machine learning bit. And I’m including myself here. Otherwise we'll just keep churning out papers with no real value to the wider world.

I’m well aware of the “publish or perish” pressure, and I’ve given in to the temptation to publish work that is not as good as it could be, but as a discipline, I think we need to get better at this. 

## Summary 

If a paper is not reproducible then its results should be taken with a large pinch of salt. 

If you don't know how the data was collected, it's as reliable as gossip.

If you haven't talked with domain experts, you're probably solving the wrong problem.

<br/><br/> 

----

[^ref]: "Common pitfalls and recommendations for using machine learning to detect and prognosticate for COVID-19 using chest radiographs and CT scans" by Roberts, M., Driggs, D., Thorpe, M. et al. **Nature Machine Intelligence** volume 3, pp. 199–217(2021) [nature.com](https://www.nature.com/articles/s42256-021-00307-0)
