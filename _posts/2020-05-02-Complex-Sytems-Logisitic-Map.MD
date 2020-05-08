---
layout: post
title:  "Logistic Map"
date:   2020-05-02 23:13:00
categories: Complex Systems
---
# Logistic Map
Currently I am reading Melanie Mitchell's wonderful book _Complexity: A Guided Tour_. Growing up I was fascinated with ants and hymenoptera in general. When I was studying linguistics I was introduced to language being viewed as a complex adaptive system. Both language and formicae behavior can be studied under the lense of complex systems so naturally I found the subject quite compelling. In the second chapter Mitchell introduces the reader to the logistic map equation. This equation has been used in biology to examine population dynamics but also is a great example of chaos theory, specifically the sensitive dependence on initial conditions. In popular culture this is often referred to as the **Butterfly Effect**.

### Equation:
The logistic map equation is quite simple in appearance, which is one of the reasons it is so appealing to study:


![Logistic Map](/assets/logistic_map.svg)


### Behavior:

There are a lot of interesting qualities about this equation and its behavior is well [documented](https://en.wikipedia.org/wiki/Logistic_map). 

For instance when _R_ is in the interval (0, 1) the population decreases. However, when _R_ is in the interval (1, 2), the population will eventually reach _(R-1)/R_ regardless of the initial population. When _R_ > 3 the population oscillates in different ways. It is when _R_ reaches ~3.56995 that  _chaos_ sets it. The behavior of this equation is far more nuanced than my explanation, but rather than copying from my sources verbatim I am going to use this as oppurtunity to do some basic plotting to show its behavior.

In this first plot we can see the behavior when _R_ = [0,4]. This plot is done with 20 iterations showing that regardless of the value of _x_ the result of the logistic map converges on the same value. However as R approaches 3 the value starts to oscillate and at ~3.56995 the behavior changes dramatically.

![Logistic Map 1](/assets/lm_1.png)

If you zoom in on these values there starts to emerge a discernible pattern. At certain values of R the result oscillates between a different number of results (2, 4, 8...).
![Logistic Map 2](/assets/lm_2.png)

When the equation reaches ~3.56995 the behavior is incredibly different. While this behavior is deemed as _chaotic_ there are patterns within it but that is beyond the scope of this post. 

As a young man, like Laplace, I imagined that if we could measure the world accurately enough the laws of physics would allow us to predict the future to some degree. This chaotic behavior demonstrates one of the reasons why this may not be the case. In this example _R_ is being incremented by .0001. The reason why this is important is because it shows that the result of the equation is dramatically different even when R is +/- 1/10000. Therefore if you were trying to model a population, a weather event, or some other phenomenon with similar behavior, if your initial measurements were off by an incredibly small amount (even +/- .0000000000001), it could still make your predictions wildly different and thus unreliable. This is where the description _sensitive dependence on initial conditions_ comes from.

![Logistic Map 3](/assets/lm_3.png)


