### "Introduction to R and RStudio"
teaching: 30
exercises: 15

 - 

## Motivation

Science is a multi-step process: once you've designed an experiment and collected
data, the real fun begins! This lesson will teach you how to start this process using
R and RStudio. We will begin with raw data, perform exploratory analyses, and learn
how to plot results graphically. This example starts with a dataset from
[gapminder.org](https://www.gapminder.org) containing population information for many
countries through time. Can you read the data into R? Can you plot the population for
Senegal? Can you calculate the average income for countries on continent of Asia?
By the end of these lessons you will be able to do things like plot the populations
for all of these countries in under a minute!

## Before Starting The Workshop

Please ensure you have the latest version of R and RStudio installed on your machine.
This is important, as some packages used in the workshop may not install correctly 
(or at all) if R is not up to date.

[Download and install the latest version of R here](https://www.r-project.org/)

[Download and install RStudio here](https://www.rstudio.com/)

## Introduction to RStudio

Why R?
Why RStudio?

**Basic layout**

three panels:

  * The interactive R console (entire left)
  * Environment/History (tabbed in upper right)
  * Files/Plots/Packages/Help/Viewer (tabbed in lower right)

Editor panel when you open scripts

## Work flow within RStudio

There are two main ways one can work within RStudio.

1. Test and play within the interactive R console then copy code into
a .R file to run later.
2. Start writing in an .R file and use RStudio's command / short cut
to push current line, selected lines or modified lines to the
interactive R console.

Run button and key shortcuts
 - ctrl-enter windows/linux
 - command-enter mac
 
Project managment 

Mostly use the console
 - run code and test commands

">" cursor - similar to the shell
 - type commands
 - R executes
 - returns result
 
The simplest thing you could do with R is do arithmetic:


~~~
1 + 100
~~~
{: .r}

Ignore the [1] for now.

Incomplete commands:

~~~
> 1 +
~~~
{: .r}

Can cancel with the "Esc" key, or "Ctrl+C" in command line - can use for running code too

order of operations

~~~
3 + 5 * 2
~~~
{: .r}

Use parentheses to force order:

~~~
(3 + 5) * 2
~~~
{: .r}

Use these to make code easier to read

~~~
(3 + (5 * (2 ^ 2))) # hard to read
3 + 5 * 2 ^ 2       # clear, if you remember the rules
3 + 5 * (2 ^ 2)     # if you forget some rules, this might help
~~~
{: .r}

"#" indicate comments

Scientific notation

~~~
2/10000
~~~
{: .r}

~~~
5e3  # Note the lack of minus here
~~~
{: .r}


## Mathematical functions

functions use name then parenthesis

~~~
sin(1)  # trigonometry functions
~~~
{: .r}


~~~
log(1)  # natural logarithm
~~~
{: .r}



~~~
log10(10) # base-10 logarithm
~~~
{: .r}

~~~
exp(0.5) # e^(1/2)
~~~
{: .r}

Can look up functions in google or use Autocomplete (tab)

*** HERE ***

## Comparing things

~~~
1 == 1  # equality (note two equals signs, read as "is equal to")
~~~
{: .r}


~~~
1 != 2  # inequality (read as "is not equal to")
~~~
{: .r}


~~~
1 <  2  # less than
~~~
{: .r}


~~~
1 <= 1  # less than or equal to
~~~
{: .r}



~~~
1 > 0  # greater than
~~~
{: .r}


~~~
1 >= -9 # greater than or equal to
~~~
{: .r}


float point error, use all.equal instead of '==' for non-integers

## Variables and assignment

use assignment arrow to save values to variables

~~~
x <- 1/40
~~~
{: .r}

No output

~~~
x
~~~
{: .r}


stored as a decimal approximation called floating point number.

point out x in environment variables

~~~
log(x)
~~~
{: .r}

Can reassign values

~~~
x <- 100
~~~
{: .r}

Can reference the variable in the assignment

~~~
x <- x + 1 #notice how RStudio updates its description of x on the top right tab
~~~
{: .r}

The right hand side of the assignment can be any valid R expression.
The right hand side is *fully evaluated* before the assignment occurs.


character values:

~~~
y <- "green"
~~~
{: .r}

Variable names rules:
can contain letters, numbers, underscores and periods
cannot start with a number nor contain spaces at all.

Naming conventions:
  * periods.between.words
  * underscores\_between_words
  * camelCaseToSeparateWords

consistency is important


can use `=` operator for assignment:

~~~
z = 1/40
~~~
{: .r}

Less common, and sometimes it is confusing to use '=' instead of '<-'
remember consistency!

## Functions

built in functions
coding your own
supplemental lesson

## R Packages

* install packages: `install.packages("packagename")`
* make a package available for use: `library(packagename)`

~~~
install.packages("gapminder")
~~~
{: .r}

text scrolling for install

~~~
library(gapminder)
~~~
{: .r}

Point out how to install via the Packages tab.

Other useful commands:

* You can see what packages are installed by typing
  `installed.packages()`
* You can update installed packages by typing `update.packages()`
* You can remove a package with `remove.packages("packagename")`

**CHALLENGES** (allot 15 min)

---
title: "Seeking Help"
teaching: 10
exercises: 10
---

## Reading Help files

~~~
help(function_name)
?function_name
~~~
{: .r}

Each help page is broken down into sections:

 - Description: An extended description of what the function does.
 - Usage: The arguments of the function and their default values.
 - Arguments: An explanation of the data each argument is expecting.
 - Details: Any important details to be aware of.
 - Value: The data the function returns.
 - See Also: Any related functions you might find useful.
 - Examples: Some examples for how to use the function.

Some may have different sections, but these are the main ones.

Help files make it easier to use R because you don;'t have to remember the usage of every function.

## Special Operators

To seek help on special operators, use quotes:

~~~
?"+"
~~~
{: .r}

## Getting help on packages

Many packages come with "vignettes": tutorials and extended example documentation.
Without any arguments

`vignette()` will list all vignettes for all installed packages;

`vignette(package="package-name")` will list all available vignettes for `package-name`

 and `vignette("vignette-name")` will open the specified vignette.

If a package doesn't have any vignettes, you can usually find help by typing
`help("package-name")`.

## When you kind of remember the function

fuzzy search:

~~~
??function_name
~~~
{: .r}

## When you have no idea where to begin

CRAN Task View - show website: http://cran.at.r-project.org/web/views

## When your code doesn't work: seeking help from your peers

Stack Overflow -  search using the `[r]` tag.


**CHALLENGES** - allot 10 min

---
title: "Data Structures"
teaching: 15
exercises: 10
---

## Data Types in R

Review operators:

~~~
x + z
~~~
{: .r}

Try adding two different types of data:

~~~
x + y
~~~
{: .r}

Gives error because 101 + "green" is nonsense.

5 main data types: `double`, `integer`, `complex`, `logical`, and `character`.


~~~
typeof(3.14)
~~~
{: .r}

A `double`, also referred to as a *floating point number*, is how R stores numeric values 
by default.


~~~
typeof(1L)
~~~
{: .r}

To use an `integer` value in R, we use the L to tell R that this value is an integer value. 
Without the L, R would store this value as a `double`.


~~~
typeof(1+1i)
~~~
{: .r}


R can also support `complex` values as well. Unless you are doing mathematical analyses or 
complicated transformations, chances are you will not encounter this data type very often.

~~~
typeof(TRUE)
~~~
{: .r}



~~~
[1] "logical"
~~~
{: .output}


`Logical` data types are particularly helpful in subsetting data frames and other types of data manipulation. We will explore this concept more later.

~~~
typeof('banana')
~~~
{: .r}

~~~
[1] "character"
~~~
{: .output}

Lastly, R stores strings as the `character` type.

No matter how complicated our analyses become, all data in R is interpreted as one of these
basic data types.

## Vectors

Remember the [1]?
R never uses just a single value, but instead uses vectors. Output before was a vector of 
length 1.

As seen in the challenges, we can build vectors using the `c` function.

~~~
x <- c(2, 4, 6, 8, 10, 12, 14, 16)
x
~~~
{: .r}

**colon operator** quickly creates sequential vectors:

~~~
y <- 1:8
y
~~~
{: .r}

can specify whatever start and stop point we want

~~~
-4:7
~~~
{: .r}

~~~
[1] -4 -3 -2 -1  0  1  2  3  4  5  6  7
~~~
{: .output}

R is **vectorized**
operations on the entire vector - returns a vector

~~~
y + 10
~~~
{: .r}

~~~
[1] 11 12 13 14 15 16 17 18
~~~
{: .output}



~~~
x * 2
~~~
{: .r}

~~~
[1]  4  8 12 16 20 24 28 32
~~~
{: .output}



~~~
x + y
~~~
{: .r}

~~~
[1]  3  6  9 12 15 18 21 24
~~~
{: .output}

when operating on two or more vectors, R performs the operation element by element:


~~~
x:  2  4  6  8 10 12 14 16
    +  +  +  +  +  +  +  +
y:  1  2  3  4  5  6  7  8
--------------------------
    3  6  9 12 15 18 21 24
~~~
{: .r}


**CHALLENGEs** - allot 10 minutes

Vectors can be made up of any of the basic data types.

Character Vectors:

~~
a <- c("one", "two", "three", "four")
a
~~~
{: .r}


similar to `typeof`, `str` will tell us the data type.

also will give us a compact view of some basic information about our object.

~~~
str(a)
~~~
{: .r}


*chr* that this is a *character* vector
numbers in the brackets indicates the dimensions of our vector. 
then a list the first few elements 

Logical Vectors:

~~~
b <- c(TRUE, TRUE, FALSE, TRUE)
b
~~~
{: .r}

*** CHALLENGES ***

we can use `c` to add elements to an existing vector

~~~
c(x, 20, 25)
~~~
{: .r}

Changes won't be saved until we use the assignment arrow

modify `y` to contain all numbers to 20 by adding on to the existing vector

~~~
y <- c(y, 9:20)
y
~~~
{: .r}

This is a nested operation, from Order of Opers. earlier the sequence inside the parenthesis is created first, then added to `y`

`length` can quickly return the length of a vector.

~~~
length(y)
~~~
{: .r}


Other data structures, **lists** and **matrices**
use `?list()`, `?matrix()` or supplemental lesson to learn about them.

primarily **data frames** today, continued after break:

---
layout: break
title: "Coffee Break"
break: 15
---
---
title: Subsetting Data
teaching: 30
exercises: 15
---

*** HERE ***

R's power comes from it's vectorization. 
many powerful subset operators that will allow you to
easily perform complex operations on any kind of dataset without the resource depletion of loops.

Let's start with a data structure we've seen before, the workhorse of R: atomic vectors.


~~~
x <- c(5.4, 6.2, 7.1, 4.8, 7.5)
~~~
{: .r}

can name elements within our vectors using the `names` function.

~~~
names(x) <- c('a', 'b', 'c', 'd', 'e')
x
~~~
{: .r}

how do we get to individual contents?

## Accessing elements using their indices

we can give their corresponding index, starting from one:

~~~
x[1]
~~~
{: .r}



~~~
x[4]
~~~
{: .r}


the square brackets operator is a function
For atomic vectors (and matrices), it means "get me the nth element".

We can ask for multiple elements at once:

~~~
x[c(1, 3)]
~~~
{: .r}


Or slices of the vector:


~~~
x[1:4]
~~~
{: .r}


the `:` operator lets us select a range of elements


We can ask for the same element multiple times:

~~~
x[c(1,1,3)]
~~~
{: .r}


a number outside of the vector, R will return missing values


~~~
x[6]
~~~
{: .r}


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

R starts indices with 1 instead of 0 like other programming languages such as C and python

## Skipping and removing elements

use a negative number to return every element *except* for the one specified:


~~~
x[-2]
~~~
{: .r}


We can skip multiple elements:


~~~
x[c(-1, -5)]  # or x[-c(1,5)]
~~~
{: .r}

Combining positive and negative indices will return an error.

To make the subset permanent we need to assign the value.

~~~
x <- x[-4]
x
~~~
{: .r}



*** CHALLENGES *** - allot 5 minutes

## Subsetting by name

can extract elements by using their name

~~~
x[c("a", "c")]
~~~
{: .r}

more reliable since positions can change. But we cannot as easily skip or remove by name.

To skip (or remove) a single named element:


~~~
x[-which(names(x) == "a")]
~~~
{: .r}


The `which` function returns the indices of all `TRUE` elements of its argument.
Step by step analysis of command:

~~~
names(x) == "a"
~~~
{: .r}


The condition operator is applied to every name of the vector `x`. Only the
first name is "a" so that element is TRUE.

`which` then converts this to an index:


~~~
which(names(x) == "a")
~~~
{: .r}


Only the first element is `TRUE`, so `which` returns 1. 

the '-' makes this index negative and removes the element

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

***CHALLENGES*** - allot 5 min



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

***CHALLENGES*** allot 10 min

---
title: "Exploring Data Frames"
teaching: 35
---

## Data Frames

So far we have covered data structures which contain all the same basic data type. But 
one of R's most powerful features is its ability to deal with tabular data -
like what you might already have in a spreadsheet or a CSV. **Data Frames** are built from 
vectors but differ from matrices in the aspect that they can contain vectors of different 
data types.

build a data frame from existing vectors - `data.frame()` command

~~~
coat <- c("calico", "black", "tabby")
weight <- c(2.1, 5.0, 3.2)
likes_string <- c(1,0,1)

cats <- data.frame(coat, weight, likes_string)
cats
~~~
{: .r}

can pull out columns by specifying them using the `$` operator


~~~
cats$weight
~~~
{: .r}



~~~
cats$coat
~~~
{: .r}


can perform operations on columns within our data frame, just like with vectors


~~~
## Say we discovered that the scale weighs two Kg light:
cats$weight + 2
~~~
{: .r}



~~~
paste("My cat is", cats$coat)
~~~
{: .r}

*** CHALLENGES*** allot 5 min

add an additional column for age using `c`

~~~
age <- c(2,3,5,12)
cats
~~~
{: .r}


We can then add this as a column in our data frame by using the `cbind()` function:


~~~
cats <- cbind(cats, age)
~~~
{: .r}

Error - there are more elements in age but only 3 rows in cats.

~~~
age <- c(4,5,8)
cats <- cbind(cats, age)
cats
~~~
{: .r}

add a row, rows are lists since they contain different types of elements:

~~~
newRow <- list("tortoiseshell", 3.3, TRUE, 9)
cats <- rbind(cats, newRow)
~~~
{: .r}


Our list had the correct number of elements, so why did R give us a warning?

~~~
class(cats$coat)
~~~
{: .r}



Factors are data classes that R uses to handle categorical data. categories are called **levels**
Anything new that doesn't fit into one of its categories is rejected as nonsense and 
is replaced by an `NA` until we explicitly add that as a *level* in the factor:


~~~
levels(cats$coat)
~~~
{: .r}



~~~
levels(cats$coat) <- c(levels(cats$coat), 'tortoiseshell')
cats <- rbind(cats, list("tortoiseshell", 3.3, TRUE, 9))
~~~
{: .r}

can also change the column to character to prevent this

~~~
str(cats)
~~~
{: .r}


~~~
cats$coat <- as.character(cats$coat)
str(cats)
~~~
{: .r}


We can now add rows and columns, but we've accidentally added a garbage row:


~~~
cats
~~~
{: .r}



~~~
           coat weight likes_string age
1        calico    2.1            1   4
2         black    5.0            0   5
3         tabby    3.2            1   8
4          <NA>    3.3            1   9
5 tortoiseshell    3.3            1   9
~~~
{: .output}

We can ask for a data.frame minus this offending row:


~~~
cats[-4,]
~~~
{: .r}


Notice the comma with nothing after it to indicate we want to drop the entire fourth row.

using `na.omit` allows us to drop all rows with `NA` values:


~~~
na.omit(cats)
~~~
{: .r}


Let's reassign the output to `cats`, so that our changes will be permanent:


~~~
cats <- na.omit(cats)
~~~
{: .r}

remember that *columns are vectors or factors, and rows are lists.* 

We can also glue two dataframes together with `rbind`:


~~~
cats <- rbind(cats, cats)
cats
~~~
{: .r}

But now the row names are unnecessarily complicated. We can remove the rownames,
and R will automatically re-name them sequentially:


~~~
rownames(cats) <- NULL
cats
~~~
{: .r}

*** CHALLENGES *** - allot 5 min

So far, you've seen the basics of manipulating data.frames with our cat data;
now, let's use those skills to digest a more realistic dataset. For the remainder of our 
lesson, we are going to use the `gapminder` data set built into the `gapminder` package.

If you did not install the `gapminder` package with our previous challenge, you can do so 
now with the `install.packages()` command:

~~~
install.packages("gapminder")
~~~
{: .r}

If you have already installed the `gapminder` package, go ahead and load it now. You can tell 
R to load the package by clicking the checkbox next to its listing in the package tab of the 
lower left pane in R studio. Or you can load it by using the 'library()' command:

~~~
library('gapminder')
~~~
{: .r}

To make sure our analysis is reproducible, we should put the code
into a script file so we can come back to it later.

Note that the library command can be used within your scripts to load any packages that your 
scripts need. To make your scripts easy to read by others, you will want to put these commands 
at the top of your script file. You can learn more about writing easy to read code in the 
supplemental lesson [Writing Good Software](https://carriebrown.github.io/r-novice-gapminder-2/07-wrap-up/).


Let's investigate gapminder a bit; the first thing we should always do is check
out what the data looks like with `str`:


~~~
str(gapminder)
~~~
{: .r}



~~~
Classes ‘tbl_df’, ‘tbl’ and 'data.frame':	1704 obs. of  6 variables:
 $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
 $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
 $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
 $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
 $ gdpPercap: num  779 821 853 836 740 ...
~~~
{: .output}

We can also examine individual columns of the data.frame with our `typeof` function:


~~~
typeof(gapminder$year)
~~~
{: .r}



~~~
[1] "integer"
~~~
{: .output}



~~~
typeof(gapminder$lifeExp)
~~~
{: .r}



~~~
[1] "double"
~~~
{: .output}



~~~
typeof(gapminder$country)
~~~
{: .r}



~~~
[1] "integer"
~~~
{: .output}



~~~
str(gapminder$country)
~~~
{: .r}



~~~
 Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
~~~
{: .output}

We can also interrogate the data.frame for information about its dimensions;
remembering that `str(gapminder)` said there were 1704 observations of 6
variables in gapminder, what do you think the following will produce, and why?


~~~
length(gapminder)
~~~
{: .r}



~~~
[1] 6
~~~
{: .output}

A fair guess would have been to say that the length of a data.frame would be the
number of rows it has (1704), but this is not the case; remember, a data.frame
is a *list of vectors and factors*:


~~~
typeof(gapminder)
~~~
{: .r}



~~~
[1] "list"
~~~
{: .output}

When `length` gave us 6, it's because gapminder is built out of a list of 6
columns. To get the number of rows and columns in our dataset, try:


~~~
nrow(gapminder)
~~~
{: .r}



~~~
[1] 1704
~~~
{: .output}



~~~
ncol(gapminder)
~~~
{: .r}



~~~
[1] 6
~~~
{: .output}

Or, both at once:


~~~
dim(gapminder)
~~~
{: .r}



~~~
[1] 1704    6
~~~
{: .output}

We'll also likely want to know what the titles of all the columns are, so we can
ask for them later:


~~~
colnames(gapminder)
~~~
{: .r}



~~~
[1] "country"   "year"      "pop"       "continent" "lifeExp"   "gdpPercap"
~~~
{: .output}

At this stage, it's important to ask ourselves if the structure R is reporting
matches our intuition or expectations; do the basic data types reported for each
column make sense? If not, we need to sort any problems out now before they turn
into bad surprises down the road, using what we've learned about how R
interprets data, and the importance of *strict consistency* in how we record our
data.

Once we're happy that the data types and structures seem reasonable, it's time
to start digging into our data proper. Check out the first few lines:


~~~
head(gapminder)
~~~
{: .r}



~~~
      country continent year lifeExp      pop gdpPercap
1 Afghanistan      Asia 1952  28.801  8425333  779.4453
2 Afghanistan      Asia 1957  30.332  9240934  820.8530
3 Afghanistan      Asia 1962  31.997 10267083  853.1007
4 Afghanistan      Asia 1967  34.020 11537966  836.1971
5 Afghanistan      Asia 1972  36.088 13079460  739.9811
6 Afghanistan      Asia 1977  38.438 14880372  786.1134
~~~
{: .output}


> ## Challenge 3
>
> Read the output of `str(gapminder)` again;
> this time, use what you've learned about factors, lists and vectors,
> as well as the output of functions like `colnames` and `dim`
> to explain what everything that `str` prints out for gapminder means.
> If there are any parts you can't interpret, discuss with your neighbors!
>
> > ## Solution to Challenge 3
> >
> > The object `gapminder` is a data frame with 1704 entries and 6 columns:
> > - `country` and `continent` are factors. The `country` factor has 142 levels and the `continent` factor has 5 levels
> > - `year` is an integer vector.
> > - `pop`, `lifeExp`, and `gdpPercap` are numeric vectors.
> >
> {: .solution}
{: .challenge}

### Subsetting Data Frames

Remember the data frames are lists underneath the hood, so similar rules
apply. However they are also two dimensional objects:

`[` with one argument will act the same was as for lists, where each list
element corresponds to a column. The resulting object will be a list:


~~~
head(gapminder[5])
~~~
{: .r}



~~~
# A tibble: 6 × 1
       pop
     <int>
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

With two arguments, `[` subsets on typical matrix format, where the first argument indicates 
rows and the second argument indicates columns. Note that if one of the arguments is blank, R will 
default to include all of the rows or columns:


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


> ## Challenge 4
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
> and 19 through 23. You can do this in one or two steps.
>
> > ## Solution to challenge 5
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
layout: break
title: "Lunch"
break: 60
---
---
title: Control Flow
teaching: 20
exercises: 15
questions:
- "How can I make data-dependent choices in R?"
- "How can I repeat operations in R?"
objectives:
- "Write conditional statements with `if()` and `else()`."
- "Write and understand `for()` loops."
keypoints:
- "Use `if` and `else` to make choices."
- "Use `for` to repeat operations."
---



Often when we're coding we want to control the flow of our actions. This can be done
by setting actions to occur only if a condition or a set of conditions are met.
Alternatively, we can also set an action to occur a particular number of times.

There are several ways you can control flow in R.
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

Let's set a seed so that we all generate the same 'pseudo-random'
number, and then print more information:


~~~
set.seed(10)
x <- rpois(1, lambda=8)

if (x >= 10) {
  print("x is greater than or equal to 10")
} else if (x > 5) {
  print("x is greater than 5")
} else {
  print("x is less than 5")
}
~~~
{: .r}



~~~
[1] "x is greater than 5"
~~~
{: .output}

> ## Tip: pseudo-random numbers
>
> In the above case, the function `rpois()` generates a random number following a
> Poisson distribution with a mean (i.e. lambda) of 8. The function `set.seed()`
> guarantees that all machines will generate the exact same 'pseudo-random'
> number ([more about pseudo-random numbers](http://en.wikibooks.org/wiki/R_Programming/Random_Number_Generation)).
> So if we `set.seed(10)`, we see that `x` takes the value 8. You should get the
> exact same number.
{: .callout}

**Important:** when R evaluates the condition inside `if()` statements, it is
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
> Use an `if()` statement to print a suitable message
> reporting whether there are any records from 2002 in
> the `gapminder` dataset.
> Now do the same for 2012.
>
> > ## Solution to Challenge 1
> > We will first see a solution to Challenge 1 which does not use the `any()` function.
> > We first obtain a logical vector describing which element of `gapminder$year` is equal to `2002`:
> > 
> > ~~~
> > gapminder[(gapminder$year == 2002),]
> > ~~~
> > {: .r}
> > Then, we count the number of rows of the data.frame `gapminder` that correspond to the 2002:
> > 
> > ~~~
> > rows2002_number <- nrow(gapminder[(gapminder$year == 2002),])
> > ~~~
> > {: .r}
> > The presence of any record for the year 2002 is equivalent to the request that `rows2002_number` is one or more:
> > 
> > ~~~
> > rows2002_number >= 1
> > ~~~
> > {: .r}
> > Putting all together, we obtain:
> > 
> > ~~~
> > if(nrow(gapminder[(gapminder$year == 2002),]) >= 1){
> >    print("Record(s) for the year 2002 found.")
> > }
> > ~~~
> > {: .r}
> >
> > All this can be done more quickly with `any()`. The logical condition can be expressed as:
> > 
> > ~~~
> > if(any(gapminder$year == 2002)){
> >    print("Record(s) for the year 2002 found.")
> > }
> > ~~~
> > {: .r}
> >
> {: .solution}
{: .challenge}


Did anyone get a warning message like this?


~~~
Warning in if (gapminder$year == 2012) {: the condition has length > 1 and
only the first element will be used
~~~
{: .error}

If your condition evaluates to a vector with more than one logical element,
the function `if()` will still run, but will only evaluate the condition in the first
element. Here you need to make sure your condition is of length 1.

> ## Tip: `any()` and `all()`
>
> The `any()` function will return TRUE if at least one
> TRUE value is found within a vector, otherwise it will return `FALSE`.
> This can be used in a similar way to the `%in%` operator.
> The function `all()`, as the name suggests, will only return `TRUE` if all values in
> the vector are `TRUE`.
{: .callout}

## Repeating operations

If you want to iterate over
a set of values, when the order of iteration is important, and perform the
same operation on each, a `for()` loop will do the job.
We saw `for()` loops in the shell lessons earlier. This is the most
flexible of looping operations, but therefore also the hardest to use
correctly. Avoid using `for()` loops unless the order of iteration is important:
i.e. the calculation at each iteration depends on the results of previous iterations.

The basic structure of a `for()` loop is:


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

We can use a `for()` loop nested within another `for()` loop to iterate over two things at
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
output_vector <- c()
for(i in 1:5){
  for(j in c('a', 'b', 'c', 'd', 'e')){
    temp_output <- paste(i, j)
    output_vector <- c(output_vector, temp_output)
  }
}
output_vector
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

> ## Tip: While loops
>
>
> Sometimes you will find yourself needing to repeat an operation until a certain
> condition is met. You can do this with a `while()` loop.
>
> 
> ~~~
> while(this condition is true){
>   do a thing
> }
> ~~~
> {: .r}
>
> As an example, here's a while loop
> that generates random numbers from a uniform distribution (the `runif()` function)
> between 0 and 1 until it gets one that's less than 0.1.
>
> ~~~
> z <- 1
> while(z > 0.1){
>   z <- runif(1)
>   print(z)
> }
> ~~~
> {: .r}
>
> `while()` loops will not always be appropriate. You have to be particularly careful
> that you don't end up in an infinite loop because your condition is never met.
{: .callout}


> ## Challenge 2
>
> Compare the objects output_vector and
> output_vector2. Are they the same? If not, why not?
> How would you change the last block of code to make output_vector2
> the same as output_vector?
>
> > ## Solution to Challenge 2
> > We can check whether the two vectors are identical using the `all()` function:
> > 
> > ~~~
> > all(output_vector == output_vector2)
> > ~~~
> > {: .r}
> > However, all the elements of `output_vector` can be found in `output_vector2`:
> > 
> > ~~~
> > all(output_vector %in% output_vector2)
> > ~~~
> > {: .r}
> > and vice versa:
> > 
> > ~~~
> > all(output_vector2 %in% output_vector)
> > ~~~
> > {: .r}
> > therefore, the element in `output_vector` and `output_vector2` are just sorted in a different order.
> > This is because `as.vector()` outputs the elements of an input matrix going over its column.
> > Taking a look at `output_matrix`, we can notice that we want its elements by rows.
> > The solution is to transpose the `output_matrix`. We can do it either by calling the transpose function
> > `t()` or by inputing the elements in the right order.
> > The first solution requires to change the original
> > 
> > ~~~
> > output_vector2 <- as.vector(output_matrix)
> > ~~~
> > {: .r}
> > into
> > 
> > ~~~
> > output_vector2 <- as.vector(t(output_matrix))
> > ~~~
> > {: .r}
> > The second solution requires to change
> > 
> > ~~~
> > output_matrix[i, j] <- temp_output
> > ~~~
> > {: .r}
> > into
> > 
> > ~~~
> > output_matrix[j, i] <- temp_output
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}

> ## Challenge 3
>
> Write a script that loops through the `gapminder` data by continent and prints out
> whether the mean life expectancy is smaller or larger than 50
> years.
>
> > ## Solution to Challenge 3
> >
> > **Step 1**:  We want to make sure we can extract all the unique values of the continent vector
> > 
> > ~~~
> > gapminder <- read.csv("data/gapminder-FiveYearData.csv")
> > unique(gapminder$continent)
> > ~~~
> > {: .r}
> >
> > **Step 2**: We also need to loop over each of these continents and calculate the average life expectancy for each `subset` of data.
> > We can do that as follows:
> >
> > 1. Loop over each of the unique values of 'continent'
> > 2. For each value of continent, create a temporary variable storing the life exepectancy for that subset,
> > 3. Return the calculated life expectancy to the user by printing the output:
> >
> > 
> > ~~~
> > for( iContinent in unique(gapminder$continent) ){
> >    tmp <- mean(subset(gapminder, continent==iContinent)$lifeExp)
> >    cat("Average Life Expectancy in", iContinent, "is", tmp, "\n")
> >    rm(tmp)
> > }
> > ~~~
> > {: .r}
> >
> > **Step 3**: The exercise only wants the output printed if the average life expectancy is less than 50 or greater than 50. So we need to add an `if` condition before printing.
> > So we need to add an `if` condition before printing, which evaluates whether the calculated average life expectancy is above or below a threshold, and print an output conditional on the result.
> > We need to amend (3) from above:
> >
> > 3a. If the calculated life expectancy is less than some threshold (50 years), return the continent and a statement that life expectancy is less than threshold, otherwise return the continent and   a statement that life expectancy is greater than threshold,:
> >
> > 
> > ~~~
> > thresholdValue <- 50
> > > >
> > for( iContinent in unique(gapminder$continent) ){
> >    tmp <- mean(subset(gapminder, continent==iContinent)$lifeExp)
> >    
> >    if(tmp < thresholdValue){
> >        cat("Average Life Expectancy in", iContinent, "is less than", thresholdValue, "\n")
> >    }
> >    else{
> >        cat("Average Life Expectancy in", iContinent, "is greater than", thresholdValue, "\n")
> >         } # end if else condition
> >    rm(tmp)
> >    } # end for loop
> > > >
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}

> ## Challenge 4
>
> Modify the script from Challenge 4 to loop over each
> country. This time print out whether the life expectancy is
> smaller than 50, between 50 and 70, or greater than 70.
>
> > ## Solution to Challenge 4
> >  We modify our solution to Challenge 3 by now adding two thresholds, `lowerThreshold` and `upperThreshold` and extending our if-else statements:
> >
> > 
> > ~~~
> >  lowerThreshold <- 50
> >  upperThreshold <- 70
> >  
> > for( iCountry in unique(gapminder$country) ){
> >     tmp <- mean(subset(gapminder, country==iCountry)$lifeExp)
> >     
> >     if(tmp < lowerThreshold){
> >         cat("Average Life Expectancy in", iCountry, "is less than", lowerThreshold, "\n")
> >     }
> >     else if(tmp > lowerThreshold && tmp < upperThreshold){
> >         cat("Average Life Expectancy in", iCountry, "is between", lowerThreshold, "and", upperThreshold, "\n")
> >     }
> >     else{
> >         cat("Average Life Expectancy in", iCountry, "is greater than", upperThreshold, "\n")
> >     }
> >     rm(tmp)
> > }
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}
---
title: Dataframe Manipulation with dplyr
teaching: 40
exercises: 15
questions:
- "How can I manipulate dataframes without repeating myself?"
objectives:
- "To be able to use the six main dataframe manipulation 'verbs' with pipes in  `dplyr`."
keypoints:
- "Use the `dplyr` package to manipulate dataframes."
- "Use `select()` to choose variables from a dataframe."
- "Use `filter()` to choose data based on values."
- "Use `group_by()` and `summarize()` to work with subsets of data."
- "Use `mutate()` to create new variables."
---



Manipulation of dataframes means many things to many researchers, we often
select certain observations (rows) or variables (columns), we often group the
data by a certain variable(s), or we even calculate summary statistics. We can
do these operations using the normal base R operations:


~~~
mean(gapminder[gapminder$continent == "Africa", "gdpPercap"])
~~~
{: .r}



~~~
[1] 2193.755
~~~
{: .output}



~~~
mean(gapminder[gapminder$continent == "Americas", "gdpPercap"])
~~~
{: .r}



~~~
[1] 7136.11
~~~
{: .output}



~~~
mean(gapminder[gapminder$continent == "Asia", "gdpPercap"])
~~~
{: .r}



~~~
[1] 7902.15
~~~
{: .output}

But this isn't very *nice* because there is a fair bit of repetition. Repeating
yourself will cost you time, both now and later, and potentially introduce some
nasty bugs.

## The `dplyr` package

Luckily, the [`dplyr`](https://cran.r-project.org/web/packages/dplyr/dplyr.pdf)
package provides a number of very useful functions for manipulating dataframes
in a way that will reduce the above repetition, reduce the probability of making
errors, and probably even save you some typing. As an added bonus, you might
even find the `dplyr` grammar easier to read.

Here we're going to cover 6 of the most commonly used functions as well as using
pipes (`%>%`) to combine them.

1. `select()`
2. `filter()`
3. `group_by()`
4. `summarize()`
5. `mutate()`

If you have have not installed this package earlier, please do so:


~~~
install.packages('dplyr')
~~~
{: .r}

Now let's load the package:


~~~
library(dplyr)
~~~
{: .r}

## Using select()

If, for example, we wanted to move forward with only a few of the variables in
our dataframe we could use the `select()` function. This will keep only the
variables you select.


~~~
year_country_gdp <- select(gapminder,year,country,gdpPercap)
~~~
{: .r}

![](../fig/13-dplyr-fig1.png)

If we open up `year_country_gdp` we'll see that it only contains the year,
country and gdpPercap. Above we used 'normal' grammar, but the strengths of
`dplyr` lie in combining several functions using pipes. Since the pipes grammar
is unlike anything we've seen in R before, let's repeat what we've done above
using pipes.


~~~
year_country_gdp <- gapminder %>% select(year,country,gdpPercap)
~~~
{: .r}

To help you understand why we wrote that in that way, let's walk through it step
by step. First we summon the gapminder dataframe and pass it on, using the pipe
symbol `%>%`, to the next step, which is the `select()` function. In this case
we don't specify which data object we use in the `select()` function since in
gets that from the previous pipe. **Fun Fact**: There is a good chance you have
encountered pipes before in the shell. In R, a pipe symbol is `%>%` while in the
shell it is `|` but the concept is the same!

## Using filter()

If we now wanted to move forward with the above, but only with European
countries, we can combine `select` and `filter`


~~~
year_country_gdp_euro <- gapminder %>%
    filter(continent=="Europe") %>%
    select(year,country,gdpPercap)
~~~
{: .r}

> ## Challenge 1
>
> Write a single command (which can span multiple lines and includes pipes) that
> will produce a dataframe that has the African values for `lifeExp`, `country`
> and `year`, but not for other Continents.  How many rows does your dataframe
> have and why?
>
> > ## Solution to Challenge 1
> >
> >~~~
> >year_country_lifeExp_Africa <- gapminder %>%
> >                            filter(continent=="Africa") %>%
> >                            select(year,country,lifeExp)
> >~~~
> >{: .r}
> {: .solution}
{: .challenge}

As with last time, first we pass the gapminder dataframe to the `filter()`
function, then we pass the filtered version of the gapminder dataframe to the
`select()` function. **Note:** The order of operations is very important in this
case. If we used 'select' first, filter would not be able to find the variable
continent since we would have removed it in the previous step.

## Using group_by() and summarize()

Now, we were supposed to be reducing the error prone repetitiveness of what can
be done with base R, but up to now we haven't done that since we would have to
repeat the above for each continent. Instead of `filter()`, which will only pass
observations that meet your criteria (in the above: `continent=="Europe"`), we
can use `group_by()`, which will essentially use every unique criteria that you
could have used in filter.


~~~
str(gapminder)
~~~
{: .r}



~~~
'data.frame':	1704 obs. of  6 variables:
 $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
 $ pop      : num  8425333 9240934 10267083 11537966 13079460 ...
 $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
 $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
 $ gdpPercap: num  779 821 853 836 740 ...
~~~
{: .output}



~~~
str(gapminder %>% group_by(continent))
~~~
{: .r}



~~~
Classes 'grouped_df', 'tbl_df', 'tbl' and 'data.frame':	1704 obs. of  6 variables:
 $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
 $ pop      : num  8425333 9240934 10267083 11537966 13079460 ...
 $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
 $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
 $ gdpPercap: num  779 821 853 836 740 ...
 - attr(*, "vars")=List of 1
  ..$ : symbol continent
 - attr(*, "drop")= logi TRUE
 - attr(*, "indices")=List of 5
  ..$ : int  24 25 26 27 28 29 30 31 32 33 ...
  ..$ : int  48 49 50 51 52 53 54 55 56 57 ...
  ..$ : int  0 1 2 3 4 5 6 7 8 9 ...
  ..$ : int  12 13 14 15 16 17 18 19 20 21 ...
  ..$ : int  60 61 62 63 64 65 66 67 68 69 ...
 - attr(*, "group_sizes")= int  624 300 396 360 24
 - attr(*, "biggest_group_size")= int 624
 - attr(*, "labels")='data.frame':	5 obs. of  1 variable:
  ..$ continent: Factor w/ 5 levels "Africa","Americas",..: 1 2 3 4 5
  ..- attr(*, "vars")=List of 1
  .. ..$ : symbol continent
  ..- attr(*, "drop")= logi TRUE
~~~
{: .output}
You will notice that the structure of the dataframe where we used `group_by()`
(`grouped_df`) is not the same as the original `gapminder` (`data.frame`). A
`grouped_df` can be thought of as a `list` where each item in the `list`is a
`data.frame` which contains only the rows that correspond to the a particular
value `continent` (at least in the example above).

![](../fig/13-dplyr-fig2.png)

## Using summarize()

The above was a bit on the uneventful side because `group_by()` much more
exciting in conjunction with `summarize()`. This will allow use to create new
variable(s) by using functions that repeat for each of the continent-specific
data frames. That is to say, using the `group_by()` function, we split our
original dataframe into multiple pieces, then we can run functions
(e.g. `mean()` or `sd()`) within `summarize()`.


~~~
gdp_bycontinents <- gapminder %>%
    group_by(continent) %>%
    summarize(mean_gdpPercap=mean(gdpPercap))
~~~
{: .r}

![](../fig/13-dplyr-fig3.png)

That allowed us to calculate the mean gdpPercap for each continent, but it gets
even better.

> ## Challenge 2
>
>
> Calculate the average life expectancy per country. Which had the longest life
> expectancy and which had the shortest life expectancy?
>
> > ## Solution to Challenge 2
> >
> >~~~
> >lifeExp_bycountry <- gapminder %>%
> >    group_by(country) %>%
> >    summarize(mean_lifeExp=mean(lifeExp))
> >~~~
> >{: .r}
> {: .solution}
{: .challenge}

The function `group_by()` allows us to group by multiple variables. Let's group by `year` and `continent`.



~~~
gdp_bycontinents_byyear <- gapminder %>%
    group_by(continent,year) %>%
    summarize(mean_gdpPercap=mean(gdpPercap))
~~~
{: .r}

That is already quite powerful, but it gets even better! You're not limited to defining 1 new variable in `summarize()`.


~~~
gdp_pop_bycontinents_byyear <- gapminder %>%
    group_by(continent,year) %>%
    summarize(mean_gdpPercap=mean(gdpPercap),
              sd_gdpPercap=sd(gdpPercap),
              mean_pop=mean(pop),
              sd_pop=sd(pop))
~~~
{: .r}

## Using mutate()

We can also create new variables prior to (or even after) summarizing information using `mutate()`.


~~~
gdp_pop_bycontinents_byyear <- gapminder %>%
    mutate(gdp_billion=gdpPercap*pop/10^9) %>%
    group_by(continent,year) %>%
    summarize(mean_gdpPercap=mean(gdpPercap),
              sd_gdpPercap=sd(gdpPercap),
              mean_pop=mean(pop),
              sd_pop=sd(pop),
              mean_gdp_billion=mean(gdp_billion),
              sd_gdp_billion=sd(gdp_billion))
~~~
{: .r}



> ## Advanced Challenge
>
> Calculate the average life expectancy in 2002 of 2 randomly selected countries
> for each continent. Then arrange the continent names in reverse order.
> **Hint:** Use the `dplyr` functions `arrange()` and `sample_n()`, they have
> similar syntax to other dplyr functions.
>
> > ## Solution to Advanced Challenge
> >
> >~~~
> >lifeExp_2countries_bycontinents <- gapminder %>%
> >    filter(year==2002) %>%
> >    group_by(continent) %>%
> >    sample_n(2) %>%
> >    summarize(mean_lifeExp=mean(lifeExp)) %>%
> >    arrange(desc(mean_lifeExp))
> >~~~
> >{: .r}
> {: .solution}
{: .challenge}

## Other great resources

* [Data Wrangling Cheat sheet](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf)
* [Introduction to dplyr](https://cran.rstudio.com/web/packages/dplyr/vignettes/introduction.html)
* [Data wrangling with R and RStudio](https://www.rstudio.com/resources/webinars/data-wrangling-with-r-and-rstudio/)
---
layout: break
title: "Coffee Break"
break: 15
---
---
title: Creating Publication-Quality Graphics
teaching: 50
exercises: 25
questions:
- "How can I create publication-quality graphics in R?"
objectives:
- "To be able to use ggplot2 to generate publication quality graphics."
- "To understand the basic grammar of graphics, including the aesthetics and geometry layers, adding statistics, transforming scales, and coloring or panelling by groups."
keypoints:
- "Use `ggplot2` to create plots."
- "Think about graphics in layers: aesthetics, geometry, statistics, scale transformation, and grouping."
---



Plotting our data is one of the best ways to
quickly explore it and the various relationships
between variables.

There are three main plotting systems in R,
the [base plotting system][base], the [lattice][lattice]
package, and the [ggplot2][ggplot2] package.

[base]: http://www.statmethods.net/graphs/
[lattice]: http://www.statmethods.net/advgraphs/trellis.html
[ggplot2]: http://www.statmethods.net/advgraphs/ggplot2.html

Today we'll be learning about the ggplot2 package, because
it is the most effective for creating publication quality
graphics.

ggplot2 is built on the grammar of graphics (where the gg comes from), the idea that any plot can be
expressed from the same set of components: a **data** set, a
**coordinate system**, and a set of **geoms**--the visual representation of data
points.

The key to understanding ggplot2 is thinking about a figure in layers.
This idea may be familiar to you if you have used image editing programs like Photoshop, Illustrator, or
Inkscape.

Let's start off with an example. The first thing we need to do is load the `ggplot2` package, just
like we did with the previous ones:


~~~
library("ggplot2")
~~~
{: .r}

In order to begin graphing, we use the `ggplot` function. This function lets R
know that we're creating a new plot, and any of the arguments we give the
`ggplot` function are the *global* options for the plot: they apply to all
layers on the plot.

~~~
library("ggplot2")
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-vs-gdpPercap-scatter-1.png" title="plot of chunk lifeExp-vs-gdpPercap-scatter" alt="plot of chunk lifeExp-vs-gdpPercap-scatter" style="display: block; margin: auto;" />

We've passed in two arguments to `ggplot`. First, we tell `ggplot` what data we
want to show on our figure, in this example the gapminder data we read in
earlier. For the second argument we passed in the `aes` function, which
tells `ggplot` how variables in the **data** map to *aesthetic* properties of
the figure, in this case the **x** and **y** locations. Here we told `ggplot` we
want to plot the "gdpPercap" column of the gapminder data frame on the x-axis, and
the "lifeExp" column on the y-axis. Notice that we didn't need to explicitly
pass `aes` these columns (e.g. `x = gapminder[, "gdpPercap"]`), this is because
`ggplot` is smart enough to know to look in the **data** for that column!

Other options that can be set with the `aes` function include color, size, transparency and shape. We will talk more about that later.

By itself, the call to `ggplot` isn't enough to draw a figure:

~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp))
~~~
{: .r}

<img src="../fig/rmd-08-unnamed-chunk-2-1.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" style="display: block; margin: auto;" />

We need to tell `ggplot` how we want to visually represent the data, which we
do by adding a new **geom** layer. In our example, we used `geom_point`, which
tells `ggplot` we want to visually represent the relationship between **x** and
**y** as a scatterplot of points:


~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-vs-gdpPercap-scatter2-1.png" title="plot of chunk lifeExp-vs-gdpPercap-scatter2" alt="plot of chunk lifeExp-vs-gdpPercap-scatter2" style="display: block; margin: auto;" />

> ## Challenge 1
>
> Our example visualizes how the GDP per capita changes in relationship to life expectancy:
> 
> ~~~
> ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) + geom_point()
> ~~~
> {: .r}
>
> Modify this example so that the plot visualizes how life expectancy has
> changed over time:
>
> Hint: the gapminder dataset has a column called "year", which should appear
> on the x-axis.
>
> > ## Solution to challenge 1
> >
> > Modify the example so that the figure visualise how life expectancy has
> > changed over time:
> >
> > 
> > ~~~
> > ggplot(data = gapminder, aes(x = year, y = lifeExp)) + geom_point()
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-08-ch1-sol-1.png" title="plot of chunk ch1-sol" alt="plot of chunk ch1-sol" style="display: block; margin: auto;" />
> >
> {: .solution}
{: .challenge}

>
> ## Challenge 2
>
> In the previous examples and challenge we've used the `aes` function to tell
> the scatterplot **geom** about the **x** and **y** locations of each point.
> Another *aesthetic* property we can modify is the point *color*. Modify the
> code from the previous challenge to **color** the points by the "continent"
> column. What trends do you see in the data? Are they what you expected?
>
> > ## Solution to challenge 2
> >
> > In the previous examples and challenge we've used the `aes` function to tell
> > the scatterplot **geom** about the **x** and **y** locations of each point.
> > Another *aesthetic* property we can modify is the point *color*. Modify the
> > code from the previous challenge to **color** the points by the "continent"
> > column. What trends do you see in the data? Are they what you expected?
> >
> > 
> > ~~~
> > ggplot(data = gapminder, aes(x = year, y = lifeExp, color=continent)) +
> >   geom_point()
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-08-ch2-sol-1.png" title="plot of chunk ch2-sol" alt="plot of chunk ch2-sol" style="display: block; margin: auto;" />
> >
> {: .solution}
{: .challenge}


## Layers

Using a scatterplot probably isn't the best for visualizing change over time.
Instead, let's tell `ggplot` to visualize the data as a line plot:


~~~
ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country, color=continent)) +
  geom_line()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-line-1.png" title="plot of chunk lifeExp-line" alt="plot of chunk lifeExp-line" style="display: block; margin: auto;" />

Instead of adding a `geom_point` layer, we've added a `geom_line` layer. We've
added the **by** *aesthetic*, which tells `ggplot` to draw a line for each
country.

But what if we want to visualize both lines and points on the plot? We can
simply add another layer to the plot:


~~~
ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country, color=continent)) +
  geom_line() + geom_point()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-line-point-1.png" title="plot of chunk lifeExp-line-point" alt="plot of chunk lifeExp-line-point" style="display: block; margin: auto;" />

