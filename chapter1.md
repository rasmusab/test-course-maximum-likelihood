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

Let's start with *what* likelihood is.

In statistics likelihood refers to how likely some data is given some *probability model*. The most basic probability models are often called probability *distributions*.  


*** =instructions

In the code to the right we generate 100 random draws from a normal distribution. Change the `mean` of the normal distribution so that the most likely outcome would be the value 42.


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


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:f39da61dd9
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

