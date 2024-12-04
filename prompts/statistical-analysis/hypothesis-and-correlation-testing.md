---
title: "Hypothesis testing"
---

## Prompting to estimate correlations and test hypotheses

LLMs can be highly useful in first-pass data analysis, particularly when paired with a useful computational engine via API integration (I love Wolfram Alpha and highly recommended trying out their API). 

They can also be used to (albeit crudely) test the correlation between two variables.

A prompt like:

`Calculate the correlation between X and Y`

is a simple but useful starting point in determining what the relationship between two data series approximates to. 

Correlations can be seen with the "naked eye" when looking at small tables of data. But when you're got thousands or millions of rows of CSV data, it very quickly stops being obvious whether there's:

- A positive correlation between A &B 
- A negative one  
- Not really much of notable correlation at all, in fact 

LLMs' main utility in data analysis, however, isn't as number-crunchers, but as bridges between human language and ... everything else. Their beauty, in this respect, is allowing us to frame our enquiries in the natural language of human inquisitiveness rather than in the rigid syntax of SQL.

By default, many LLMs will explain mathematical correlations in conventional terms like "weakly positive". These may be mathematically accurate. But they're not particularly descriptive. Without asking them to write poetery about stock indices, LLMs can be nudged to be a bit more expressive than these bald statements!

The strength of what seems like a strong correlation, for example, might be undermined by a small sample size that may render the finding statistically insignificant. 

So why not ask:

## How's my sample size, LLM?

As a non-statistician, I'm a huge fan of using LLMs as instructive guides in this capacity to educate me on the basics before I pass over something that might be good to someone who actually knows what they're doing. 

To do that, I'm simply very honest about what I do and don't know. When prompting a robot, I have nobody to impress. Nor can I embarass myself. So I don't bluff.

I might prompt (note: I'm being deliberately specific about identifying columns):

>This dataset looks interesting. Look at column A (average salary) and column B (average employee tenure). Can you do the following: one, calculate the correlation between these two datapoints, expressing it mathematically between 0 and 1 correct to two decimal places. Additionally, consider the sample size.

This prompt isn't quite finished yet, because asking it to "consider the sample size" is not very precise. Because LLMs are the world champions of literalism (they're more deadpan than me on a bad day), they'd probably chime back with:

>Your sample size is 438 employees.

I mean *yes*. You have certainly *considered* my sample size by telling me how big it is. But yeah ... not quite what I was hoping for, guy.

So what I would prompt, instead (in this imaginary scenario, we're looking at data for companies in Illinois):

>See if you can find recent studies comparing employee remuneration and tenure in Illinois. Limit your focus to studies that have been published since 01/01/2023. If you can find any such studies, state how many samples were included in the analysis. 

All I'm trying to do, here, is get a sense for what *might* be considered a reasonable sample size for this particular line of sociological enquiry. So that I don't wind up with egg in my face when I announce that I made a great discovery (but yes, based on three companies...)

The specificities in the prompt are merely to limit the LLM's retrieval to within the narrow parameters of data that may be instructive for my own analysis. 

I'm assuming that the question of the extent to which remuneration keeps people in jobs is a well-worn one. So rather than trying to fish through *every* study that has ever looked at this point, I'm trying to say (in prompting terms):

>I know you have access to petabytes of data. But just look here. 

## Really basic hypothesis testing

One of the pitfalls of working with data is becoming emotionally invested in hoping to see a hoped-for hypothesis validated by your findings. 

Sadly, this doesn't always happen. Research undertaken solely to validate a hypothesis isn't really scientific enquiry. 

But what can I say ... I'm a human with feelings like the rest of us.

Often, I'm looking at data for a project. But that doesn't mean that I'm not bummed out to discover that the data I spent hours sifting through just means that I'm wrong.

A prompting strategy I've devised in this regard is what I call simple hypothesis testing. I like it because it's easy to template and it can help to both:

- Cushion the blow of an experiment that shows the opposite findings of what you were expecting  
- Tamper down your subjectivity by spelling it out like it is.

### Prompt template

Take a look at this dataset:

{dataset}.

The hypothesis is this:

{hypothesis}

Choose from one of the following options. Pair your choice with a description.

The correlation observed in the dataset:

1) Supports the hypothesis
2) Argues against the hypothesis
3) Neither strongly supports nor refutes the hypothesis  

### Some notes about prompt wording

Note that the above prompt deliberately takes some options off the table. 

It's spectacularly unlikely that a data doesn't make some marginal argument for or against a hypothesis. That's why I've added *strongly* to option 3. 

This prompt is also kind of like a question in *Who Wants To Be A Millionaire* in which you've handed the contestant a question after cutting out half the options.

I took the possibitility that this finding decisively throws the hypothesis in the bin off the card for this reason because *ouch* I know, I know but ... let me down lightly, please. 

Finally, I've resisted the temptation to ask the LLM to try to be overly clever and ask the LLM to rate the support or refutation of the hypothesis on a scale from 1 to 10 or 0 to 100.

My reason for doing so is because I've been using these tools long enough to have learned their modus operandi.

Given the chance to cook up these kind of remarkable findings they absolutely will do so with their characteristic conviction (Anthropic's models are kind of the exception because they've had ethical refusals very deliberately baked into them).

The problem is that it's like asking me to say what I think the chance of it raining tomorrow is.

I can tell you that I've calculated it to be 70.72%. You might think I'm a meteorological genius with a crystal ball. But actually, I just plucked that number out of thin air.