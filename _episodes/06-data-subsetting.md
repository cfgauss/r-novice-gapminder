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




R has many powerful subset operators and mastering them will allow you to
easily perform complex operations on any kind of dataset.

There are six different ways we can subset any kind of object, and three
different subsetting operators for the different data structures.

Let's start with the workhorse of R: atomic vectors.


~~~
x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
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

the `:` operator creates a sequence of numbers from the left element to the right.

~~~
1:4
~~~
{: .r}



~~~
[1] 1 2 3 4
~~~
{: .output}



~~~
c(1, 2, 3, 4)
~~~
{: .r}



~~~
[1] 1 2 3 4
~~~
{: .output}


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
> Come up with at least 3 different commands that will produce the following output:
>
> 
> ~~~
>   b   c   d 
> 6.2 7.1 4.8 
> ~~~
> {: .output}
>
> After you find 3 different commands, compare notes with your neighbour. Did you have different strategies?
>
> > ## Solution to challenge 1
> >
> > 
> > ~~~
> > x[2:4]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > ~~~
> > x[-c(1,5)]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > ~~~
> > x[c("b", "c", "d")]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
> > {: .output}
> > 
> > ~~~
> > x[c(2,3,4)]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >   b   c   d 
> > 6.2 7.1 4.8 
> > ~~~
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

Unfortunately we can't skip or remove elements so easily.

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
> x <- 1:3
> x
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
> names(x) <- c('a', 'a', 'a')
> x
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
> x['a']  # only returns first value
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
> x[which(names(x) == 'a')]  # returns all three values
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
c("a", "b", "c", "e")  # names of x
   |    |    |    |    # The elements == is comparing
c("a", "c")
~~~
{: .r}

When one vector is shorter than the other, it gets *recycled*:


~~~
c("a", "b", "c", "e")  # names of x
   |    |    |    |    # The elements == is comparing
c("a", "c", "a", "c")
~~~
{: .r}

In this case R simply repeats `c("a", "c")` twice. If the longer
vector length isn't a multiple of the shorter vector length, then
R will also print out a warning message:


~~~
names(x) == c('a', 'c', 'e')
~~~
{: .r}



~~~
[1]  TRUE FALSE FALSE
~~~
{: .output}

This difference between `==` and `%in%` is important to remember,
because it can introduce hard to find and subtle bugs!

## Subsetting through other logical operations

We can also more simply subset through logical operations:


~~~
x[c(TRUE, TRUE, FALSE, FALSE)]
~~~
{: .r}



~~~
a a 
1 2 
~~~
{: .output}

Note that in this case, the logical vector is also recycled to the
length of the vector we're subsetting!


~~~
x[c(TRUE, FALSE)]
~~~
{: .r}



~~~
a a 
1 3 
~~~
{: .output}

Since comparison operators evaluate to logical vectors, we can also
use them to succinctly subset vectors:


~~~
x[x > 7]
~~~
{: .r}



~~~
named integer(0)
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

## Handling special values

At some point you will encounter functions in R which cannot handle missing, infinite,
or undefined data.

There are a number of special functions you can use to filter out this data:

 * `is.na` will return all positions in a vector, matrix, or data.frame
   containing `NA`.
 * likewise, `is.nan`, and `is.infinite` will do the same for `NaN` and `Inf`.
 * `is.finite` will return all positions in a vector, matrix, or data.frame
   that do not contain `NA`, `NaN` or `Inf`.
 * `na.omit` will filter out all missing values from a vector

## Factor subsetting

Now that we've explored the different ways to subset vectors, how
do we subset the other data structures?

Factor subsetting works the same way as vector subsetting.


~~~
f <- factor(c("a", "a", "b", "c", "c", "d"))
f[f == "a"]
~~~
{: .r}



~~~
[1] a a
Levels: a b c d
~~~
{: .output}



~~~
f[f %in% c("b", "c")]
~~~
{: .r}



~~~
[1] b c c
Levels: a b c d
~~~
{: .output}



~~~
f[1:3]
~~~
{: .r}