It's important to note that each layer is drawn on top of the previous layer. In
this example, the points have been drawn *on top of* the lines. Here's a
demonstration:


~~~
ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country)) +
  geom_line(aes(color=continent)) + geom_point()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-layer-example-1-1.png" title="plot of chunk lifeExp-layer-example-1" alt="plot of chunk lifeExp-layer-example-1" style="display: block; margin: auto;" />

In this example, the *aesthetic* mapping of **color** has been moved from the
global plot options in `ggplot` to the `geom_line` layer so it no longer applies
to the points. Now we can clearly see that the points are drawn on top of the
lines.

> ## Tip: Setting an aesthetic to a value instead of a mapping
>
> So far, we've seen how to use an aesthetic (such as **color**) as a *mapping* to a variable in the data. For example, when we use `geom_line(aes(color=continent))`, ggplot will give a different color to each continent. But what if we want to change the colour of all lines to blue? You may think that `geom_line(aes(color="blue"))` should work, but it doesn't. Since we don't want to create a mapping to a specific variable, we simply move the color specification outside of the `aes()` function, like this: `geom_line(color="blue")`.
{: .callout}

> ## Challenge 3
>
> Switch the order of the point and line layers from the previous example. What
> happened?
>
> > ## Solution to challenge 3
> >
> > Switch the order of the point and line layers from the previous example. What
> > happened?
> >
> > 
> > ~~~
> > ggplot(data = gapminder, aes(x=year, y=lifeExp, by=country)) +
> >  geom_point() + geom_line(aes(color=continent))
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-08-ch3-sol-1.png" title="plot of chunk ch3-sol" alt="plot of chunk ch3-sol" style="display: block; margin: auto;" />
> >
> > The lines now get drawn over the points!
> >
> {: .solution}
{: .challenge}

