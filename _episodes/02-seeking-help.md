---
title: "Seeking Help"
teaching: 10
exercises: 10
questions:
- "How can I get help in R?"
objectives:
- "To be able read R help files for functions and special operators."
- "To be able to use CRAN task views to identify packages to solve a problem."
- "To be able to seek help from your peers."
keypoints:
- "Use `help()` to get online help in R."
---



## Reading Help files

R, and every package, provide help files for functions. To search for help on a
function from a specific function that is in a package loaded into your
namespace (your interactive R session):


~~~
?function_name
help(function_name)
~~~
{: .r}

This will load up a help page in RStudio (or as plain text in R by itself).

Each help page is broken down into sections:

 - Description: An extended description of what the function does.
 - Usage: The arguments of the function and their default values.
 - Arguments: An explanation of the data each argument is expecting.
 - Details: Any important details to be aware of.
 - Value: The data the function returns.
 - See Also: Any related functions you might find useful.
 - Examples: Some examples for how to use the function.

Different functions might have different sections, but these are the main ones you should be aware of.

> ## Tip: Reading help files
>
> One of the most daunting aspects of R is the large number of functions
> available. It would be prohibitive, if not impossible to remember the
> correct usage for every function you use. Luckily, the help files
> mean you don't have to!
{: .callout}

## Special Operators

To seek help on special operators, use quotes:


~~~
?"+"
~~~
{: .r}

## Getting help on packages

Many packages come with "vignettes": tutorials and extended example documentation.
Without any arguments, `vignette()` will list all vignettes for all installed packages;
`vignette(package="package-name")` will list all available vignettes for
`package-name`, and `vignette("vignette-name")` will open the specified vignette.

If a package doesn't have any vignettes, you can usually find help by typing
`help("package-name")`.

## When you kind of remember the function

If you're not sure what package a function is in, or how it's specifically spelled you can do a fuzzy search:


~~~
??function_name
~~~
{: .r}

## When you have no idea where to begin

If you don't know what function or package you need to use
[CRAN Task Views](http://cran.at.r-project.org/web/views)
is a specially maintained list of packages grouped into
fields. This can be a good starting point.

## When your code doesn't work: seeking help from your peers

If you're having trouble using a function, 9 times out of 10,
the answers you are seeking have already been answered on
[Stack Overflow](http://stackoverflow.com/). You can search using
the `[r]` tag.

> ## Challenge 1
>
> Look at the help for the `c` function. What kind of vector do you
> expect you will create if you evaluate the following:
> 
> ~~~
> c(1, 2, 3)
> c('d', 'e', 'f')
> c(1, 2, 'f')`
> ~~~
> {: .r}
> > ## Solution to Challenge 1
> >
> > The `c()` function creates a vector, in which all elements are the
> > same type. In the first case, the elements are numeric, in the
> > second, they are characters, and in the third they are characters:
> > the numeric values "coerced" to be characters.
> {: .solution}
{: .challenge}

> ## Challenge 2
> 
> Look at the help for the `typeof` function. What does this function do?
> Try creating the following objects and using this function on them. 
>
> 1. m <- 15
> 2. n <- "Lincoln"
>
> Explain to your neighbor what this function is telling us about these objects:
>
> > ## Solution to Challenge 2
> > 
> > ~~~
> > help("typeof")
> > ?typeof
> > ~~~
> > {: .r}
> > 
> > We can see from the help file that `typeof` tells us the type of an object in R. We will 
> > discuss R data types further in the next lecture.
> >
> > ~~~
> > m <- 15
> > typeof(m)
> > ~~~
> > 
> > ~~~
> > [1] "double"
> > ~~~
> > {: .output}
> > 
> > This is telling us that `m` is the data type `double` which is a numeric data type in R.
> >
> > ~~~
> > n <- "Lincoln"
> > typeof(n)
> > ~~~
> > {: .r}
> > 
> > ~~~
> > [1] "character"
> > ~~~
> > {: .output}
> > 
> > Here, `n` is the data type `character` which is the data type R uses for strings.
> {: .solution}
{: .challenge}

> ## Challenge 3 - Advanced
>
> The `read.table` function is used to read in external files into a data frame format.
> For example: to read in a file called "data.csv" you would use the following command:
> 
> ~~~
> read.table(file = "data.csv")
> ~~~
> {: .r}
>
> Look at the help for the `read.table` function.
>
> What argument would you use if you wanted to read in a file without a header?
> What argument would allow you to switch between a comma separated file and a tab separated
> file?
>
> > ## Solution to Challenge 3
> >
> > Look at the help for the `read.table` function.
> >
> > 
> > ~~~
> > help("read.table")
> > ?read.table
> > ~~~
> > {: .r}
> >
> > In order to prevent R from automatically assuming the first row of your file is a header row,
> > you would specify `header = FALSE` in your function call. To switch between comma separated 
> > files (csv) and tab separated files (tsv), you would use the `sep` argument.
> > 
> {: .solution}
{: .challenge}


## Other ports of call

* [Quick R](http://www.statmethods.net/)
* [RStudio cheat sheets](http://www.rstudio.com/resources/cheatsheets/)
* [Cookbook for R](http://www.cookbook-r.com/)
