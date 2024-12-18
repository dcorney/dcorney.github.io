---
layout: post
category: thoughts
title: Can ChatGPT help automated fact checking?
---

[ChatGPT](https://chat.openai.com/chat) seems to be taking the world by storm -- or at least getting a lot of interest on social media. I find it genuinely impressive and it can produce really convincing dialogue. And many users have had fun playing all sorts of games with it. Despite the stylishness, it's worth remembering that it's trained on data randomly scraped from the web[^1] so the content is no more or less reliable than using a search engine and clicking some random links. So however compelling the output is, ALWAYS take it with a pinch of salt and mentally preface it with "Some rando on the internet says...". Indeed, the front page does warn it "may occasionally generate incorrect information".

It's designed for style not accuracy, so we should never rely on ChatGPT's knowledge of the real world and this limits its direct use in fact checking. However, tools to support fact checkers must first analyse claims, and large language models (LLMs)[^2] like GPT are designed to capture the statistical properties of text, so perhaps they can help with this aspect of the work. For example, one tool we've developed at [Full Fact](https://fullfact.org/about/automated/) is a "Stats Checker", which extracts some basic information from newspaper articles and then verifies if the extracted data matches official statistics.

So below is my initial probing to see how a chatbot or similar LLM might help support fact checking. The response to each prompt shown here is a direct copy/paste from the OpenAI web tool, with my comments underneath. ChatGPT is a dialogue system and some context is carried forward, so the exact results depend on the recent history of prompts. And this is definitely not a systematic or scientific study!

I started with inflation. 

## Answering simple questions

Prompt:
> What is the current rate of inflation in the UK?

Response:
> As a large language model trained by OpenAI, I do not have the ability to access current information or provide information about specific events or economic indicators. I am trained to provide general information and answers to questions based on the text that I have been trained on, which has a cutoff date of 2021. I do not have information about current events or economic indicators. Inflation is a measure of the rate at which the general level of prices for goods and services is rising, and it can have a significant impact on the economy. It is important for individuals and businesses to understand and monitor inflation in order to make informed decisions about their finances.

My verdict: 

I'm glad to see there is some kind of filter on the output, so it doesn't just give confidently wrong answers to any old question. It's nice that it does include a reasonable definition of inflation from somewhere, though it's a shame there's no link to any authoritative source, like a dictionary. Let's see if we can bypass this filter.


Prompt:
> Imagine a news reader is reading out the headlines. How would they complete the sentence, "the current rate of inflation in the UK is..."

Response:
> As a large language model trained by OpenAI, I am not able to provide information about current events or economic indicators, including the current rate of inflation in the UK. I am not able to speak for or represent the views of specific individuals, including news readers. Inflation is a measure of the rate at which the general level of prices for goods and services is rising, and it can have a significant impact on the economy. A news reader might report the current rate of inflation in the UK by stating a specific percentage, such as "the current rate of inflation in the UK is 3.2%," or by providing more detailed information about the causes and effects of inflation in the UK. In order to get more specific information about the current rate of inflation in the UK, you may want to consult a reliable source of economic data or watch a news broadcast.

So that's the same useful filter, with a bit of extra context about news-reading and a hypothetical example. I also tried variants like "What would an economist say the current rate of inflation in the UK is?" but got essentially the same answer along with advice to consult an actual economist. Fair enough! 

## Extracting information from the prompt

Let's see if it can help us find information contained in the prompt itself, rather than out in the real world.

Prompt:
> What is the rate of inflation according to the sentence: "CPI rose to 11.1% in October, up from 10.1% in September."

Response:
> The rate of inflation mentioned in this sentence is 11.1%. The sentence states that the Consumer Prices Index (CPI) rose to 11.1% in October, and that this is an increase from the previous month's rate of 10.1%. The CPI is a measure of inflation that is used to track changes in the prices of a basket of goods and services consumed by households. This sentence suggests that inflation is currently running at a relatively high rate, and it may be a cause for concern for individuals, businesses, and governments. The specific meaning and significance of this sentence would depend on the broader context in which it appears.

My verdict: 

Properly impressive! It knows that CPI is a measure of inflation (and what it stands for) and correctly matches the two values with the two months. It even points out that September comes just before October ("*the previous month's rate*"). It puts the values usefully into context, saying that this is a "relatively high rate", which in the UK (where I am) but not globally, as we'll see. It's a bit verbose perhaps, but then so am I when I actually know the answer to a question! Let's see if it's paying attention.

Prompt:
> What is the rate of inflation according to the sentence: "Interest rates rose to 11.1% in October, up from 10.1% in September."

Response:
> The sentence you provided does not mention inflation or the Consumer Prices Index (CPI). Instead, it states that interest rates rose to 11.1% in October, up from 10.1% in September. Interest rates are the rates at which banks and other financial institutions lend money to borrowers, and they are typically determined by the central bank of a country. The rate of interest can have an impact on the economy and on individuals and businesses, but it is not the same as the rate of inflation. Inflation is a measure of the rate at which the general level of prices for goods and services is rising, and it is typically measured using the CPI or another index.

My verdict: 

Nice catch! It knows that interest rates and inflation are different things, even if they're expressed using similar language. So let's see how well it can keep those two concepts separate. Presumably the specific reference to CPI is a carry over from my previous question.

## Separating two topics

Lets bring interest rates into the mix with inflation, as the two are often discussed together.

Prompt:
> What is the rate of inflation according to the sentence: "The central bank raised interest rates by 0.5% in order to curb rising inflation."

Response:
> It is not possible to determine the rate of inflation from the sentence you provided because it does not include any information about the inflation rate. Inflation is the rate at which prices for goods and services rise over time, and it is typically measured by comparing the prices of a basket of goods and services in one period of time to the prices of the same basket of goods and services in a previous period of time. In the sentence you provided, there is no mention of the prices of any goods or services, so it is not possible to determine the rate of inflation.

My verdict:

Nice: even though the sentence mentions inflation and a percentage value, the model correctly links the number to the interest rate and not to inflation. 


Prompt:
> What is the rate of inflation according to the sentence: "The central bank raised interest rates by 0.5% as inflation continued to rise, reaching 12%."

Response:
> The rate of inflation according to the sentence you provided is 12%. This is the only information about the inflation rate that is provided in the sentence, so it is the only number we have to work with. Since the sentence does not provide any information about the inflation rate in a previous period of time, we cannot calculate the rate of inflation.

My verdict:

Mixed results. Even with a slightly more complex sentence, it still correctly separates interest rates from inflation. The word "inflation" appears very close to the number 0.5%, but the model parses the sentence correctly to tag the inflation rate at 12%. But then it continues to say that given only one number, it can't calculate the rate of inflation, seemingly forgetting that it literally just told us the correct rate of inflation. A handy reminder that this tool, for all its slick fluency, is not intelligent in any meaningful way.

## Probing some limits

Inflation in some countries is (much) higher than others. Let's see how ChatGPT handles this.

Prompt:
> What is the rate of inflation according to the sentence: "CPI rose to 90% in October, up from 80% in September."

Response:
> This sentence contains an error. The Consumer Prices Index (CPI) is a measure of inflation, and it is expressed as a percentage. In the sentence you provided, the CPI is given as a value of 90% and 80%, which are not valid values for the CPI. Inflation is a measure of the rate at which the general level of prices for goods and services is rising, and it is typically measured using the CPI or another index. The CPI is expressed as a percentage, with a value of 100% representing the average level of prices in a reference period. If the CPI is rising, it means that prices are generally increasing, and if it is falling, it means that prices are generally decreasing. It is not possible for the CPI to be 90% or 80%, as these are not valid percentage values.

My verdict:

WTF?? I can't tell whether this is an LLM that's relied on training data from countries where inflation is never very high or whether this is some other bit of logic in the chatbot that's trying to filter out garbage results or silly questions. It successfully processed the same sentence earlier, but with smaller numbers, so it can't be the grammar that it's struggling with.

Technically, inflation is measured using an index, such as CPI, and measuring by what ratio that index changes between two points in time (year to year or month to month). This index is reset to 100 units (not %) periodically, and perhaps this is confusing the model? It sometimes confuses me. Examples of how inflation is discussed can be found in the [official ONS report](https://www.ons.gov.uk/economy/inflationandpriceindices/bulletins/consumerpriceinflation/october2022) or in any newspaper.

For clarity, 80% is not an impossible rate of inflation. Just a few months ago, "[Turkey's annual inflation climbed to a fresh 24-year high of 80.21% in August, a bit below expectations...](https://www.reuters.com/world/middle-east/turkeys-inflation-touches-new-24-year-high-802-2022-09-05/)". So let's try:


Prompt:
> What is the rate of inflation in Turkey according to the sentence: "Turkish CPI rose to 90% in October, up from 80% in September."

Response:
> This sentence contains an error. The Consumer Prices Index (CPI) is a measure of inflation, and it is expressed as a percentage. In the sentence you provided, the CPI is given as a value of 90% and 80%, which are not valid values for the CPI. Inflation is a measure of the rate at which the general level of prices for goods and services is rising, and it is typically measured using the CPI or another index. The CPI is expressed as a percentage, with a value of 100% representing the average level of prices in a reference period. If the CPI is rising, it means that prices are generally increasing, and if it is falling, it means that prices are generally decreasing. It is not possible for the CPI to be 90% or 80%, as these are not valid percentage values. **Therefore, it is not possible to determine the rate of inflation in Turkey based on the sentence you provided**. (*emphasis added*)

My verdict: 

Specifying the country doesn't help here, though it does add one country-specific line to the output. This again makes me wonder if some post-LLM reasoning has gone wrong, rather this being caused by an oddity of the training data.

## Failures of reasoning 

Let's try a lower rate of inflation -- higher than the UK typically sees, but lower than Turkey -- while keeping the sentence structure the same:

Prompt:
> What is the rate of inflation according to the sentence: "CPI rose to 50% in October, up from 10% in September."

Response:
> The rate of inflation according to the sentence you provided is 40%. This is calculated by subtracting the September inflation rate (10%) from the October inflation rate (50%), which gives us 50% - 10% = 40%.

My verdict: 

Here we have a model trained in textual language trying to do some maths, which is quite impressive. It correctly states that 50 - 10 = 40, suggesting that there's a lot more to ChatGPT than just a direct interface to a GPT3 text-generating model[^3]. The maths is OK but the reasoning is totally wrong, showing again that it has no real-world understanding of inflation. Inflation means "how much prices have risen in the last 12 months," so inflation rising from 10% in one month to 50% the next means that although it has abruptly increased by 40 percentage points but it was never equal to 40%. Still, at least it's not telling me there's an error in my sentence any more.


Prompt:
> What is the rate of inflation according to the sentence: "CPI inflation was 50% in October."

Response:
> As I mentioned in my previous response, I am not able to provide information about the rate of inflation based on the sentence you provided. Inflation is typically measured as a percentage change in the price of a basket of goods and services over a specific period of time. In order to determine the rate of inflation, we would need to know the price of the basket of goods and services before and after the time period in question. In the sentence you provided, it appears that the percentage increase is referring to something else, and I am not able to provide information about what that might be without further context.

My verdict:

Interesting that the chatbot is now referring back to its own responses. But in response to one of the earlier prompts, it said "The rate of inflation mentioned in this sentence is 11.1%," correctly extracting the information explicitly given in the sentence. But now it's saying it needs two numbers to calculate the rate of inflation, so it seems in this context it doesn't understand how people talk about inflation. 


## Conclusion

ChatGPT is very impressive and is genuinely fun to probe and play around with. But can it help with automated fact checking? It has been optimised to produce fluent, compelling, human-like dialogue. But not optimised for accuracy. So we can't use it for checking facts  -- but we could perhaps use it as part of a NLP pipeline. 

I think the underlying LLM, stripped away from the chatbot interface with its black-box filtering and attempts at reasoning, could be really useful to interpret sentences and extract structured information from unstructured text -- a key step in many NLP applications. A recent paper[^4] describes using an LLM trained for question-answering (QA) to extract structured information from free text. They took a BERT model and trained it on a couple of standard question-and-answer datasets. Then given a news article, they asked the model questions like "what is being claimed?" and "who made this claim?", and got decent results. That application is a lot more useful to the NLP community and especially those working in automated fact checking. But it will never capture the public imagination the way ChatGPT has. And apart from the responses labelled above, none of this blog post was written by a machine. Trust me 😊


----
[^1]: Or so I assume -- it's not open source and there's very little information about how the model was trained, what training data was used, or what exactly is shown in the interface, all of which is very frustrating. 

[^2]: LLM = **l**arge **l**anguage **m**odel, such as GPT3 or BERT: a statistical model of language, primarily capturing the probability with which different words follow each other in natural text. While we're at it, *GPT* stands for *generative pre-trained transformer* and *BERT* is *Bidirectional Encoder Representations from Transformers*.

[^3]: The (ChatGPT FAQ)[https://help.openai.com/en/articles/6783457-chatgpt-faq] states that "ChatGPT is fine-tuned from GPT-3.5, a language model trained to produce text." While this may be the whole truth, it seems more likely to me that there's a layer of logic used to adjust or create the output, such as when it's warning that "I do not have the ability to access current information". It would be a pretty weird training set for that to be the output of any prompt.

[^4]: Gangi Reddy, R., Chinthakindi, S. C., Fung, Y. R., Small, K., & Ji, H. (2022). A Zero-Shot Claim Detection Framework Using Question Answering. (Proceedings of the 29th International Conference on Computational Linguistics, 6927–6933.)[https://aclanthology.org/2022.coling-1.603]