## Transformations and statistics

`ggplot` also makes it easy to overlay statistical models over the data. To
demonstrate we'll go back to our first example:


~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point()
~~~
{: .r}

<img src="../fig/rmd-08-lifeExp-vs-gdpPercap-scatter3-1.png" title="plot of chunk lifeExp-vs-gdpPercap-scatter3" alt="plot of chunk lifeExp-vs-gdpPercap-scatter3" style="display: block; margin: auto;" />

Currently it's hard to see the relationship between the points due to some strong
outliers in GDP per capita. We can change the scale of units on the x axis using
the *scale* functions. These control the mapping between the data values and
visual values of an aesthetic. We can also modify the transparency of the
points, using the *alpha* function, which is especially helpful when you have
a large amount of data which is very clustered.


~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point(alpha = 0.5) + scale_x_log10()
~~~
{: .r}

<img src="../fig/rmd-08-axis-scale-1.png" title="plot of chunk axis-scale" alt="plot of chunk axis-scale" style="display: block; margin: auto;" />

The `log10` function applied a transformation to the values of the gdpPercap
column before rendering them on the plot, so that each multiple of 10 now only
corresponds to an increase in 1 on the transformed scale, e.g. a GDP per capita
of 1,000 is now 3 on the y axis, a value of 10,000 corresponds to 4 on the y
axis and so on. This makes it easier to visualize the spread of data on the
x-axis.

