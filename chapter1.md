---
title       : What is likelihood?
description : Before we maximize the likelihood we need to know what it is.

--- type:NormalExercise lang:r  xp:100 skills:1,7 key:0f9caee3f2

*Maximum likelihood estimation* is a widely used method in both statistics and machine learning. It's used in everything from simple procedures, such as the t-test and linear regression, to more advanced methods like hierarchical models and neural networks. Understanding what maximum likelihood estimation  is and how it works is *crucial* if you want to understand more advanced statistical methods. Fortunately, it's not that difficult!

To understand maximum likelihood estimation (or MLE for short) you need to understand

  * *What* likelihod is.
  * *Why* you would want to maximize it.
  * And *how* you can maximize it.

Let's start with *what* likelihood is.



*** =instructions

*** =hint

*** =pre_exercise_code

*** =sample_code

*** =solution

*** =sct

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:f39da61dd9
## A really bad movie

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

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f1128290
## More movies

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
