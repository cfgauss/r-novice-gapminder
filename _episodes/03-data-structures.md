---
title: "Data Structures"
teaching: 50
exercises: 15
questions:
- "What are the basic data types in R?"
- "How does R handle operations on different data types?"
objectives:
- "To be aware of the different types of data."
- "To be able to ask questions from R about the type, class, and structure of an object."
keypoints:
- "The basic data types in R are double, integer, complex, logical, and character."
- "These basic data types can be used to build larger data structures, called classes."
---

## Data Types in R

In the previous lesson, we discovered how to perform operations on variables through 
operators such as `+` and `*`. Let's review that now, using the `mass` and `age` variables 
we assigned during our last challenges:

~~~
x + z
~~~
{: .r}

~~~
[1] 101.025
~~~
{: .output}


~~~
x + y
~~~
{: .r}

~~~
Error in x + y : non-numeric argument to binary operator
~~~
{: .output}

As you might have expected, R gave us an error. It does not know how to add the values 
101 and "green". This is because these are not the correct data types. R has 5 main data 
types: `double`, `integer`, `complex`, `logical`, and `character`.

~~~
[1] "double"
~~~
{: .output}

There are 5 main types: `double`, `integer`, `complex`, `logical` and `character`.


~~~
typeof(3.14)
~~~
{: .r}



~~~
[1] "double"
~~~
{: .output}



~~~
typeof(1L)
~~~
{: .r}



~~~
[1] "integer"
~~~
{: .output}



~~~
typeof(1+1i)
~~~
{: .r}



~~~
[1] "complex"
~~~
{: .output}



~~~
typeof(TRUE)
~~~
{: .r}



~~~
[1] "logical"
~~~
{: .output}


~~~
typeof('banana')
~~~
{: .r}

~~~
[1] "character"
~~~
{: .output}

Note the `L` suffix to insist that a number is an integer. No matter how
complicated our analyses become, all data in R is interpreted as one of these
basic data types.

## Vectors

Remember previously when R returned a value, it prepended the output with `[1]`? This is 
because R never actually works with just one value, but always a string of values called 
a **vector**. As we saw in our last challenge, we can create vectors by 
using the `c()` function.

~~~
x <- c(2, 4, 6, 8, 10, 12, 14, 16)
~~~
{: .r}

We can also use the colon operator to quickly create sequential vectors:

~~~
y <- 1:8
~~~
{: .r}


R is a **vectorized** language. This means that we can perform operations on the entire 
vector just like we did for single values previously. When we apply operations to a vector, 
R returns a new vector with the results.

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

Notice that when we add two different vectors together, R performs the operation element 
by element. This is the way R handles most base operations between two vectors.

> ## Challenge 1
>
> What will happen if we perform an operation between two vectors of different size?
> 
> Test your guess by creating two vectors of different lengths using the colon operator 
> and adding or multiplying them together.
>
> > ## Solution to Challenge 1
> >
> > 
> > ~~~
> > a <- 1:10
> > b <- 1:5
> > a * b
> > ~~~
> > {: .r}
> > 
> > ~~~
> > [1]  1  4  9 16 25  6 14 24 36 50
> > ~~~
> > {: .output}
> > 
> > Notice how R repeated the shorter vector until it had finished operating on every 
> > element of the larger vector. This is known as "vector recycling".
> >
> > If your shorter vector is not a even multiple of the larger one, R will still perform 
> > the operation but it will give you the following error message:
> >
> > ~~~
> > Warning message:
> > In x + y : longer object length is not a multiple of shorter object length
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

Vectors can be made up of any of the basic data types.

Examples of character, logical, other vectors

challenge asking what happens if we combine times?

> ## Challenge 2
>
> R also vectorizes operations on character vectors as well.
>
> Use the `c()` function to create a character vector named `colors` with the values: "red", 
> "yellow" and "blue". Use the `paste()` function to combine `"My ball is"` with each element 
> of your vector.
> 
> > ## Solution to Challenge 2
> >
> > ~~~
> > colors <- c("red", "yellow", "blue")
> > paste("My ball is", colors)
> > ~~~
> > {: .r}
> > 
> > ~~~
> > [1] "My ball is red"    "My ball is yellow"
> > [3] "My ball is blue"  
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

Discussion of the str() command and length() commands, discussion of using c() to lengthen vectors

There are other data structures in R called **lists**, **matrices**, and **arrays**. You 
can discover more about these by looking at the help files associated with their constructor 
functions: `?list()`, `?matrix()`, `?array()`.