> ## Tip Reminder: Setting an aesthetic to a value instead of a mapping
>
> Notice that we used `geom_point(alpha = 0.5)`. As the previous tip mentioned, using a setting outside of the `aes()` function will cause this value to be used for all points, which is what we want in this case. But just like any other aesthetic setting, *alpha* can also be mapped to a variable in the data. For example, we can give a different transparency to each continent with `geom_point(aes(alpha = continent))`.
{: .callout}

We can fit a simple relationship to the data by adding another layer,
`geom_smooth`:


~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point() + scale_x_log10() + geom_smooth(method="lm")
~~~
{: .r}

<img src="../fig/rmd-08-lm-fit-1.png" title="plot of chunk lm-fit" alt="plot of chunk lm-fit" style="display: block; margin: auto;" />

We can make the line thicker by *setting* the **size** aesthetic in the
`geom_smooth` layer:


~~~
ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
  geom_point() + scale_x_log10() + geom_smooth(method="lm", size=1.5)
~~~
{: .r}

<img src="../fig/rmd-08-lm-fit2-1.png" title="plot of chunk lm-fit2" alt="plot of chunk lm-fit2" style="display: block; margin: auto;" />

There are two ways an *aesthetic* can be specified. Here we *set* the **size**
aesthetic by passing it as an argument to `geom_smooth`. Previously in the
lesson we've used the `aes` function to define a *mapping* between data
variables and their visual representation.

