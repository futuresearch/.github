# Welcome to [FutureSearch](http://futuresearch.ai)!

### FutureSearch gives **unbiased**, **deeply-researched** answers to **hard** questions about the world.

This page describes how FutureSearch answers judgment-heavy questions other AI systems fall short on.

- [Reasoning with LLMs](#reasoning-with-llms)
  - [Six steps to answer hard questions](#six-steps-to-answer-hard-questions)
- [Doing the Research](#doing-the-research)
  - [Summary of the Situation](#1-what-is-a-basic-summary-of-this-situation)
  - [Important People and Their Dispositions](#2-who-are-the-important-people-involved-and-what-are-their-dispositions)
  - [Deep Research on Key Facets](#3-what-are-the-key-facets-of-the-situation-that-will-influence-the-outcome)
  - [Distribution of Historical Outcomes for Each Facet](#4-what-is-the-distribution-of-historical-outcomes-for-each-facet)
  - [Weighing Conflicting Model Results](#5-how-do-i-weigh-the-conflicting-results-of-the-models)
  - [Final Adjustments and Answer](#6-whats-unique-about-this-situation-to-adjust-for-in-my-final-answer)
- [Evals](#evals)
- [Copiloting](#copiloting)

## Just Show Me Examples

- [The DOJ’s antitrust suit against Apple](https://app.futuresearch.ai/forecasts/eMocg/public)
- [The New York Times lawsuit on whether OpenAI can train & serve on their data](https://app.futuresearch.ai/forecasts/QsYKs/public)
- [The 2024 U.S. Supreme Court case on whether to uphold emergency abortion care protections](https://app.futuresearch.ai/forecasts/A873f/public)
- [The 2024 U.S. Supreme Court case on whether to grant former presidents immunity from prosecution](https://app.futuresearch.ai/forecasts/iFLVq/public)

## Reasoning with LLMs
FutureSearch is different from other LLM-based research and analysis tools in that it relies on the [techniques of modern judgmental forecasting](https://en.wikipedia.org/wiki/Superforecasting:_The_Art_and_Science_of_Prediction).

In one-shot reasoning tasks, LLMs fall short in answering questions with uncertainty and that require judgment:
- They give excessively cautious and nonspecific answers;
- They perform worse on partisan questions, or refuse to answer them outright;
- They don’t ground their claims statistically in concrete evidence;
- They have cognitive biases: gullibility, availability heuristic, anchoring, etc.

Consider the first example, how the antitrust case will go against Apple. An expert forecaster tasked with this, armed with Google and a spreadsheet, might take this approach:

### Six steps to answer hard questions

1. What is a basic summary of this situation?
2. Who are the important people involved, and what are their dispositions?
3. What are the key facets of the situation that will influence the outcome?
4. For each key facet, what’s a simple model of the distribution of outcomes from past instances that share that facet?
5. How do I weigh the conflicting results of the models?
6. What’s unique about this situation to adjust for in my final answer?

We’ve found this breakdown to be fairly robust across many types of judgment-heavy questions - law, economics, politics, business (see [evals](#evals)). If each stage goes well, the final answer can be superhuman in quality, and laying out the full set of findings can be [quite valuable in their own right](https://forum.effectivealtruism.org/posts/qMP7LcCBFBEtuA3kL/the-rationale-shaped-hole-at-the-heart-of-forecasting).

FutureSearch takes ~10 minutes to do this research and modeling workflow, even on domains where it's never answered a question before.

## Doing the Research
There are a variety of techniques to get higher quality outputs for each stage or subtask: prompt engineering, self-reflection, chain-of-thought, skeleton-of-thought, graph-of-thought, agent-loops, writing and executing  programs. For gathering information, there is trained knowledge of various LLMs, websearch, structured data from places like Wikipedia, news databases, and many sources of proprietary data. (LLMs speak many languages too.) There are a variety of LLMs to use, and there’s fine-tuning.

We don’t here describe which combinations of these techniques we use to produce each result, that’s the FutureSearch special sauce. But we will suggest some subtasks we have to handle to get great results.

Let’s look at a customer question, [Will the DOJ’s antitrust suit against Apple result in Apple being forced to change its business?](https://app.futuresearch.ai/forecasts/eMocg/public), and see how we apply the six steps.

### 1. What is a basic summary of this situation?
![background](/README-background.png)
This task is easy in this example, as we need only find and summarize the right Wikipedia article. In many cases it is more challenging, especially on breaking news. Done quickly and accurately, all subsequent stages can be seeded with this context, which can guide the initial stages of research on those steps.

In this case, the key things to find that improve later results are (a) that the suit is from the DOJ, not the FTC, and (b) that there are many distinct claims against Apple, not just their App Store practices.

### 2. Who are the important people involved, and what are their dispositions?
![profile](/README-profile.png)

Here the complexity of the world begins to creep in. In this case, FutureSearch decided Tim Cook, Merrick Garland (US Attorney General), and Jonathan Kanter (Assistant Attorney General) were the key figures, and not for example Lina Khan (head of FTC) or Joe Biden.

The first challenge, identifying the right people, can be quite nuanced. In the linked SCOTUS examples, the challenge is identifying the swing justices. In European politics, there are many heads of state that may turn out to be decisive.

Once FutureSearch chooses the actors, it decides on a series of dimensions to analyze. Here, Tim Cook’s willingness to settle lawsuits is a key feature to assess. For Merrick Garland, how they conducted previous suits against large tech companies could be a good predictor of their prosecution against Apple.

Finally, for each dimension of each actor, FutureSearch conducts research to find a series of observations of what the person has said or done, and then summarizes them to make an assessment. It cites each observation to its source - in this case, part of the FutureSearch Knowledge Base.

### 3. What are the key facets of the situation that will influence the outcome?
![fact cluster](/README-fact-cluster.png)

Next FutureSearch conducts broad research into the facts of the matter. It produces a set of 4-8 facets like the above, each backed by reliable factual statements cited to their sources.

Doing this well requires choosing good sources, in this case including DOJ’s official pages and specialist analyses like antitrustlawblog.com. Critical is extracting authoritative claims and not treating speculation as fact. There are tradeoffs, because reading hundreds of sources with top-tier LLMs can be expensive and slow, and fine-tuned or multiple passes of increasing quality through articles, can help.

After conducting the research, presenting the conclusions is a clustering task. Getting the distilled “facets” of the question - in this case, the specific allegations, and the legal process involved - are crucial for the next step.

### 4. What is the distribution of historical outcomes for each facet?
![model](/README-model.png)

Everything up until here could be the typical workflow of a diligent generalist. Expert forecasters, though, usually make simple models of their domain to extrapolate outcomes.

First, drawing from the earlier research - the influential actors and key facets - FutureSearch identifies a series of 3-10 reference classes of similar events. Then, it identifies an outcome to analogize to the outcome in the user's question.

In this example, the key facet is that the suit is coming from the DOJ, not the FTC. The reference class is DOJ antitrust lawsuits. And the outcome is whether the company had to change their business practices in some way.

Next, for each reference class, FutureSearch conducts a historical search to find a large set of matching instances, and then determines what the specified outcome was in each case.

Finally, FutureSearch chooses a statistical model for the data found. In this example, it used a beta distribution, guessed a prior, and then did a Bayesian update for each data point to generate a posterior distribution. Time-series and Poisson distributions are commonly useful too.

In this example, the prior was very weak, and FutureSearch only arrived at a confident estimate after looking at the outcomes of ~20 instances matching the reference class.

### 5. How do I weigh the conflicting results of the models?
![weights](/README-weights.png)

Here the task is one of interpretation. Statistical models focusing on key features of the situation will imply different answers to the original question. Considering all of them together, an expert forecaster would weigh the tradeoff between specificity - historical events that closely match the current situation - and generality, where one can find many more data points. closely matching the currentthem based on how well they capture the crucial characteristics of the situation, but still have robust data. There’s a tradeoff of generality and specificity.

For example here, one model considers all major lawsuits against Apple, not just antitrust. Another considers antitrust cases against tech companies. Which is more important: that the case is about Apple, or that the case is antitrust?

We generate weights and justifications, and use them to compute a single historical forecast.

### 6. What’s unique about this situation to adjust for in my final answer?
![forecast](/README-forecast.png)

The final step, synthesis, takes all of the information above: the influential actor profiles, the key facets, the weighted models, and then asks for a single answer.

Much can be said about this synthesis task. Suffice to say, running evals on different methods (see below) given the same input information is crucial.

If the question is yes/no, like this one, the answer will be a probability. “When?” questions get answered with a date distribution, and “What?” or “How many?” questions are answered with a numeric distribution and a choice of units.

## Evals
![Manifold](/README-manifold.png)

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

