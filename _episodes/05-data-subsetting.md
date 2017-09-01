---
title: Subsetting Data
teaching: 30
exercises: 15
questions:
- "How can I work with subsets of data in R?"
objectives:
- "To be able to subset vectors, factors, and data frames"
- "To be able to extract individual and multiple elements: by index, by name, using comparison operations"
- "To be able to skip and remove elements from various data structures."
keypoints:
- "Indexing in R starts at 1, not 0."
- "Access individual values by location using `[]`."
- "Access slices of data using `[low:high]`."
- "Access arbitrary sets of data using `[c(...)]`."
- "Use `which` to select subsets of data based on value."
---


Much of R's power comes from it's vectorization. R has many powerful subset operators and mastering them will allow you to
easily perform complex operations on any kind of dataset without the resource depletion of loops.

There are a few different ways we can subset any kind of object, and
different subsetting operators for the different data structures.

Let's start with a data structure we've seen before, the workhorse of R: atomic vectors.


~~~
x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
~~~
{: .r}

We can name elements within our vectors using the `names` function. Here, we have named each element 
with a different letter of the alphabet.

~~~
names(x) <- c('a', 'b', 'c', 'd', 'e')
x
~~~
{: .r}

~~~
  a   b   c   d   e 
5.4 6.2 7.1 4.8 7.5 
~~~
{: .output}

So now that we've created a dummy vector to play with, how do we get at its
contents?

## Accessing elements using their indices

To extract elements of a vector we can give their corresponding index, starting
from one:


~~~
x[1]
~~~
{: .r}



~~~
  a 
5.4 
~~~
{: .output}


~~~
x[4]
~~~
{: .r}



~~~
  d 
4.8 
~~~
{: .output}

It may look different, but the square brackets operator is a function. For atomic vectors
(and matrices), it means "get me the nth element".

We can ask for multiple elements at once:


~~~
x[c(1, 3)]
~~~
{: .r}



~~~
  a   c 
5.4 7.1 
~~~
{: .output}

Or slices of the vector:


~~~
x[1:4]
~~~
{: .r}



~~~
  a   b   c   d 
5.4 6.2 7.1 4.8 
~~~
{: .output}

Remember that the `:` operator creates a sequence of numbers from the left element to the right. Using it inside the square 
brackets lets us select a range of elements.

We can ask for the same element multiple times:


~~~
x[c(1,1,3)]
~~~
{: .r}



~~~
  a   a   c 
5.4 5.4 7.1 
~~~
{: .output}

If we ask for a number outside of the vector, R will return missing values:


~~~
x[6]
~~~
{: .r}



~~~
<NA> 
  NA 
~~~
{: .output}

This is a vector of length one containing an `NA`, whose name is also `NA`.

If we ask for the 0th element, we get an empty vector:


~~~
x[0]
~~~
{: .r}



~~~
named numeric(0)
~~~
{: .output}

> ## Vector numbering in R starts at 1
>
> In many programming languages (C and python, for example), the first
> element of a vector has an index of 0. In R, the first element is 1.
{: .callout}

## Skipping and removing elements

If we use a negative number as the index of a vector, R will return
every element *except* for the one specified:


~~~
x[-2]
~~~
{: .r}



~~~
  a   c   d   e 
5.4 7.1 4.8 7.5 
~~~
{: .output}


We can skip multiple elements:


~~~
x[c(-1, -5)]  # or x[-c(1,5)]
~~~
{: .r}



~~~
  b   c   d 
6.2 7.1 4.8 
~~~
{: .output}

> ## Tip: Order of operations
>
> A common trip up for novices occurs when trying to skip
> slices of a vector. Most people first try to negate a
> sequence like so:
>
> 
> ~~~
> x[-1:3]
> ~~~
> {: .r}
>
> This gives a somewhat cryptic error:
>
> 
> ~~~
> Error in x[-1:3]: only 0's may be mixed with negative subscripts
> ~~~
> {: .error}
>
> But remember the order of operations. `:` is really a function, so
> what happens is it takes its first argument as -1, and second as 3,
> so generates the sequence of numbers: `c(-1, 0, 1, 2, 3)`.
>
> The correct solution is to wrap that function call in brackets, so
> that the `-` operator applies to the results:
>
> 
> ~~~
> x[-(1:3)]
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>   d   e 
> 4.8 7.5 
> ~~~
> {: .output}
{: .callout}


To remove elements from a vector, we need to assign the results back
into the variable:


~~~
x <- x[-4]
x
~~~
{: .r}



~~~
  a   b   c   e 
5.4 6.2 7.1 7.5 
~~~
{: .output}