> ## Challenge 4a
>
> Modify the color and size of the points on the point layer in the previous
> example.
>
> Hint: do not use the `aes` function.
>
> > ## Solution to challenge 4a
> >
> > Modify the color and size of the points on the point layer in the previous
> > example.
> >
> > Hint: Do not use the `aes` function.
> >
> > 
> > ~~~
> > ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp)) +
> >  geom_point(size=3, color="orange") + scale_x_log10() +
> >  geom_smooth(method="lm", size=1.5)
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-08-ch4a-sol-1.png" title="plot of chunk ch4a-sol" alt="plot of chunk ch4a-sol" style="display: block; margin: auto;" />
> {: .solution}
{: .challenge}


> ## Challenge 4b
>
> Modify your solution to Challenge 4a so that the
> points are now a different shape and are colored by continent with new
> trendlines.
>
> Hint: The color argument can be used inside the aesthetic.
>
> > ## Solution to challenge 4b
> >
> > Modify Challenge 4 so that the points are now a different shape and are
> > colored by continent with new trendlines.
> >
> > Hint: The color argument can be used inside the aesthetic.
> >
> >
> >~~~
> > ggplot(data = gapminder, aes(x = gdpPercap, y = lifeExp, color = continent)) +
> > geom_point(size=3, pch=17) + scale_x_log10() +
> > geom_smooth(method="lm", size=1.5)
> >~~~
> >{: .r}
> >
> ><img src="../fig/rmd-08-ch4b-sol-1.png" title="plot of chunk ch4b-sol" alt="plot of chunk ch4b-sol" style="display: block; margin: auto;" />
> {: .solution}
{: .challenge}


