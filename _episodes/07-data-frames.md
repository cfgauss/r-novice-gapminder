---
title: "Exploring Data Frames"
teaching: 35
exercises: 25
questions:
- "How can access datasets in R?"
- "How do I represent categorical information in R?"
- "How can I manipulate a dataframe?"
objectives:
- "To begin exploring data frames and understand how it's related to vectors, factors and lists."
- "To learn how to manipulate a data.frame in memory."
- "To tour some best practices of exploring and understanding a data frame when it is first loaded."
keypoints:
- "Use `cbind` to add a new column to a dataframe."
- "Use `rbind` to add a new row to a dataframe."
- "Remove rows from a dataframe."
- "Use `na.omit` to remove rows from a dataframe with `NA` values."
---

## Data Frames

So far we have covered data structures which contain all the same basic data type. But
one of R's most powerful features is its ability to deal with tabular data -
like what you might already have in a spreadsheet or a CSV. **Data Frames** are built from
vectors but they can contain vectors of different data types.

To build a data frame from existing vectors we use the `data.frame` command. Let's build
a data frame for with some information on cats.

~~~
coat <- c("calico", "black", "tabby")
weight <- c(2.1, 5.0, 3.2)
likes_string <- c(TRUE, FALSE, TRUE)

cats <- data.frame(coat, weight, likes_string)
cats
~~~
{: .r}

~~~
    coat weight likes_string
1 calico    2.1         TRUE
2  black    5.0        FALSE
3  tabby    3.2         TRUE
~~~
{: .output}

We can begin exploring our dataset right away, pulling out columns by specifying
them using the `$` operator:


~~~
cats$weight
~~~
{: .r}



~~~
[1] 2.1 5.0 3.2
~~~
{: .output}



~~~
cats$coat
~~~
{: .r}



~~~
[1] calico black  tabby
Levels: black calico tabby
~~~
{: .output}

Just like we did with vectors, we can perform operations on columns within our data frame:


~~~
## Say we discovered that the scale weighs two Kg light:
cats$weight + 2
~~~
{: .r}



~~~
[1] 4.1 7.0 5.2
~~~
{: .output}



~~~
paste("My cat is", cats$coat)
~~~
{: .r}



~~~
[1] "My cat is calico" "My cat is black"  "My cat is tabby"
~~~
{: .output}


Try this challenge to see different ways of interacting with data frames:

> ## Challenge 1
>
> There are several subtly different ways to call variables, observations and
> elements from data.frames:
>
> - `cats[1]`
> - `cats$coat`
> - `cats`["coat"]
> - `cats[1, 1]`
> - `cats[, 1]`
> - `cats[1, ]`
>
> Try out these examples and explain what is returned by each one.
{: .challenge}

Let's modify our data frame by adding an additional column which will hold the age of each
of the cats. As we saw in the previous challenge, columns in a data frame are vectors which
we construct using the `c` function as before:

~~~
age <- c(2,3,5,12)
cats
~~~
{: .r}



~~~
    coat weight likes_string
1 calico    2.1         TRUE
2  black    5.0        FALSE
3  tabby    3.2         TRUE
~~~
{: .output}

We can then add this as a column in our data frame by using the `cbind` function:


~~~
cats <- cbind(cats, age)
~~~
{: .r}



~~~
Error in data.frame(..., check.names = FALSE): arguments imply differing number of rows: 3, 4
~~~
{: .error}

Why didn't this work? Of course, R wants to see one element in our new column
for every row in the table. Since our data frame only has 3 rows, we can only add a column
with 3 elements. Let's try that again:


~~~
age <- c(2,3,5)
cats <- cbind(cats, age)
cats
~~~
{: .r}



~~~
    coat weight likes_string age
1 calico    2.1         TRUE   2
2  black    5.0        FALSE   3
3  tabby    3.2         TRUE   5
~~~
{: .output}

Now how about adding rows - in this case, we saw last time that the rows of a
data.frame are made of lists:


~~~
newRow <- list("tortoiseshell", 3.3, TRUE, 9)
cats <- rbind(cats, newRow)
~~~
{: .r}



~~~
Warning in `[<-.factor`(`*tmp*`, ri, value = "tortoiseshell"): invalid
factor level, NA generated
~~~
{: .error}

Our list had the correct number of elements, so why did R give us a warning? It looks like
the error occurred in the `coat` column. Let's take a closer look.

