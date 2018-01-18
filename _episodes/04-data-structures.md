---
title: "Data Structures"
teaching: 15
exercises: 10
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
operators such as `+` and `*`. Let's review that now, using the variables `x` and `z` that
we assigned during our last lesson:

~~~
x + z
~~~
{: .r}

~~~
[1] 101.025
~~~
{: .output}


Our output was just as we expected. Let's try adding together `x` and `y`:

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
typeof(3.14)
~~~
{: .r}


~~~
[1] "double"
~~~
{: .output}

A `double`, also referred to as a *floating point number*, is how R stores numeric values
by default.


~~~
typeof(1L)
~~~
{: .r}



~~~
[1] "integer"
~~~
{: .output}

To use an `integer` value in R, we use the L to tell R that this value is an integer value.
Without the L, R would store this value as a `double`.


~~~
typeof(1+1i)
~~~
{: .r}



~~~
[1] "complex"
~~~
{: .output}

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

Remember previously when R returned a value, it prepended the output with `[1]`? This is
because R never actually works with just one value, but always a series of values called
a **vector**. All of our previous output were vectors with a length of 1.
As we saw in our last challenge, we can create vectors of longer length by
using the `c` function.

~~~
x <- c(2, 4, 6, 8, 10, 12, 14, 16)
x
~~~
{: .r}

~~~
[1]  2  4  6  8 10 12 14 16
~~~
{: .output}

Additionally, we can also use the **colon operator** to quickly create sequential vectors:

~~~
y <- 1:8
y
~~~
{: .r}

~~~
[1] 1 2 3 4 5 6 7 8
~~~
{: .output}

Using the colon operator, we can specify whatever start and stop point we want and R will automatically create an `integer` vector containing these and all numbers between for us.

~~~
-4:7
~~~
{: .r}

~~~
[1] -4 -3 -2 -1  0  1  2  3  4  5  6  7
~~~
{: .output}

R is **vectorized**. This means that we can perform operations on the entire
vector just like we did for single values previously. When operations are applied to a vector,
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
by element:


~~~
x:  2  4  6  8 10 12 14 16
    +  +  +  +  +  +  +  +
y:  1  2  3  4  5  6  7  8
--------------------------
    3  6  9 12 15 18 21 24
~~~
{: .r}



Vectors can be made up of any of the basic data types.

#### Character Vectors:

~~~
a <- c("one", "two", "three", "four")
a
~~~
{: .r}

~~~
[1] "one"   "two"   "three" "four"
~~~
{: .output}

Just like we used the `typeof` command earlier, the `str` command will also tell us the data
type of our object. Additionally, it gives us a compact view of some basic information about
our object.

~~~
str(a)
~~~
{: .r}

~~~
 chr [1:4] "one" "two" "three" "four"
~~~
{: .output}

We can see from the first three letters *chr* that this is a *character* vector. The numbers
in the brackets indicates the dimensions of our vector. And then it will list the first few
elements of the vector.

#### Logical Vectors:

~~~
b <- c(TRUE, TRUE, FALSE, TRUE)
b
~~~
{: .r}

~~~
[1]  TRUE  TRUE FALSE  TRUE
~~~
{: .output}

In addition to using the `c` command to create vectors, we can use it to add elements to an
existing vector:

~~~
c(x, 20, 25)
~~~
{: .r}

~~~
 [1]  2  4  6  8 10 12 14 16 20 25
~~~
{: .output}

These changes won't take place until we use the assignment arrow to store the new value.
Let's modify our vector `y` so that it contains all numbers up to 20. We can use the colon
operator that we talked about earlier:

~~~
y <- c(y, 9:20)
y
~~~
{: .r}

~~~
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
~~~

This is an example of a **nested operation**. Remember from the order of operations previously,
R will do any operations inside the parenthesis first. In this example, R created the sequence
from 9 to 20, and then it combined it with what we already had stored in `y`.

Another helpful function for vectors is `length`. We can use this command to quickly return the length of a vector.

~~~
length(y)
~~~
{: .r}

~~~
[1] 20
~~~
{: .r}

> ## Challenge 1
>
> Predict what will happen if we perform an operation between two vectors of different size?
>
> Test your guess by creating two vectors of different lengths using the colon operator
> and adding or multiplying them together.
{: .challenge}


> ## Challenge 2
>
> What happens when we create a vector that combines data types?
>
> Try creating a vector named `my_vector` containing the elements 1, "four", and TRUE. What does the vector
> look like?
>
> Use the `str` command to determine what data type is in your vector?
{: .challenge}


> ## Challenge 3
>
> R also vectorizes functions on character vectors as well.
>
> Use the `c` function to create a character vector named `colors` with the values: "red",
> "yellow" and "blue". Use the `paste` function to combine `"My ball is"` with each element
> of your vector.
{: .challenge}

There are other data structures in R called **lists** and **matrices**. You
can discover more about these by looking at the help files associated with their constructor
functions: `?list`, `?matrix` or by checking out the supplemental lesson [Lists and Matrices](https://carriebrown.github.io/r-novice-gapminder-2/02-additional-datatypes/)

Today, we will be working primarily with the **data frame** data structures. We will explore these
more indepth after our break.
v