## Multi-panel figures

Earlier we visualized the change in life expectancy over time across all
countries in one plot. Alternatively, we can split this out over multiple panels
by adding a layer of **facet** panels. Focusing only on those countries with
names that start with the letter "A" or "Z".

We start by subsetting the data.  We use the `substr` function to
pull out a part of a character string; in this case, the letters that occur
in positions `start` through `stop`, inclusive, of the `gapminder$country`
vector.



~~~
starts.with <- substr(gapminder$country, start = 1, stop = 1)
az.countries <- gapminder[starts.with == "A" | starts.with == "Z", ]
ggplot(data = az.countries, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country)
~~~
{: .r}

<img src="../fig/rmd-08-facet-1.png" title="plot of chunk facet" alt="plot of chunk facet" style="display: block; margin: auto;" />

> ## Tip
> 
> Instead of using multiple subsetting conditions (in this case, `starts.with == "A" | starts.with == "Z"`)
> we can use the operator `%in%` which selects any entries which match a list of conditions. Here we would use 
> `%in%` by using this command instead of the one we used before:
> 
> ~~~
> az.countries <- gapminder[starts.with %in% c("A", "Z"), ]
> ~~~
> {: .r}
{: .callout}


The `facet_wrap` layer takes a "formula" as its argument, denoted by the tilde
(~). This tells R to draw a panel for each unique value in the country column
of the gapminder dataset.


