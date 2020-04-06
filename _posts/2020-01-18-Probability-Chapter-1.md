---
layout: post
title:  "Introduction to Probabilistic Models 1"
date:   2020-01-18 08:49:00 -0500
categories: Math
---
# Introduction
So what follows is the beginning of a series of posts I will be making while going through Sheldon Ross's _Introduction to Probability Models 10ed._.
Now that I have graduated I have a little more time to dedicate to topics that I find interesting. One of the topics I find most interesting is math, particularly probability, statistics, and how they can be used to model language. A lot of Ross's book will be a review for me so I am hoping to hammer out some of the finer details that I may have missed when I first started studying probability.

## Why this _Introduction to Probability Models_ ?
	So I have been exposed to a lot of different materials with regard to math especially with regard to probability and statistics. I have read some of Jaynes _Probability Theory_, about half of McElreaths _Statistical Rethinking_, and been exposed to a variety of different books with regard to probability especially from the viewpoint of machine learning. I have chosen this book because A) I am looking for a book strictly about probability and B) so far Ross's book has been these most accessible. There seems to be little _fluff_ in this book. The topics are clearly outlined. The chapters are short and to the point. The exercises are illuminating. I am hoping to review a lot of topics and learn some new stuff along the way. If you are also following along, maybe you will too.

## Chapter 1
In chapter 1 we will be looking at the following topics:
- Sample Spaces and Events
- Probabilities Defined on Events
- Conditional Probability 
- Indepence
- Bayes' Rule/Formula

All of these topics are rather rudimentary so this discussion will be brief.

### Sample Space and Events
- A sample space can be defined as all of the outcomes that are possible given an experiment. If we are talking about a coin being flipped once then this _sample space_ can be defined as:
$$S=[H,T]$$

An event in this sample space (S), can be defined as any subset of the this sample space. In the easy case above there are only two events heads(H) or tails (T)

Now obviously this idea extends to anything. Often you will see examples looking at dice, cards, or jars of colored balls etc. If we have two coins and are flipping them each once or _one coin but flipping it twice_ then the sample space would be:
S=[(H,H),(H,T),(T,H),(T,T)]

In this latter case then the set of events are simply the cartesian product of the outcomes of the two coins. Each of the combinations of heads and tails in the above example are events. If you are familiar with set theory the sample space can be defined as the cartesian product of the sets of events.

##### Unions and Intersections of events
If we have multiple events often we want to talk about how these events occur and whether or not they occur together. For two separate events _A_ and _B_ we describe their _union_ as A or B occuring. As an example , if event _A_ is (H,H) and event _B_ is (H,T) then there union is the subset of S [(H,H), (H,T)] 

UNION PIC

If _union_ can be described as _A or B occuring_ then _intersection_ can be described as A and B both occuring. If _A_ is the event that the first coin is heads and _B_ is the event that the second coin is heads then the interesection can be defined as (H,H). 

INTERSECTION PIC

##### Mutually Exclusive
Now sometimes two events _cannot_ cooccur. In this instance we refer to these events as being _mutually exclusive_. For a really obviously example of this, consider the two events _A_ the first coin is heads and _B_ the first coin is tails. Now obviously if you flip the coin it has to land on either heads or tails so in this case the set of events that represent the intersection of _A_ and _B_ is empty. These two events are thus _mutually exclusive_.

MUTUALLY Exclusive Pic

##### Complement
The above example can also help us illustrate another concept and that is the _complement_. The _complement_ of an event _A_ can be be described as the set of all events in the sample space that are not _A_. The _complements_ of an event and the event are always mutually exclusive. If we are flipping two coins and we describe event _A_ as the event that first coin is heads, then the complement is the subset of the sample space where _A_ is not heads namely:
A^c = [(T,H),(T,T)]
where A would equal:
A = [(H,H),(H,T)]

##### Sets of sets
Now often when we are discussing events we don't just want to talk about single outcomes such as a coin landing heads. Often we want to talk about lots of different events. We can apply the same notions of _intersection_, _union_, _complement_, and _mutual exclusion_ on sets of events. For this we use the same symbols from above but larger.


## Probabilites of Events
Looking back at the previous examples we can now define the probability of events E_n in the sample space S as P(E). There are three conditions for describing these probabilities

1) 0<= P(E) <= 1
2) P(S) = 1
3) Given a set of events in S that are mutually exclusive the probability of the union of those events is equal to the sum of their probabilities, or:

P(UE) = SUM(E_N)

A nice feature of this if we have two events E and complementE then their Union will equal S and thus the probability of their union is 1

If we are looking at two events who are not mutually exclusive then we can define the probability of their union as

P(EuF) = P(E)+P(F) - P(EF).

The reason for subtracting their intersection is that any events that occur in both E and F will also occur in E and F individually. If we did not subtract these events they would be counted twice. A really nice way to see this is to draw out these events as a ven diagram. This property of adding the individual probabilities and then subtracting their intersections can be extended  to as the _inclusion-exclusion identity_. 

## Conditional Probabilities
Conditional probabilities are a way to talk about probability when you are given information that affects the outcome in a sample space. For instance in our coin flipping example with two coins, if you are given the information that the first coin was heads, it eliminates certain outcomes. If we know the first coin is heads then the only possible outcomes are [(H,H),(H,T)]. Conditional probability is defined as:

P(E|F) = P(EF)/P(F)

Ex: If we flip two coins the probability of the outcome being (H,H) is 1/4
However the conditional probability of (H,H) given that the first coin is heads is 1/2. Why?
If F is the event the first coin is heads and E is the event the second coin is heads then looking back at our sample space we have:

S = [(H,H),(H,T),(T,H),(T,T)]
E = [(H,H),(T,H)]
F = [(H,H),(H,T)]
EF = [(H,H)] 

and

P(EF) = 1/4 ; P(F) = 2/4
then P(E|F) = (1/4)/(2/4) = 1/2

This is a very simple example and almost seems illogical because the second coin flip isn't affected by the first coin flip. However, what is affected by knowing the first coin flip is the subset of possible outcomes. 

Let's look at a more complicated example:
A deck of cards consists of 26 red cards and 26 black cards. If we define event F as you drawing a black card and event E as you drawing a red card, we can ask: What is the probability of E given F? How does the probability of E change as a result of F?

P(F) = 26/52 = 1/2
P(E) = 26/52 = 1/2
P(EF)= (26/52)*(26/51)
P(E|F) = P(EF)/P(F) = 26/51

One of the hardest things about probability is figuring out how to describe events. It is a very common pitfall to describe P(EF)= 0 which would make the probability of P(E|F) which is obviously false. Really, using just your intuition one can see that the probability of drawing black card after drawing a red card is 26/51. Understanding how to formulate this though is just as important as the formulas themselves.

### Indepence
Two events are said to be independent if the probability of their interesection is equal to the product of their individual probabilities, or:

P(EF) = P(E)*P(F) and therefore
P(E|F) = P(E)

Independence is important because it helps us to understand how different events affect each other. A lot of statistical tests will make assumptions regarding independence. One of the most important concepts in statistics is knowing that the models you create are just that _models_. These models often explicitly make assumptions about independence which may not accuratley represent the real world. Understanding this is crucial in the real world because often these assumptions do not accurately reflect reality and can make us overconfident in our predictions. Events that are not independent are said to be dependent.

### Bayes' Formula
Bayes' formula is an extension of the conditional probability we discussed above. What is different from the conditional probability is that now is that when we formulate the denominator we extend it to explicitly state that it regards all events where are conditional event could occur. Specifically,

BAYES' formula