> ## Challenge 1
>
> Given the following code:
>
> 
> ~~~
> x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
> names(x) <- c('a', 'b', 'c', 'd', 'e')
> print(x)
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>   a   b   c   d   e 
> 5.4 6.2 7.1 4.8 7.5 
> ~~~
> {: .output}
>
> Come up with at least 2 different commands that will produce the following output:
>
> 
> ~~~
>   b   c   d 
> 6.2 7.1 4.8 
> ~~~
> {: .output}
>
> After you find 2 different commands, compare notes with your neighbour. Did you have different strategies?
>
> > ## Solution to challenge 1
> >
> > Use the `c` function:
> > ~~~
> > x[c(2,3,4)]
> > ~~~
> > {: .r}
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > 
> > Use the colon operator:
> > 
> > ~~~
> > x[2:4]
> > ~~~
> > {: .r}
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > Select elements by name:
> > 
> > ~~~
> > x[c("b", "c", "d")]
> > ~~~
> > {: .r}
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > Use the `-` (NOT) along with the `c` function to remove elements you don't want:
> > 
> > ~~~
> > x[-c(1,5)]
> > ~~~
> > {: .r}
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > {: .output}
> >
> {: .solution}
{: .challenge}

## Subsetting by name

We can extract elements by using their name, instead of index:


~~~
x[c("a", "c")]
~~~
{: .r}



~~~
  a   c 
5.4 7.1 
~~~
{: .output}

This is usually a much more reliable way to subset objects: the
position of various elements can often change when chaining together
subsetting operations, but the names will always remain the same!

Unfortunately we can't skip or remove elements so easily when we extract them by their name.

To skip (or remove) a single named element:


~~~
x[-which(names(x) == "a")]
~~~
{: .r}



~~~
  b   c   d   e 
6.2 7.1 4.8 7.5 
~~~
{: .output}

The `which` function returns the indices of all `TRUE` elements of its argument.
Remember that expressions evaluate before being passed to functions. Let's break
this down so that its clearer what's happening.

First this happens:


~~~
names(x) == "a"
~~~
{: .r}



~~~
[1]  TRUE FALSE FALSE FALSE FALSE
~~~
{: .output}

The condition operator is applied to every name of the vector `x`. Only the
first name is "a" so that element is TRUE.

`which` then converts this to an index:


~~~
which(names(x) == "a")
~~~
{: .r}



~~~
[1] 1
~~~
{: .output}



Only the first element is `TRUE`, so `which` returns 1. Now that we have indices
the skipping works because we have a negative index!

Skipping multiple named indices is similar, but uses a different comparison
operator:


~~~
x[-which(names(x) %in% c("a", "c"))]
~~~
{: .r}



~~~
  b   d   e 
6.2 4.8 7.5 
~~~
{: .output}

The `%in%` goes through each element of its left argument, in this case the
names of `x`, and asks, "Does this element occur in the second argument?".

> ## Challenge 2
>
> Run the following code to define vector `x` as above:
>
> 
> ~~~
> x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
> names(x) <- c('a', 'b', 'c', 'd', 'e')
> print(x)
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>   a   b   c   d   e 
> 5.4 6.2 7.1 4.8 7.5 
> ~~~
> {: .output}
>
> Given this vector `x`, what would you expect the following to do?
>
>~~~
> x[-which(names(x) == "g")]
>~~~
>{: .r}
>
> Try out this command and see what you get. Did this match your expectation?
> Why did we get this result? (Tip: test out each part of the command on it's own - this is a useful debugging strategy)
>
> Which of the following are true:
>
> * A) if there are no `TRUE` values passed to `which`, an empty vector is returned
> * B) if there are no `TRUE` values passed to `which`, an error message is shown
> * C) `integer()` is an empty vector
> * D) making an empty vector negative produces an "everything" vector
> * E) `x[]` gives the same result as `x[integer()]`
>
> > ## Solution to challenge 2
> >
> > A and C are correct.
> >
> > The `which` command returns the index of every `TRUE` value in its
> > input. The `names(x) == "g"` command didn't return any `TRUE` values. Because
> > there were no `TRUE` values passed to the `which` command, it returned an
> > empty vector. Negating this vector with the minus sign didn't change its
> > meaning. Because we used this empty vector to retrieve values from `x`, it
> > produced an empty numeric vector. It was a `named numeric` empty vector
> > because the vector type of x is "named numeric" since we assigned names to the
> > values (try `str(x)` ).
> {: .solution}
{: .challenge}