## Modifying text

To clean this figure up for a publication we need to change some of the text
elements. 

First, let's rename our `x` and `y` axes to neater and more informative labels. We can do that using the `xlab()` and `ylab()` functions:

~~~
ggplot(data = az.countries, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country) +
  xlab("Year") + ylab("Life Expectancy")
~~~
{: .r}

<img src="../fig/rmd-08-theme-1a.png" title="plot of chunk theme" alt="plot of chunk theme" style="display: block; margin: auto;" />
 
Let's give our figure a title with the `ggtitle()` function. And while we're at it, let's capitalize the label of our
legend. This can be done using the **scales** layer.

~~~
ggplot(data = az.countries, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country) +
  xlab("Year") + ylab("Life Expectancy") + 
  ggtitle("Figure 1") + scale_colour_discrete(name="Continent")
~~~
{: .r}

<img src="../fig/rmd-08-theme-1b.png" title="plot of chunk theme" alt="plot of chunk theme" style="display: block; margin: auto;" />

 
Lastly, let's remove the x-axis labels so the plot is less cluttered. To do this, we use the **theme** layer which controls
the axis text and overall text size.

~~~
ggplot(data = az.countries, aes(x = year, y = lifeExp, color=continent)) +
  geom_line() + facet_wrap( ~ country) +
  xlab("Year") + ylab("Life Expectancy") + 
  ggtitle("Figure 1") + scale_colour_discrete(name="Continent") +
  theme(axis.text.x=element_blank(), axis.ticks.x=element_blank())
~~~
{: .r}

<img src="../fig/rmd-08-theme-1.png" title="plot of chunk theme" alt="plot of chunk theme" style="display: block; margin: auto;" />

> ## Tip:
>
> The line breaks in our commands do not need to be in specific locations. They can be made wherever
> necessary to keep your code neat and make it easier to read. Some people place them to keep the lines roughly
> and equal length, while others put a single option on each line. The benefit of this approach is that you can
> use in line comments to remind you what each option does. Whichever approach you use, remember to keep the
> `+` at the end of the line so R knows that your command continues on the next line.

This is a taste of what you can do with `ggplot2`. RStudio provides a
really useful [cheat sheet][cheat] of the different layers available, and more
extensive documentation is available on the [ggplot2 website][ggplot-doc].
Finally, if you have no idea how to change something, a quick Google search will
usually send you to a relevant question and answer on Stack Overflow with reusable
code to modify!

[cheat]: http://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf
[ggplot-doc]: http://docs.ggplot2.org/current/


> ## Challenge 5
>
> Create a density plot of GDP per capita, filled by continent.
>
> Advanced:
>  - Transform the x axis to better visualise the data spread.
>  - Add a facet layer to panel the density plots by year.
>
> > ## Solution to challenge 5
> >
> > Create a density plot of GDP per capita, filled by continent.
> >
> > Advanced:
> >  - Transform the x axis to better visualise the data spread.
> >  - Add a facet layer to panel the density plots by year.
> >
> > 
> > ~~~
> > ggplot(data = gapminder, aes(x = gdpPercap, fill=continent)) +
> >  geom_density(alpha=0.6) + facet_wrap( ~ year) + scale_x_log10()
> > ~~~
> > {: .r}
> > 
> > <img src="../fig/rmd-08-ch5-sol-1.png" title="plot of chunk ch5-sol" alt="plot of chunk ch5-sol" style="display: block; margin: auto;" />
> {: .solution}
{: .challenge}
---
title: Writing Data
teaching: 10
exercises: 15
questions:
- "How can I save plots and data created in R?"
objectives:
- "To be able to write out plots and data from R."
keypoints:
- "Save plots from RStudio using the 'Export' button."
- "Use `write.table` to save tabular data."
---




## Saving plots

So making publication quality plots is great but does us little good if we cannot get them out of
R and into our documents.

You can save a plot from within RStudio using the 'Export' button
in the 'Plot' window. This will give you the option of saving as a
.pdf or as .png, .jpg or other image formats.

<img src="../fig/12-data-fig1.png" title="export plots in rstudio" alt="export plots in rstudio" style="display: block; margin: auto;" />

But what if you are working in a command line environment, or want to create multiple plots without user interaction?
In `ggplot2` you can use the `ggsave` function to save your plots quickly. This function can be used to save the last displayed plot in a format specified by the file name.
You can save as several different formats, such as a PDF:

~~~
ggsave("My_most_recent_plot.pdf")
~~~
{: .r}

Or as a JPG:

~~~
ggsave("My_most_recent_plot.jpg")
~~~
{: .r}

`ggsave` also allows you to specify size and quality of the image. You can check out all of the 
options using the `?ggsave` command to view the help file.

Sometimes you will want to save plots without creating them in the
'Plot' window first. Perhaps you want to make a pdf document with
multiple pages: each one a different plot, for example. Or perhaps
you're looping through multiple subsets of a file, plotting data from
each subset, and you want to save each plot, but obviously can't stop
the loop to click 'Export' for each one.

In this case you can use a more flexible approach. The function
`pdf` creates a new pdf device. You can control the size and resolution
using the arguments to this function.


~~~
pdf("Life_Exp_vs_time.pdf", width=12, height=4)
ggplot(data=gapminder, aes(x=year, y=lifeExp, color=continent)) +
  geom_point()

dev.off()
~~~
{: .r}

The `pdf` command opens the pdf file, and any output between this command and the `dev.off()` command 
will be added to that file. Forgetting to "close" your pdf device by using the `dev.off()` command can
lead to an incorrect file, so be sure to include it immediately after your output.

Open up this document and have a look.

> ## Challenge 1
>
> Rewrite your 'pdf' command to print a second
> page in the pdf, showing a facet plot
> of the same data with one panel per continent.
>
> Hint: Remember that we used the `facet_wrap` command previously to create a facet plot.
>
> > ## Solution to challenge 1
> > 
> > You can output a second plot, by adding a second `ggplot` command with the `facet_wrap` command before
> > `dev.off` command.
> >
> > ~~~
> > pdf("Life_Exp_vs_time2.pdf", width=12, height=4)
> > ggplot(data=gapminder, aes(x=year, y=lifeExp)) +
> >   geom_point()
> > ggplot(data=gapminder, aes(x=year, y=lifeExp)) +
> >   geom_point() + facet_wrap(~ continent)
> > 
> > # don't forget to close your pdf device!
> > dev.off()
> > ~~~
> > {: .r}
> > 
> > Did you see the line which started with a `#`? The `#` character tells R that this line
> > is a **comment** and not to execute the line.
> > Using comments in your script is a great way to remind your future self of what the commands in your code are doing.
> > It also makes your code easier for someone else to read and understand.
> > For more information on good code writing practices, check out the supplemental lesson
> > [Writing Good Software](https://carriebrown.github.io/r-novice-gapminder-2/07-wrap-up/)
> {: .solution}
{: .challenge}

The commands `jpeg`, `png` etc. are used similarly to produce
documents in different formats.

## Writing data

At some point, you'll also want to write out data from R.

We can use the `write.table` function for this, which is
very similar to the `read.table` function that we mentioned previously in Lesson 2. 
For more information on reading in your own data in R and the `read.table` function, check out the
supplemental lesson [Reading and Writing CSV Files](https://carriebrown.github.io/r-novice-gapminder-2/11-supp-read-write-csv/).

Let's create a data-cleaning script, for this analysis, we
only want to focus on the gapminder data for Australia:


~~~
aust_subset <- gapminder[gapminder$country == "Australia",]

write.table(aust_subset,
  file="gapminder-aus.csv",
  sep=","
)
~~~
{: .r}

Remember in our last lesson when we discussed line breaks and the different approaches for neat and tidy code.
Here, the line breaks have been placed between the different parameters of our command to make the code easier to read.
One benefit to this approach is that we can then comment each line to remind ourselves what they do. Here's our previous
example with these **in line comments**

~~~
aust_subset <- gapminder[gapminder$country == "Australia",]

write.table(aust_subset,		# Gapminder data for countries located in Australia
  file="gapminder-aus.csv", 	# Name of the output file
  sep=","						# Comma separated
)
~~~
{: .r}

This approach becomes really beneficial when you start writing commands which use a lot of parameters.

Now, we can use the shell commands we used yesterday to inspect our data. Go ahead and open a shell
window and navigate to the location of the file using your `cd` command. If you don't know where R is saving
your files, you can check the `file` pane or use the `getwd()` command.

Once you have navigated to the file
location type this in to check out the output file:

~~~
head gapminder-aus.csv
~~~
{: .r}

Note: If you did not attend yesterday's lesson, or have forgotten the shell commands, you can view
the file in R by clicking on the filename in the `file` pane and selecting `View File`.


~~~
"country","year","pop","continent","lifeExp","gdpPercap"
"61","Australia",1952,8691212,"Oceania",69.12,10039.59564
"62","Australia",1957,9712569,"Oceania",70.33,10949.64959
"63","Australia",1962,10794968,"Oceania",70.93,12217.22686
"64","Australia",1967,11872264,"Oceania",71.1,14526.12465
"65","Australia",1972,13177000,"Oceania",71.93,16788.62948
"66","Australia",1977,14074100,"Oceania",73.49,18334.19751
"67","Australia",1982,15184200,"Oceania",74.74,19477.00928
"68","Australia",1987,16257249,"Oceania",76.32,21888.88903
"69","Australia",1992,17481977,"Oceania",77.56,23424.76683
~~~
{: .output}

Hmm, that's not quite what we wanted. Where did all these
quotation marks come from? Also the row numbers are
meaningless.

Let's look at the help file to work out how to change this
behaviour.


~~~
?write.table
~~~
{: .r}

By default R will wrap character vectors with quotation marks
when writing out to file. It will also write out the row and
column names.

Let's fix this:


~~~
write.table(aust_subset,		# Gapminder data for countries located in Australia
  file="gapminder-aus.csv",		# Name of the output file
  sep=",",						# Comma separated
  quote=FALSE,					# Turn off quotation marks
  row.names=FALSE				# No row names
)
~~~
{: .r}

Now lets look at the data again using our shell skills:


~~~
head gapminder-aus.csv
~~~
{: .r}



~~~
country,year,pop,continent,lifeExp,gdpPercap
Australia,1952,8691212,Oceania,69.12,10039.59564
Australia,1957,9712569,Oceania,70.33,10949.64959
Australia,1962,10794968,Oceania,70.93,12217.22686
Australia,1967,11872264,Oceania,71.1,14526.12465
Australia,1972,13177000,Oceania,71.93,16788.62948
Australia,1977,14074100,Oceania,73.49,18334.19751
Australia,1982,15184200,Oceania,74.74,19477.00928
Australia,1987,16257249,Oceania,76.32,21888.88903
Australia,1992,17481977,Oceania,77.56,23424.76683
~~~
{: .output}

That looks better!

> ## Challenge 2
>
> Write a data-cleaning script file that subsets the gapminder
> data to include only data points collected since 1990.
>
> Use this script to write out the new subset to a file
> your working directory.
>
> Remember to use a different file name so that the new output doesn't overwrite your old output
>
> > ## Solution to challenge 2
> > 
> > ~~~
> > new_data <- gapminder[gapminder$year >= 1990,]
> > write.table(new_data,
> >   file="gapminder-1990.csv",
> >   sep=",",
> >   quote=FALSE,
> >   row.names=FALSE
> > )
> > ~~~
> > {: .r}
>{: .solution}
{: .challenge}
---

### Wrap Up

# Help Files in R
Don't forget your R helpfiles and package vignettes which can be accessed
by using the `?` and `vignette` commands.

# [Supplemental Lessons](https://carriebrown.github.io/r-novice-gapminder-2/)
Additional R topics that we could not cover today.

# R Club at UNL
The R Club meets on East Campus twice a month. It is headed by Leonardo Bastos, a PhD student in Agronomy
and Horticulture. You can [email](mailto: lmbastos@unl.edu) Leonardo for more information, or check out
the club's [GitHub page](https://github.com/ahgsa-unl) which contains previous meeting topics.

# [RStudio cheat sheets](https://www.rstudio.com/resources/cheatsheets/)
R quick reference guides including today's handouts and more!

# [R for Data Science](http://r4ds.had.co.nz/)
Hadley Wickham is RStudio's Chief Data Scientist and developer of the `dplyr` and `ggplot2` packages.
R for Data Science is his newest book, and is available here for free.

# [One R Tip a Day on Twitter](https://twitter.com/RLangTip)
Following One R Tip a Day is a great way to learn new tips and tricks in R.

# [Twotorials](http://www.twotorials.com/)
Twotorials is a compilation of 2 minute youtube videos which highlight a specific topic in R.

# [Quick R Website](http://www.statmethods.net/)

# [Cookbook for R](http://www.cookbook-r.com/)

# [Advanced R](http://adv-r.had.co.nz/)
For more advanced topics, check out Hadley Wickham's website based on his book "Advanced R".