~~~
[1] a a b
Levels: a b c d
~~~
{: .output}

An important note is that skipping elements will not remove the level
even if no more of that category exists in the factor:


~~~
f[-3]
~~~
{: .r}



~~~
[1] a a c c d
Levels: a b c d
~~~
{: .output}

## Data frames

Remember the data frames are lists underneath the hood, so similar rules
apply. However they are also two dimensional objects:

`[` with one argument will act the same was as for lists, where each list
element corresponds to a column. The resulting object will be a data frame:


~~~
head(gapminder[3])
~~~
{: .r}



~~~
       pop
1  8425333
2  9240934
3 10267083
4 11537966
5 13079460
6 14880372
~~~
{: .output}

Similarly, `[[` will act to extract *a single column*:


~~~
head(gapminder[["lifeExp"]])
~~~
{: .r}



~~~
[1] 28.801 30.332 31.997 34.020 36.088 38.438
~~~
{: .output}

And `$` provides a convenient shorthand to extract columns by name:


~~~
head(gapminder$year)
~~~
{: .r}



~~~
[1] 1952 1957 1962 1967 1972 1977
~~~
{: .output}

With two arguments, `[` behaves the same way as for matrices:


~~~
gapminder[1:3,]
~~~
{: .r}



~~~
      country year      pop continent lifeExp gdpPercap
1 Afghanistan 1952  8425333      Asia  28.801  779.4453
2 Afghanistan 1957  9240934      Asia  30.332  820.8530
3 Afghanistan 1962 10267083      Asia  31.997  853.1007
~~~
{: .output}

If we subset a single row, the result will be a data frame (because
the elements are mixed types):


~~~
gapminder[3,]
~~~
{: .r}



~~~
      country year      pop continent lifeExp gdpPercap
3 Afghanistan 1962 10267083      Asia  31.997  853.1007
~~~
{: .output}

But for a single column the result will be a vector (this can
be changed with the third argument, `drop = FALSE`).

> ## Challenge 7
>
> Fix each of the following common data frame subsetting errors:
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
> > ## Solution to challenge 7
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

> ## Challenge 8
>
> 1. Why does `gapminder[1:20]` return an error? How does it differ from `gapminder[1:20, ]`?
>
>
> 2. Create a new `data.frame` called `gapminder_small` that only contains rows 1 through 9
> and 19 through 23. You can do this in one or two steps.
>
> > ## Solution to challenge 8
> >
> > 1.  `gapminder` is a data.frame so needs to be subsetted on two dimensions. `gapminder[1:20, ]` subsets the data to give the first 20 rows and all columns.
> >
> > 2. 
> >
> > 
> > ~~~
> > gapminder_small <- gapminder[c(1:9, 19:23),]
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}


---
title: Vectorization
teaching: 10
exercises: 15
questions:
- "How can I operate on all the elements of a vector at once?"
objectives:
- "To understand vectorized operations in R."
keypoints:
- "Use vectorized operations instead of loops."
---



Most of R's functions are vectorized, meaning that the function will
operate on all elements of a vector without needing to loop through
and act on each element one at a time. This makes writing code more
concise, easy to read, and less error prone.



~~~
x <- 1:4
x * 2
~~~
{: .r}



~~~
[1] 2 4 6 8
~~~
{: .output}

The multiplication happened to each element of the vector.

We can also add two vectors together:


~~~
y <- 6:9
x + y
~~~
{: .r}



~~~
[1]  7  9 11 13
~~~
{: .output}

Each element of `x` was added to its corresponding element of `y`:


~~~
x:  1  2  3  4
    +  +  +  +
y:  6  7  8  9
---------------
    7  9 11 13
~~~
{: .r}


