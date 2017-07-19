---
title       : What is likelihood?
description : Before we maximize the likelihood we need to know what it is.


--- type:NormalExercise lang:r  xp:100 skills:1,7 key:0f9caee3f2
## Introducing maximum likelihood

*Maximum likelihood estimation* is a widely used method in both statistics and machine learning. It's used in everything from simple procedures, such as the t-test and linear regression, to more advanced methods like hierarchical models and neural networks. Understanding what maximum likelihood estimation  is and how it works is *crucial* if you want to understand more advanced statistical methods. Fortunately, it's not that difficult!

To understand maximum likelihood estimation (or MLE for short) you need to understand

  * *What* likelihod is.
  * *Why* you would want to maximize it.
  * And *how* you can maximize it.

Let's start with *what* likelihood is, which this chapter is all about. In statistics likelihood refers to how likely some data is given some *probability model*. So to grok likelihood you need to know a little about probability models, so let's start there. 

The most basic probability models are often called probability *distributions*. You might have heard of probability distributions like the binomial distribution, the poisson distribution and the exponential distribution. But, by far, the most common example of a distribution is the *normal distribution*. So let's take a look at that one. 


*** =instructions

In the code to the right we generate 100 random draws from a normal distribution. Change the `mean` of the normal distribution so that the most *likely* outcome would be the value 42.


*** =hint

The `mean` defines the center of the normal distribution, and most draws from a normal distribution will be close to the center.


*** =sample_code
```{r}
# Here we draw 100 random draws from a normal distribution
y <- rnorm(n = 100, mean = ___, sd = 1)

# And plot the result as a histogram
hist(y)
```
*** =solution
```{r}
# Here we draw 100 random draws from a normal distribution
y <- rnorm(n = 100, mean = 42, sd = 1)

# And plot the result as a histogram
hist(y)
```
*** =sct
```{r}
test_function("rnorm", args = "mean")
test_error()
success_msg("Good work!")
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:7 key:f39da61dd9
## The term likelihood

In what context do you usually use the term *likelihood* in statistical modeling?

*** =instructions
- The likelihood of *the parameters*.
- The likelihood of *the data*.
- The likelihood of *the probability*.
- The likelihood of *the model*

*** =hint
*Likelihood* is a term from classical statistics where the model and the parameters are assumed fixed



*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That's not usually how it's used..."
msg_success <- "Yep! The term likelihood is used when talking about how likely some data is to be generated from a given statistical model."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:7 key:bfc8ebf3bf
## Guess the mean

This histogram shows 1000 draws from a normal distribution. Looking at this histogram, what parameters would be most likely to generate this data?

*** =pre_exercise_code
```{r}
y <- rnorm(n = 1000, mean = 100, sd = 10)
hist(y, 100, col = "lightblue")
```

*** =instructions
- A mean of 42 and a standard deviation of 10.
- A mean of 100 and a standard deviation of 50.
- A mean of 150 and a standard deviation of 100.
- A mean of 100 and a standard deviation of 10.

*** =hint


The mean is the center of the normal distribution that generated this data, and the standard deviation defines the spread, where around 68% of the data would be within one standard deviation from the mean.


*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "Mmmm, that doesn't seem likely..."
msg_success <- "Right! Out of these option a mean of 100 and a standard deviation of 10 seems pretty likely."
test_mc(correct = 4, feedback_msgs = c(msg_bad, msg_bad, msg_bad, msg_success))
```


--- type:NormalExercise lang:r xp:100 skills:1,7 key:03d21d51b4
## What is a probability model?

A probability model, like the normal distribution, is a function that defines how likely different outcomes are. For example, a normal distribution defines how likely a continous outcome from $-\infty$ to $\infty$ is. Most interesting probability models have *parameters* that changes this likelihood. The normal distribution has two parameters, the *mean* which defines what outcome is the most likely and the *standard deviation* which defines how centered the likelihood of outcomes is around the mean, a small standard deviation and it's very likely that outcomes will be close to the mean, a larger standard deviation and it's more likely the outcomes will be far away.

The are an infinite number of possible probability models, but the most common and useful ones are often called probbaility distributions. In R there are many more probability distributions that the normal distribution, let's look at some more!

*** =instructions

To the right is code that samples from some more probability distributions that are available in R. Try out parameter different parameter values and see how that changes the distribution of the generated samples. There are no wrong answers to this question, just explore! 

*** =hint

No wrong answer here, just try out some different parameters. However, some of the parameters has to be positive and one of the parameters can only be between 0.0 and 1.0.

*** =sample_code
```{r}
# The poisson distribution, defines the likelihood of non-negative whole numbers.
pois_sample <- rpois(n = 1000, lambda = ___)
hist(pois_sample, col = "green")

# The exponential distribution, defines the likelihood of non-negative continous numbers.
exp_sample <- rexp(n = 1000, rate = ___)
hist(exp_sample, col = "green")

# The binomial distribution, defines the likelihood of whole numbers from 0 to size.
binom_sample <- rbinom(n = 1000, size = 10, prob = ___)
hist(binom_sample, col = "green")
```

*** =solution

```{r}
# The poisson distribution, defines the likelihood of non-negative whole numbers.
pois_sample <- rpois(n = 1000, lambda = 10)
hist(pois_sample, col = "green")

# The exponential distribution, defines the likelihood of non-negative continous numbers.
exp_sample <- rexp(n = 1000, rate = 1 / 5)
hist(exp_sample, col = "green")

# The binomial distribution, defines the likelihood of whole numbers from 0 to size.
binom_sample <- rbinom(n = 1000, size = 10, prob = 0.3)
hist(binom_sample, col = "green")
```

*** =sct
```{r}
test_error()
success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1,7 key:7b21ab4f00
## Calculating the likelihood directly


*** =instructions


*** =hint


*** =sample_code
```{r}

```

*** =solution

```{r}

```

*** =sct
```{r}

```