~~~
class(cats$coat)
~~~
{: .r}

~~~
[1] "factor"
~~~
{: .output}


So in our `cats` data frame, the `coat` column is a data class named a **factor**. Factors
are data classes that R uses to handle categorical data. Each category in a factor is called a **level**
When we tried adding a new row to the `cats` data frame, the new data contained a level of
`coat` that we had not previously used.  This is something we need to look out for - when
R creates a factor, it only
allows whatever is originally there when our data was first loaded, which was
'black', 'calico' and 'tabby' in our case. Anything new that doesn't fit into
one of its categories is rejected as nonsense and is replaced by an `NA` until we explicitly add that as a
level to the factor:


~~~
levels(cats$coat)
~~~
{: .r}



~~~
[1] "black"  "calico" "tabby"
~~~
{: .output}



~~~
levels(cats$coat) <- c(levels(cats$coat), 'tortoiseshell')
cats <- rbind(cats, newRow)
~~~
{: .r}

Alternatively, we can change a factor column to a character vector; we lose the
handy categories of the factor, but can subsequently add any word we want to the
column without babysitting the factor levels:


~~~
str(cats)
~~~
{: .r}



~~~
'data.frame':	5 obs. of  4 variables:
 $ coat        : Factor w/ 4 levels "black","calico",..: 2 1 3 NA 4
 $ weight      : num  2.1 5 3.2 3.3 3.3
 $ likes_string: logi  TRUE FALSE TRUE TRUE TRUE
 $ age         : num  4 5 8 9 9
~~~
{: .output}



~~~
cats$coat <- as.character(cats$coat)
str(cats)
~~~
{: .r}



~~~
'data.frame':	5 obs. of  4 variables:
 $ coat        : chr  "calico" "black" "tabby" NA ...
 $ weight      : num  2.1 5 3.2 3.3 3.3
 $ likes_string: logi  TRUE FALSE TRUE TRUE TRUE
 $ age         : num  4 5 8 9 9
~~~
{: .output}

We now know how to add rows and columns to our data.frame in R - but in our work
we've accidentally added a garbage row:


~~~
cats
~~~
{: .r}



~~~
           coat weight likes_string age
1        calico    2.1         TRUE   4
2         black    5.0        FALSE   5
3         tabby    3.2         TRUE   8
4          <NA>    3.3         TRUE   9
5 tortoiseshell    3.3         TRUE   9
~~~
{: .output}

We can ask for a data.frame minus this offending row:


~~~
cats[-4,]
~~~
{: .r}



~~~
           coat weight likes_string age
1        calico    2.1         TRUE   4
2         black    5.0        FALSE   5
3         tabby    3.2         TRUE   8
5 tortoiseshell    3.3         TRUE   9
~~~
{: .output}

Notice the comma with nothing after it to indicate we want to drop the entire fourth row.

Alternatively, we can drop all rows with `NA` values by using the `na.omit` command:


~~~
na.omit(cats)
~~~
{: .r}



~~~
           coat weight likes_string age
1        calico    2.1         TRUE   4
2         black    5.0        FALSE   5
3         tabby    3.2         TRUE   8
5 tortoiseshell    3.3         TRUE   9
~~~
{: .output}

Let's reassign the output to `cats`, so that our changes will be permanent:


~~~
cats <- na.omit(cats)
~~~
{: .r}

We can also glue two dataframes together with `rbind`:


~~~
cats <- rbind(cats, cats)
cats
~~~
{: .r}



~~~
            coat weight likes_string age
1         calico    2.1         TRUE   4
2          black    5.0        FALSE   5
3          tabby    3.2         TRUE   8
5  tortoiseshell    3.3         TRUE   9
11        calico    2.1         TRUE   4
21         black    5.0        FALSE   5
31         tabby    3.2         TRUE   8
51 tortoiseshell    3.3         TRUE   9
~~~
{: .output}
But now the row names are unnecessarily complicated. We can remove the rownames,
and R will automatically re-name them sequentially:


~~~
rownames(cats) <- NULL
cats
~~~
{: .r}



~~~
           coat weight likes_string age
1        calico    2.1         TRUE   4
2         black    5.0        FALSE   5
3         tabby    3.2         TRUE   8
4 tortoiseshell    3.3         TRUE   9
5        calico    2.1         TRUE   4
6         black    5.0        FALSE   5
7         tabby    3.2         TRUE   8
8 tortoiseshell    3.3         TRUE   9
~~~
{: .output}