> ## Challenge 1
>
> Let's try this on the `pop` column of the `gapminder` dataset.
>
> Make a new column in the `gapminder` data frame that
> contains population in units of millions of people.
> Check the head or tail of the data frame to make sure
> it worked.
>
> > ## Solution to challenge 1
> >
> > Let's try this on the `pop` column of the `gapminder` dataset.
> >
> > Make a new column in the `gapminder` data frame that
> > contains population in units of millions of people.
> > Check the head or tail of the data frame to make sure
> > it worked.
> >
> > 
> > ~~~
> > gapminder$pop_millions <- gapminder$pop / 1e6
> > head(gapminder)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >       country year      pop continent lifeExp gdpPercap pop_millions
> > 1 Afghanistan 1952  8425333      Asia  28.801  779.4453     8.425333
> > 2 Afghanistan 1957  9240934      Asia  30.332  820.8530     9.240934
> > 3 Afghanistan 1962 10267083      Asia  31.997  853.1007    10.267083
> > 4 Afghanistan 1967 11537966      Asia  34.020  836.1971    11.537966
> > 5 Afghanistan 1972 13079460      Asia  36.088  739.9811    13.079460
> > 6 Afghanistan 1977 14880372      Asia  38.438  786.1134    14.880372
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}


> ## Challenge 2
>
> On a single graph, plot population, in
> millions, against year, for all countries. Don't worry about
>identifying which country is which.
>
> Repeat the exercise, graphing only for China, India, and
>Indonesia. Again, don't worry about which is which.
>
> > ## Solution to challenge 2
> >
> > Refresh your plotting skills by plotting population in millions against year.
> >
> > 
> > ~~~
> > ggplot(gapminder, aes(x = year, y = pop_millions)) +
> >  geom_point()
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-09-ch2-sol-1.png" title="plot of chunk ch2-sol" alt="plot of chunk ch2-sol" style="display: block; margin: auto;" />
> > 
> > ~~~
> > countryset <- c("China","India","Indonesia")
> > ggplot(gapminder[gapminder$country %in% countryset,],
> >        aes(x = year, y = pop_millions)) +
> >   geom_point()
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-09-ch2-sol-2.png" title="plot of chunk ch2-sol" alt="plot of chunk ch2-sol" style="display: block; margin: auto;" />
> {: .solution}
{: .challenge}


Comparison operators, logical operators, and many functions are also
vectorized:


**Comparison operators**


~~~
x > 2
~~~
{: .r}



~~~
[1] FALSE FALSE  TRUE  TRUE
~~~
{: .output}

**Logical operators**

~~~
a <- x > 3  # or, for clarity, a <- (x > 3)
a
~~~
{: .r}



~~~
[1] FALSE FALSE FALSE  TRUE
~~~
{: .output}

> ## Tip: some useful functions for logical vectors
>
> `any()` will return `TRUE` if *any* element of a vector is `TRUE`
> `all()` will return `TRUE` if *all* elements of a vector are `TRUE`
{: .callout}

Most functions also operate element-wise on vectors:

**Functions**

~~~
x <- 1:4
log(x)
~~~
{: .r}



~~~
[1] 0.0000000 0.6931472 1.0986123 1.3862944
~~~
{: .output}

Vectorized operations work element-wise on matrices:


~~~
m <- matrix(1:12, nrow=3, ncol=4)
m * -1
~~~
{: .r}



~~~
     [,1] [,2] [,3] [,4]
[1,]   -1   -4   -7  -10
[2,]   -2   -5   -8  -11
[3,]   -3   -6   -9  -12
~~~
{: .output}


