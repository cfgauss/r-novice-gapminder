---
title: Control Flow
teaching: 20
exercises: 10
questions:
- "How can I make data-dependent choices in R?"
- "How can I repeat operations in R?"
objectives:
- "Write conditional statements with `if` and `else`."
- "Write and understand `for` loops."
keypoints:
- "Use `if` and `else` to make choices."
- "Use `for` to repeat operations."
---

Often when we're coding we want to control the flow of our actions. This can be done
by setting actions to occur only if a condition or a set of conditions are met.
Alternatively, we can also set an action to occur a particular number of times.

There are several ways you can control flow in R.

## Conditional Statements

For conditional statements, the most commonly used approaches are the constructs:


~~~
# if
if (condition is true) {
  perform action
}

# if ... else
if (condition is true) {
  perform action
} else {  # that is, if the condition is false,
  perform alternative action
}
~~~
{: .r}

Say, for example, that we want R to print a message if a variable `x` has a particular value:


~~~
# sample a random number from a Poisson distribution
# with a mean (lambda) of 8

x <- rpois(1, lambda=8)

if (x >= 10) {
  print("x is greater than or equal to 10")
}

x
~~~
{: .r}



~~~
[1] 8
~~~
{: .output}

Note you may not get the same output as your neighbour because
you may be sampling different random numbers from the same distribution.

~~~
x <- rpois(1, lambda=8)

if (x >= 10) {
  print("x is greater than or equal to 10")
} else {
  print("x is less than 10")
}
~~~
{: .r}

~~~
[1] "x is less than 10"
~~~
{: .output}

~~~
x <- rpois(1, lambda=8)

if (x >= 10) {
  print("x is greater than or equal to 10")
} else if (10 > x > 6) {
  print("x is between 10 and 6")
} else {
  print("x is less than or equal to 6")
}
~~~
{: .r}

~~~
[1] "x is greater than or equal to 10"
~~~
{: .output}