> ## Tip: Non-unique names
>
> You should be aware that it is possible for multiple elements in a
> vector to have the same name. (For a data frame, columns can have
> the same name --- although R tries to avoid this --- but row names
> must be unique.) Consider these examples:
>
>
>~~~
> y <- 1:3
> y
>~~~
>{: .r}
>
>
>
>~~~
>[1] 1 2 3
>~~~
>{: .output}
>
>
>
>~~~
> names(y) <- c('a', 'a', 'a')
> y
>~~~
>{: .r}
>
>
>
>~~~
>a a a 
>1 2 3 
>~~~
>{: .output}
>
>
>
>~~~
> y['a']  # only returns first value
>~~~
>{: .r}
>
>
>
>~~~
>a 
>1 
>~~~
>{: .output}
>
>
>
>~~~
> y[which(names(y) == 'a')]  # returns all three values
>~~~
>{: .r}
>
>
>
>~~~
>a a a 
>1 2 3 
>~~~
>{: .output}
{: .callout}


> ## Tip: Getting help for operators
>
> Remember you can search for help on operators by wrapping them in quotes:
> `help("%in%")` or `?"%in%"`.
>
{: .callout}


So why can't we use `==` like before? That's an excellent question.

Let's take a look at the comparison component of this code:


~~~
names(x) == c('a', 'c')
~~~
{: .r}



~~~
Warning in names(x) == c("a", "c"): longer object length is not a multiple
of shorter object length
~~~
{: .error}



~~~
[1]  TRUE FALSE  TRUE
~~~
{: .output}

Obviously "c" is in the names of `x`, so why didn't this work? `==` works
slightly differently than `%in%`. It will compare each element of its left argument
to the corresponding element of its right argument.

Here's a mock illustration:


~~~
c("a", "b", "c", "d", "e")  # names of x
   |    |    |    |    |    # The elements == is comparing
c("a", "c")
~~~
{: .r}

Remember from our last lesson, when one vector is shorter than the other, it gets *recycled*:


~~~
c("a", "b", "c", "d", "e")  # names of x
   |    |    |    |    |    # The elements == is comparing
c("a", "c", "a", "c", "a")
~~~
{: .r}

In this case R simply repeats `c("a", "c")` two and a half times. If the longer
vector length isn't a multiple of the shorter vector length, then
R will also print out a warning message.

This difference between `==` and `%in%` is important to remember,
because it can introduce hard to find and subtle bugs!


## Using Logical Operations to Subset Data

We can subset data by using boolean vectors:

~~~
x[c(TRUE, TRUE, FALSE, FALSE, FALSE)]
~~~
{: .r}



~~~
a a 
1 2 
~~~
{: .output}


R will return any values that are indicated by `TRUE` in your vector, and filter out any that 
are `FALSE`.


~~~
x[c(TRUE, FALSE)]
~~~
{: .r}



~~~
a a 
1 3 
~~~
{: .output}

Notice how R also recycled our logical vector to the correct length?


Since comparison operators evaluate to logical vectors, we can also
use them to succinctly subset vectors. When we do a logical comparison on a vector, R returns a 
logical vector as the result:

~~~
x > 7
~~~
{: .r}

~~~
    a     b     c     d     e 
FALSE FALSE  TRUE FALSE  TRUE 
~~~
{: .output}

We can nest our comparison inside of our subsetting operators to tell R to return a subset of 
our data which matches whatever criteria we specify.

~~~
x[x > 7]
~~~
{: .r}

~~~
  c   e 
7.1 7.5 
~~~
{: .output}



> ## Tip: Combining logical conditions
>
> There are many situations in which you will wish to combine multiple logical
> criteria. For example, we might want to find all the countries that are
> located in Asia **or** Europe **and** have life expectancies within a certain
> range. Several operations for combining logical vectors exist in R:
>
>  * `&`, the "logical AND" operator: returns `TRUE` if both the left and right
>    are `TRUE`.
>  * `|`, the "logical OR" operator: returns `TRUE`, if either the left or right
>    (or both) are `TRUE`.
>
> The recycling rule applies with both of these, so `TRUE & c(TRUE, FALSE, TRUE)`
> will compare the first `TRUE` on the left of the `&` sign with each of the
> three conditions on the right.
>
> You may sometimes see `&&` and `||` instead of `&` and `|`. These operators
> do not use the recycling rule: they only look at the first element of each
> vector and ignore the remaining elements. The longer operators are mainly used
> in programming, rather than data analysis.
>
>  * `!`, the "logical NOT" operator: converts `TRUE` to `FALSE` and `FALSE` to
>    `TRUE`. It can negate a single logical condition (eg `!TRUE` becomes
>    `FALSE`), or a whole vector of conditions(eg `!c(TRUE, FALSE)` becomes
>    `c(FALSE, TRUE)`).
>
> Additionally, you can compare the elements within a single vector using the
> `all` function (which returns `TRUE` if every element of the vector is `TRUE`)
> and the `any` function (which returns `TRUE` if one or more elements of the
> vector are `TRUE`).
{: .callout}