> ## Tip: element-wise vs. matrix multiplication
>
> Very important: the operator `*` gives you element-wise multiplication!
> To do matrix multiplication, we need to use the `%*%` operator:
>
> 
> ~~~
> m %*% matrix(1, nrow=4, ncol=1)
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>      [,1]
> [1,]   22
> [2,]   26
> [3,]   30
> ~~~
> {: .output}
> 
> 
> 
> ~~~
> matrix(1:4, nrow=1) %*% matrix(1:4, ncol=1)
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>      [,1]
> [1,]   30
> ~~~
> {: .output}
>
> For more on matrix algebra, see the [Quick-R reference
> guide](http://www.statmethods.net/advstats/matrix.html)
{: .callout}


> ## Challenge 3
>
> Given the following matrix:
>
> 
> ~~~
> m <- matrix(1:12, nrow=3, ncol=4)
> m
> ~~~
> {: .r}
> 
> 
> 
> ~~~
>      [,1] [,2] [,3] [,4]
> [1,]    1    4    7   10
> [2,]    2    5    8   11
> [3,]    3    6    9   12
> ~~~
> {: .output}
>
> Write down what you think will happen when you run:
>
> 1. `m ^ -1`
> 2. `m * c(1, 0, -1)`
> 3. `m > c(0, 20)`
> 4. `m * c(1, 0, -1, 2)`
>
> Did you get the output you expected? If not, ask a helper!
>
> > ## Solution to challenge 3
> >
> > Given the following matrix:
> >
> > 
> > ~~~
> > m <- matrix(1:12, nrow=3, ncol=4)
> > m
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >      [,1] [,2] [,3] [,4]
> > [1,]    1    4    7   10
> > [2,]    2    5    8   11
> > [3,]    3    6    9   12
> > ~~~
> > {: .output}
> >
> >
> > Write down what you think will happen when you run:
> >
> > 1. `m ^ -1`
> >
> > 
> > ~~~
> >           [,1]      [,2]      [,3]       [,4]
> > [1,] 1.0000000 0.2500000 0.1428571 0.10000000
> > [2,] 0.5000000 0.2000000 0.1250000 0.09090909
> > [3,] 0.3333333 0.1666667 0.1111111 0.08333333
> > ~~~
> > {: .output}
> >
> > 2. `m * c(1, 0, -1)`
> >
> > 
> > ~~~
> >      [,1] [,2] [,3] [,4]
> > [1,]    1    4    7   10
> > [2,]    0    0    0    0
> > [3,]   -3   -6   -9  -12
> > ~~~
> > {: .output}
> >
> > 3. `m > c(0, 20)`
> >
> > 
> > ~~~
> >       [,1]  [,2]  [,3]  [,4]
> > [1,]  TRUE FALSE  TRUE FALSE
> > [2,] FALSE  TRUE FALSE  TRUE
> > [3,]  TRUE FALSE  TRUE FALSE
> > ~~~
> > {: .output}
> >
> {: .solution}
{: .challenge}


> ## Challenge 4
>
> We're interested in looking at the sum of the
> following sequence of fractions:
>
> 
> ~~~
>  x = 1/(1^2) + 1/(2^2) + 1/(3^2) + ... + 1/(n^2)
> ~~~
> {: .r}
>
> This would be tedious to type out, and impossible for high values of
> n.  Use vectorisation to compute x when n=100. What is the sum when
> n=10,000?
>
> > ##  Challenge 4
> >
> > We're interested in looking at the sum of the
> > following sequence of fractions:
> >
> > 
> > ~~~
> >  x = 1/(1^2) + 1/(2^2) + 1/(3^2) + ... + 1/(n^2)
> > ~~~
> > {: .r}
> >
> > This would be tedious to type out, and impossible for
> > high values of n.
> > Can you use vectorisation to compute x, when n=100?
> > How about when n=10,000?
> >
> > 
> > ~~~
> > sum(1/(1:100)^2)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.634984
> > ~~~
> > {: .output}
> > 
> > 
> > 
> > ~~~
> > sum(1/(1:1e04)^2)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.644834
> > ~~~
> > {: .output}
> > 
> > 
> > 
> > ~~~
> > n <- 10000
> > sum(1/(1:n)^2)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.644834
> > ~~~
> > {: .output}
> >
> > We can also obtain the same results using a function:
> > 
> > ~~~
> > inverse_sum_of_squares <- function(n) {
> >   sum(1/(1:n)^2)
> > }
> > inverse_sum_of_squares(100)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.634984
> > ~~~
> > {: .output}
> > 
> > 
> > 
> > ~~~
> > inverse_sum_of_squares(10000)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.644834
> > ~~~
> > {: .output}
> > 
> > 
> > 
> > ~~~
> > n <- 10000
> > inverse_sum_of_squares(n)
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] 1.644834
> > ~~~
> > {: .output}
> >
> {: .solution}
{: .challenge}