> ## Tip: pseudo-random numbers
>
> In the above case, the function `rpois` generates a random number following a
> Poisson distribution with a mean (i.e. lambda) of 8. The function `set.seed`
> guarantees that all machines will generate the exact same 'pseudo-random'
> number ([more about pseudo-random numbers](http://en.wikibooks.org/wiki/R_Programming/Random_Number_Generation)).
> So if we `set.seed(10)`, we see that `x` takes the value 8. You should get the
> exact same number.
{: .callout}

**Important:** when R evaluates the condition inside `if` statements, it is
looking for a logical element, i.e., `TRUE` or `FALSE`. This can cause some
headaches for beginners. For example:


~~~
x  <-  4 == 3
if (x) {
  "4 equals 3"
}
~~~
{: .r}

As we can see, the message was not printed because the vector x is `FALSE`


~~~
x <- 4 == 3
x
~~~
{: .r}



~~~
[1] FALSE
~~~
{: .output}

> ## Challenge 1
>
> Use an `if` statement to print a suitable message
> reporting whether there are any records from 2002 in
> the `gapminder` dataset. Then write a similar statement that
> reports if there are both 2002 *and* 2012 records.
{: .challenge}


Did anyone get a warning message like this?


~~~
Warning in if (gapminder$year == 2012) {: the condition has length > 1 and
only the first element will be used
~~~
{: .error}

If your condition evaluates to a vector with more than one logical element,
the function `if` will still run, but will only evaluate the condition in the first
element. Here you need to make sure your condition is of length 1.

> ## Tip: `any` and `all`
>
> The `any` function will return TRUE if at least one
> TRUE value is found within a vector, otherwise it will return `FALSE`.
> This can be used in a similar way to the `%in%` operator.
> The function `all`, as the name suggests, will only return `TRUE` if all values in
> the vector are `TRUE`.
{: .callout}

## While loops


Sometimes you will find yourself needing to repeat an operation until a certain condition is met. You can do this with a `while` loop.

~~~
while(this condition is true){
  do a thing
}
~~~
{: .r}

As an example, here's a while loop
that generates random numbers from a uniform distribution (the `runif` function)
between 0 and 1 until it gets one that's less than 0.1.

~~~
z <- 1
while(z > 0.1){
  z <- runif(1)
  print(z)
}
~~~
{: .r}

`while` loops will not always be appropriate. You have to be particularly careful
that you don't end up in an infinite loop because your condition is never met.


## Repeating operations

If you want to iterate over
a set of values, when the order of iteration is important, and perform the
same operation on each, a `for` loop will do the job.
We saw `for` loops in the shell lessons earlier. This is the most
flexible of looping operations, but therefore also the hardest to use
correctly. Avoid using `for` loops unless the order of iteration is important:
i.e. the calculation at each iteration depends on the results of previous iterations.

The basic structure of a `for` loop is:


~~~
for(iterator in set of values){
  do a thing
}
~~~
{: .r}

For example:


~~~
for(i in 1:10){
  print(i)
}
~~~
{: .r}



~~~
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
[1] 7
[1] 8
[1] 9
[1] 10
~~~
{: .output}

The `1:10` bit creates a vector on the fly; you can iterate
over any other vector as well.

We can use a `for` loop nested within another `for` loop to iterate over two things at
once.


~~~
for(i in 1:5){
  for(j in c('a', 'b', 'c', 'd', 'e')){
    print(paste(i,j))
  }
}
~~~
{: .r}



~~~
[1] "1 a"
[1] "1 b"
[1] "1 c"
[1] "1 d"
[1] "1 e"
[1] "2 a"
[1] "2 b"
[1] "2 c"
[1] "2 d"
[1] "2 e"
[1] "3 a"
[1] "3 b"
[1] "3 c"
[1] "3 d"
[1] "3 e"
[1] "4 a"
[1] "4 b"
[1] "4 c"
[1] "4 d"
[1] "4 e"
[1] "5 a"
[1] "5 b"
[1] "5 c"
[1] "5 d"
[1] "5 e"
~~~
{: .output}

Rather than printing the results, we could write the loop output to a new object.


~~~
output_matrix <- matrix(nrow=5, ncol=5)
for(i in 1:5){
  for(j in c('a', 'b', 'c', 'd', 'e')){
    temp_output <- paste(i, j)
    output_matrix[i, j] <- temp_output
  }
}
output_vector2 <- as.vector(output_matrix)
output_vector2
~~~
{: .r}



~~~
 [1] "1 a" "1 b" "1 c" "1 d" "1 e" "2 a" "2 b" "2 c" "2 d" "2 e" "3 a"
[12] "3 b" "3 c" "3 d" "3 e" "4 a" "4 b" "4 c" "4 d" "4 e" "5 a" "5 b"
[23] "5 c" "5 d" "5 e"
~~~
{: .output}

This approach can be useful, but 'growing your results' (building
the result object incrementally) is computationally inefficient, so avoid
it when you are iterating through a lot of values.

> ## Tip: don't grow your results
>
> One of the biggest things that trips up novices and
> experienced R users alike, is building a results object
> (vector, list, matrix, data frame) as your for loop progresses.
> Computers are very bad at handling this, so your calculations
> can very quickly slow to a crawl. It's much better to define
> an empty results object before hand of the appropriate dimensions.
> So if you know the end result will be stored in a matrix like above,
> create an empty matrix with 5 row and 5 columns, then at each iteration
> store the results in the appropriate location.
{: .callout}

A better way is to define your (empty) output object before filling in the values.
For this example, it looks more involved, but is still more efficient.


~~~
output_matrix <- matrix(nrow=5, ncol=5)
j_vector <- c('a', 'b', 'c', 'd', 'e')
for(i in 1:5){
  for(j in 1:5){
    temp_j_value <- j_vector[j]
    temp_output <- paste(i, temp_j_value)
    output_matrix[i, j] <- temp_output
  }
}
output_vector2 <- as.vector(output_matrix)
output_vector2
~~~
{: .r}

~~~
 [1] "1 a" "2 a" "3 a" "4 a" "5 a" "1 b" "2 b" "3 b" "4 b" "5 b" "1 c"
[12] "2 c" "3 c" "4 c" "5 c" "1 d" "2 d" "3 d" "4 d" "5 d" "1 e" "2 e"
[23] "3 e" "4 e" "5 e"
~~~
{: .output}

> ## Challenge 2
>
> Write a script that loops through the `gapminder` data by continent and
> prints out the continent, the mean life expectancy on that continent, and
> whether or not that life expectancy is larger than 65 years. *Hints:* If `x`
> is a numeric vector, `mean(x)` returns the mean of `x`. For any vector `x`,
> `unique(x)` returns a vector with the unique values of `x`. Finally `cat("x
> is",6)` prints `x is 6`.
{: .challenge}

> ## Challenge 3
>
> Modify the script from Challenge 4 to loop over each country. This time
> print out whether the life expectancy is smaller than 50, between 50 and 70,
> or greater than 70.
{: .challenge}