> ## Challenge 3
>
> Given the following code:
>
> 
> ~~~
> x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
> names(x) <- c('a', 'b', 'c', 'd', 'e')
> print(x)
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>   a   b   c   d   e 
> 5.4 6.2 7.1 4.8 7.5 
> ~~~
> {: .output}
>
> Write a subsetting command to return the values in x that are greater than 4 and less than 7.
>
> > ## Solution to challenge 3
> >
> > 
> > ~~~
> > x_subset <- x[x<7 & x>4]
> > print(x_subset)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >   a   b   d 
> > 5.4 6.2 4.8 
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}


> ## Challenge 4
>
> Using the gapminder data we loaded previously, fix each of the following common data frame subsetting errors:
>
> 1. Extract observations collected for the year 1957
>
>    
>    ~~~
>    gapminder[gapminder$year = 1957,]
>    ~~~
>    {: .r}
>
> 2. Extract all columns except 1 through to 4
>
>    
>    ~~~
>    gapminder[,-1:4]
>    ~~~
>    {: .r}
>
> 3. Extract the rows where the life expectancy is longer the 80 years
>
>    
>    ~~~
>    gapminder[gapminder$lifeExp > 80]
>    ~~~
>    {: .r}
>
> 4. Extract the first row, and the fourth and fifth columns
>   (`lifeExp` and `gdpPercap`).
>
>    
>    ~~~
>    gapminder[1, 4, 5]
>    ~~~
>    {: .r}
>
> 5. Advanced: extract rows that contain information for the years 2002
>    and 2007
>
>    
>    ~~~
>    gapminder[gapminder$year == 2002 | 2007,]
>    ~~~
>    {: .r}
>
> > ## Solution to challenge 4
> >
> > Fix each of the following common data frame subsetting errors:
> >
> > 1. Extract observations collected for the year 1957
> >
> >    
> >    ~~~
> >    # gapminder[gapminder$year = 1957,]
> >    gapminder[gapminder$year == 1957,]
> >    ~~~
> >    {: .r}
> >
> > 2. Extract all columns except 1 through to 4
> >
> >    
> >    ~~~
> >    # gapminder[,-1:4]
> >    gapminder[,-c(1:4)]
> >    ~~~
> >    {: .r}
> >
> > 3. Extract the rows where the life expectancy is longer the 80 years
> >
> >    
> >    ~~~
> >    # gapminder[gapminder$lifeExp > 80]
> >    gapminder[gapminder$lifeExp > 80,]
> >    ~~~
> >    {: .r}
> >
> > 4. Extract the first row, and the fourth and fifth columns
> >   (`lifeExp` and `gdpPercap`).
> >
> >    
> >    ~~~
> >    # gapminder[1, 4, 5]
> >    gapminder[1, c(4, 5)]
> >    ~~~
> >    {: .r}
> >
> > 5. Advanced: extract rows that contain information for the years 2002
> >    and 2007
> >
> >     
> >     ~~~
> >     # gapminder[gapminder$year == 2002 | 2007,]
> >     gapminder[gapminder$year == 2002 | gapminder$year == 2007,]
> >     gapminder[gapminder$year %in% c(2002, 2007),]
> >     ~~~
> >     {: .r}
> {: .solution}
{: .challenge}

> ## Challenge 5
>
> 1. Why does `gapminder[1:20]` return an error? How does it differ from `gapminder[1:20, ]`?
>
>
> 2. Create a new `data.frame` called `gapminder_small` that only contains rows 1 through 9
> and 19 through 23. There are many ways to accomplish this. Compare with your neighbor and see if they did it a different way than you.
>
> > ## Solution to challenge 5
> >
> > 1.  `gapminder` is a data.frame so needs to be subsetted on two dimensions. `gapminder[1:20, ]` subsets the data to give the first 20 rows and all columns.
> >
> > 2. There are several different ways to accomplish this task:
> > 
> > First, you can do it in two steps by subsetting all the rows 1 through 23, then removing rows 10 through 18:
> > 
> > ~~~
> > gapminder_small <- gapminder[1:23, ]
> > gapminder_small <- gapminder_small[-18:-10, ]
> > ~~~
> > {: .r}
> > 
> > Or, you can first subset rows 1 through 9, then use `rbind` to concatenate the next subset of rows 10 through 18:
> > 
> > ~~~
> > gapminder_small <- gapminder[1:9, ]
> > gapminder_small <- rbind(gapminder_small, gapminder[19:23, ]
> > ~~~
> > {: .r}
> >
> > Or you can do this in a single step by combining your ranges:
> >
> > ~~~
> > gapminder_small <- gapminder[c(1:9, 19:23), ]
> > ~~~
> >
> > There are probably other ways to accomplish this task. Did you come up with any that we didn't show here?
> >
> > {: .r}
> {: .solution}
{: .challenge}