> ## Challenge 2
>
> Remember that you can create a new data.frame right from within R with the following syntax:
>
> ~~~
> variable1 <- c('a', 'b', 'c')
> variable2 <- c(1, 2, 3)
> variable3 <- c(TRUE, TRUE, FALSE)
> df <- data.frame(variable1,
>                  variable2,
>                  variable3,
>                  stringsAsFactors = FALSE)
> ~~~
> {: .r}
>
> Note that the `stringsAsFactors` setting allows us to tell R that we want to preserve our
> character fields and not have R convert them to factors.
>
> Modifying the syntax above, make a data.frame that holds the following information for yourself:
>
> - first name
> - last name
> - lucky number
>
> Then use `rbind` to add an entry for the people sitting beside you.
> Finally, use `cbind` to add a column with each person's answer to the question, "Is it time for coffee break?"
{: .challenge}


#### Data Frames with Gapminder

So far, you've seen the basics of manipulating data.frames with our cat data;
now, let's use those skills to digest a more realistic dataset. For the remainder of our
lesson, we are going to use the `gapminder` data set built into the `gapminder` package.

If you did not install the `gapminder` package with our previous challenge, you can do so
now with the `install.packages` command:

~~~
install.packages("gapminder")
~~~
{: .r}

If you have already installed the `gapminder` package, go ahead and load it now. You can tell
R to load the package by clicking the checkbox next to its listing in the package tab of the
lower left pane in R studio. Or you can load it by using the `library` command:

~~~
library('gapminder')
~~~
{: .r}

To make sure our analysis is reproducible, we should put the code
into a script file so we can come back to it later.

> ## Note:
>
> The `library` command can be used within your scripts to load any packages that your
> scripts need. To make your scripts easy to read by others, you will want to put these commands
> at the top of your script file. You can learn more about writing easy to read code in the
> supplemental lesson [Writing Good Software](https://carriebrown.github.io/r-novice-gapminder-2/07-wrap-up/).
{: .callout}

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
number of rows it has (1704), but this is not the case. Let's find out why:


~~~
typeof(gapminder)
~~~
{: .r}



~~~
[1] "list"
~~~
{: .output}

> ## Tip: Data Frames
>
> Data Frames are actually **lists** of **vectors**. So, while they behave similarly to vectors, there are some differences in some commands.
>
> For more information about lists, or other R data types such as matrices and arrays, check out the Supplemental Lesson [Lists and Matrices](https://carriebrown.github.io/r-novice-gapminder-2/02-additional-datatypes/)
{: .callout}

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

### Subsetting Data Frames

Remember that data frames are lists of vectors. Similarly to how we subsetted vectors, using the `[` operator with one argument will extract one element from our list.
In this case, our elements are vectors, so the `[` operator will return a list of vectors, the columns of our data frame.


~~~
head(gapminder[5])
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

As before, we can also use the `c` command to return multiple columns:

~~~
head(gapminder[c(1,5)])
~~~
{: .r}

~~~
      country      pop
1 Afghanistan  8425333
2 Afghanistan  9240934
3 Afghanistan 10267083
4 Afghanistan 11537966
5 Afghanistan 13079460
6 Afghanistan 14880372
~~~
{: .output}

The `$` operator provides a convenient shorthand to extract columns by name:

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


> ## Challenge 3
>
> Fix each of the following common data frame subsetting errors:
>
> 1. Extract observations collected for the year 1957.
>
>
>    ~~~
>    gapminder[gapminder$year = 1957,]
>    ~~~
>    {: .r}
>
> 2. Extract all columns except 1 through 4.
>
>
>    ~~~
>    gapminder[,-1:4]
>    ~~~
>    {: .r}
>
> 3. Extract the rows where the life expectancy is longer than 80 years.
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
>    and 2007.
>
>
>    ~~~
>    gapminder[gapminder$year == 2002 | 2007,]
>    ~~~
>    {: .r}
{: .challenge}

> ## Challenge 4
>
> 1. Why does `gapminder[1:20]` return an error? How does it differ from `gapminder[1:20, ]`?
>
>
> 2. Create a new `data.frame` called `gapminder_small` that only contains rows 1 through 9
> and 19 through 23. You can do this in one or two steps.
{: .challenge}
