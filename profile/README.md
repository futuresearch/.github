# Welcome to [FutureSearch](http://futuresearch.ai)!

## Tagline
FutureSearch gives **unbiased**, **deeply-researched** answers to **hard** questions about the world.

Want to try it in your business? [Get in touch](https://futuresearch.ai/request-a-demo), and see these examples. Otherwise, see below for more on how FutureSearch works.

## Table of Contents
- [Introduction](#welcome-to-futuresearch)
  - [Tagline](#tagline)
  - [Examples](#examples)
- [Reasoning with LLMs](#reasoning-with-llms)
- [Doing the Research](#doing-the-research)
  - [Summary of the Situation](#what-is-a-basic-summary-of-this-situation)
  - [Important People and Their Dispositions](#who-are-the-important-people-involved-and-what-are-their-dispositions)
  - [Key Facets Influencing the Outcome](#what-are-the-key-facets-of-the-situation-that-will-influence-the-outcome)
  - [Distribution of Outcomes](#for-each-key-facet-what-is-the-distribution-of-outcomes-from-past-similar-events)
  - [Weighing Conflicting Model Results](#how-do-i-weigh-the-conflicting-results-of-the-models)
  - [Unique Aspects of the Situation](#whats-unique-about-this-situation-to-adjust-for-in-my-final-conclusion)
- [Evals](#evals)
- [Copiloting](#copiloting)
- [Other FutureSearch Examples](#other-futuresearch-examples)

## Just Show Me Examples

- [The 2024 U.S. Supreme Court case on whether to uphold emergency abortion care protections](https://app.futuresearch.ai/forecasts/A873f/public)
- [The 2024 U.S. Supreme Court case on whether to grant former presidents immunity from prosecution](https://app.futuresearch.ai/forecasts/iFLVq/public)
- [The New York Times lawsuit on whether OpenAI can continue to serve models train on NYT articles](https://app.futuresearch.ai/forecasts/QsYKs/public)
- [The DOJ’s antitrust suit against Apple filed on March 21, 2024](https://app.futuresearch.ai/forecasts/eMocg/public)

## Reasoning with LLMs
FutureSearch is different from other LLM-based research and analysis tools in that it relies on the [techniques of modern judgmental forecasting](https://en.wikipedia.org/wiki/Superforecasting:_The_Art_and_Science_of_Prediction).

In one-shot reasoning tasks, LLMs fall short in answering hard questions:
- They give excessively cautious and nonspecific answers;
- They perform worse on partisan questions, or refuse to answer them outright;
- They don’t ground their claims in concrete evidence;
- They have cognitive biases: gullibility, availability heuristic, anchoring, etc.

Consider one of the four cases above, perhaps how the antitrust case will go against Apple. An expert forecaster tasked with this, armed with Google and a spreadsheet, would take a modeling-first approach:

1. What is a basic summary of this situation?
2. Who are the important people involved, and what are their dispositions?
3. What are the key facets of the situation that will influence the outcome?
4. For each key facet, what’s a simple model of the distribution of outcomes from past instances that share that facet?
5. How do I weigh the conflicting results of the models?
6. What’s unique about this situation to adjust for in my final answer?

We’ve found this breakdown to be fairly robust across many types of judgment-heavy questions - law, economics, politics, business (see [evals](#evals)). If each stage goes well, the final answer can be superhuman in quality. And the research & modeling can be done from scratch, in less than 15 minutes, on novel domains that FutureSearch has never handled before.

So how do we emulate the entire research and modeling workflow of an expert human forecaster?

## Doing the Research
There are a variety of techniques to get higher quality outputs. They include: prompt engineering, self-reflection, chain-of-thought, skeleton-of-thought, graph-of-thought, agent-loops, writing and executing  programs. And for information, there is trained knowledge of various LLMs, websearch, structured data from places like Wikipedia, news databases, and many sources of proprietary data. (LLMs speak many languages too.) There are a variety of LLMs to use, and there’s fine-tuning.

We don’t here describe which combinations of these techniques we use to produce each result, that’s the FutureSearch special sauce. But we will suggest some subtasks to perform to get great results.

Let’s ask [whether the DOJ’s antitrust suit against Apple will result in Apple being forced to change its business](https://app.futuresearch.ai/forecasts/eMocg/public).

### What is a basic summary of this situation?
*image*
This task is easy in this example, as one need only find and summarize the Wikipedia article on this case. In many cases it is more challenging. Done quickly and accurately, all subsequent stages can be seeded with this context, which can guide the initial stages of research to find the most useful material.

In this case, the key things to find that improve later results are (a) that the suit is from the DOJ, not the FTC, and (b) that there are many distinct claims against Apple, not just their App Store practices.

### Who are the important people involved, and what are their dispositions?
*image*

Here the complexity of the world begins to creep in. In this case, FutureSearch decided Tim Cook, Merrick Garland (US Attorney General), and Jonathan Kanter (Assistant Attorney General) were the key figures, and not for example Lina Khan (head of FTC) or Joe Biden.

This problem comes in many flavors. In the above SCOTUS case, the challenge is identifying the swing voters. In European politics, there are many heads of state that may turn out to be decisive.

Once FutureSearch decides on the actors, it decides on a series of dimensions to analyze. Here, Tim Cook’s willingness to settle lawsuits is a key feature to assess. For Merrick Garland, their previous suits against large tech companies could be a good predictor of their prosecution against Apple.

Then, FutureSearch researches the dimension to generate an assessment, from a series of observations of what the person has said or done. It cites each observation to its source - in this case, part of the FutureSearch Knowledge Base.


### What are the key facets of the situation that will influence the outcome?
*image*

Here FutureSearch conducts broad research into the facts of the matter. It produces a set of 4-8 facets like the above, each backed by reliable statements cited to their sources.

Doing this well requires choosing good sources, in this case including DOJ’s official pages and specialist analyses like antitrustlawblog.com. Critical is extracting authoritative claims and not treating speculation as fact. There are tradeoffs, because reading hundreds of sources with top-tier LLMs can be expensive and slow, and fine-tuned models help.

After conducting the research, presenting the conclusions is a clustering task that benefits from its own refinement. Getting the distilled “features” of the question - in this case, the specific allegations, and the legal process involved - are crucial for the next step.


### For each key facet, what is the distribution of outcomes from past similar events?
*image*

Everything up until here could be the typical workflow of a diligent generalist. Expert forecasters, though, usually make simple models of their domain to extrapolate outcomes.

First, drawing from the earlier research - the influential actors and key facets - FutureSearch identifies a series of 3-10 reference classes of similar events. Then, it identifies an outcome to analogize to the outcome in question.

Here, the key facet is that the suit is coming from the DOJ, not the FTC. The reference class is DOJ antitrust lawsuits. And the outcome is whether the company had to change their business practices in some way.

Next, FutureSearch conducts a historical search to find a large set of relevant instances of the reference class, and determines what the specified outcome was in each case.

Then, FutureSearch chooses a statistical model for the data found. In this example, it used a beta distribution, guessed a prior, and then did a Bayesian update for each data point to generate a posterior distribution. Note that the prior was very weak, and only got a confident estimate after looking at about 20 data points.


### How do I weigh the conflicting results of the models?
*image*

Here the task is one of interpretation. Models focusing on key features of the situation will give different outputs. Considering all of them together, an expert forecaster would weigh them based on how well they capture the crucial characteristics of the situation, but still have robust data. There’s a tradeoff of generality and specificity.

For example here, one model considers all major lawsuits against Apple, not just antitrust. Another considers antitrust cases against tech companies. Which is more important: that the case is about Apple, or that the case is antitrust?

We generate weights and justifications, and use them to compute a single historical forecast.

### What’s unique about this situation to adjust for in my final answer?
*image*

The final step, synthesis, takes all of the information above: the influential actor profiles, the key facets, the weighted models, and then asks for a single answer.

Much can be said about this synthesis task. Suffice to say, running evals on different methods (see below) given the same input information is crucial.

If the question is yes/no, like this one, the answer will be a probability. “When?” questions get answered with a date distribution, and “What?” or “How many?” questions are answered with a numeric distribution and a choice of units.

## Evals
*image*
*Source: [https://manifold.markets/FUTURESEARCH](https://manifold.markets/FUTURESEARCH)*

FutureSearch uses several methods to evaluate its question-answering skill. The simplest is the above: formulating answers as probabilities, trading in a prediction market, and then checking later what actually happens to evaluate accuracy via profit and loss. (FutureSearch is profitable across a sample of ~75 questions, without any portfolio strategy, simply placing one bet on each question once a week, more [here](https://news.manifold.markets/p/human-v-bots-forecasting-tournament).)

All the final predictions FutureSearch has made are available at the graph link, though the full rationales are only provided to customers.

Other evals are necessary for development, as the real world moves slowly, and some hard questions cannot be easily resolved to produce scores (e.g. “Did Covid19 originate in a lab leak?”). It’s important to have an eval that can be run instantly to evaluate a change.

## Copiloting
Finally, FutureSearch is built to put the user in control. Since the complete research and models are an open box - choice of individual data sources, who to profile along what dimensions, what historical examples to consider - we let users make modifications if they disagree with conclusions, or want to nudge FutureSearch to research or model in a different direction.

All of this copiloting data can then be used for debugging, fine-tuning or training models, or extending systems to handle new cases.

## Other FutureSearch Examples
If you’d like to see a demo on a question relevant to you or your business, [get in touch](https://futuresearch.ai/request-a-demo), and see these other examples:

- [The 2024 U.S. Supreme Court case on whether to uphold emergency abortion care protections](https://app.futuresearch.ai/forecasts/A873f/public)
- [The 2024 U.S. Supreme Court case on whether to grant former presidents immunity from prosecution](https://app.futuresearch.ai/forecasts/iFLVq/public)
- [The New York Times lawsuit on whether OpenAI can continue to serve models train on NYT articles](https://app.futuresearch.ai/forecasts/QsYKs/public)

