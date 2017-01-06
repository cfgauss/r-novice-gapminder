---
layout: page
title: Figures
permalink: /figures/
---


## Introduction to RStudio

> ## Challenge 1
>
> Which of the following are valid R variable names?
> 
> ~~~
> min_height
> max.height
> _age
> .mass
> MaxLength
> min-length
> 2widths
> celsius2kelvin
> ~~~
> {: .r}
>
>
> > ## Solution to challenge 1
> >
> > The following can be used as R variables:
> > 
> > ~~~
> > min_height
> > max.height
> > MaxLength
> > celsius2kelvin
> > ~~~
> > {: .r}
> >
> > The following creates a hidden variable:
> > 
> > ~~~
> > .mass
> > ~~~
> > {: .r}
> >
> > The following will not be able to be used to create a variable
> > 
> > ~~~
> > _age
> > min-length
> > 2widths
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}

> ## Challenge 2
>
> What will be the value of each  variable  after each
> statement in the following program?
>
> 
> ~~~
> mass <- 47.5
> age <- 122
> mass <- mass * 2.3
> age <- age - 20
> ~~~
> {: .r}
>
> > ## Solution to challenge 2
> >
> > 
> > ~~~
> > mass <- 47.5
> > ~~~
> > {: .r}
> > This will give a value of 47.5 for the variable mass.
> >
> > 
> > ~~~
> > age <- 122
> > ~~~
> > {: .r}
> > This will give a value of 122 for the variable age.
> >
> > 
> > ~~~
> > mass <- mass * 2.3
> > ~~~
> > {: .r}
> > This will multiply the existing value of 47.5 by 2.3 to give a new value of
> > 109.25 to the variable mass.
> >
> > 
> > ~~~
> > age <- age - 20
> > ~~~
> > {: .r}
> > This will subtract 20 from the existing value of 122 to give a new value
> > of 102 to the variable age.
> {: .solution}
{: .challenge}


> ## Challenge 3
>
> Run the code from the previous challenge, and write a command to
> compare mass to age. Is mass larger than age?
>
> > ## Solution to challenge 3
> >
> > One way of answering this question in R is to use the `>` to set up the following:
> > 
> > ~~~
> > mass > age
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] TRUE
> > ~~~
> > {: .output}
> > This should yield a boolean value of TRUE since 109.25 is greater than 102.
> {: .solution}
{: .challenge}


> ## Challenge 4
>
> Install the packages `ggplot2` and `dplyr`
>
> After installing, load both of these packages so they are active. Try using both ways that we discussed.
>
> (Note: We will be using these packages in future lessons, so ask a helper for
> assistance if you have difficulties)
>
> > ## Solution to challenge 5
> >
> > We can use the `install.packages` command to install the required packages.
> > 
> > ~~~
> > install.packages("ggplot2")
> > install.packages("dplyr")
> > ~~~
> > {: .r}
> > 
> > You can also install packages through the `Packages` tab in the lower right pane of RStudio 
> > by clicking `Install` and then typing in the names of the packages we want to install.
> >
> > To load the packages use the following commands:
> > 
> > ~~~
> > library(ggplot2)
> > library(dplyr)
> > ~~~
> > {: .r}
> > 
> > Or you can click the corresponding checkbox next to the name of the package from the list 
> > in the `Packages` tab.
> {: .solution}
{: .challenge}

## Seeking Help

> ## Challenge 1
>
> Look at the help for the `c` function. Try the following commands and see if you can use 
> the help file to explain the output you see:
> 
> ~~~
> c(1, 2, 3)
> c('d', 'e', 'f')
> c(1, 5, 'g')
> ~~~
> {: .r}
> > ## Solution to Challenge 1
> >
> > ~~~
> > c(1,2,3)
> > [1] 1 2 3
> > c('d','e','f')
> > [1] "d" "e" "f"
> > c(1,5,'g')
> > [1] "1" "5" "g"
> > ~~~
> > {: .output}
> > 
> > The `c` function creates a vector, which is a sequence of individual elements in R. In a vector, all elements must be the
> > same data type. In the first case, we created a numeric vector. For the 
> > second, our vector is a character vector which you can see by the quotes that R put around 
> > each element. In the third example, since we gave R both numeric and character elements, R 
> > converted all the elements to characters so that our vector contained all the same type of elements.
> > 
> > Don't worry if this is confusing right now. We will clarify more in our next lesson about 
> > data structures in R.
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
> The `read.table` function is used to read data from external files into the R environment.
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
> > To view the help for the `read.table` function, you can type one of the following commands into 
> > your console:
> >
> > 
> > ~~~
> > help("read.table")
> > ?read.table
> > ~~~
> > {: .r}
> >
> > By looking at the arguments section of the help file, we can see that to prevent R from automatically assuming the first row of your file is a header row, you would specify `header = FALSE`. 
> > 
> > ~~~
> > read.table(file = "data.csv", header = FALSE)
> > ~~~
> > {: .r}
> > 
> > To switch between comma separated files (csv) and tab separated files (tsv), you would use the `sep` argument.
> > 
> {: .solution}
{: .challenge}

## Data Structures

> ## Challenge 1
>
> Predict what will happen if we perform an operation between two vectors of different size?
> 
> Test your guess by creating two vectors of different lengths using the colon operator 
> and adding or multiplying them together.
>
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
> > In a * b : longer object length is not a multiple of shorter object length
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}


> ## Challenge 2
>
> What happens when we create a vector that combines data types?
>
> Try creating a vector named `my_vector` containing the elements 1, "four", and TRUE. What does the vector 
> look like? 
> 
> Use the `str` command to determine what data type is in your vector?
>
> > ## Solution to Challenge 2
> >
> > ~~~
> > my_vector <- c(1, "four", TRUE)
> > my_vector
> > ~~~
> > {: .r}
> > 
> > ~~~
> > [1] "1"    "four" "TRUE"
> > ~~~
> > {: .output}
> > 
> > ~~~
> > str(my_vector)
> > ~~~
> > {: .r}
> > 
> > ~~~
> >  chr [1:3] "1" "four" "TRUE"
> > ~~~
> > {: .output}
> > 
> > See the quotes around each element of `my_vector`? R turned every element of the vector into 
> > a character. Since all elements of the vector must be of the same data type, R picked the 
> > best one based on the data we gave it. This is called **type coercion**. Type coercion can 
> > cause problems if your data is not consistant or if it is assigned to an unexpected data type, so we need to watch for it as we work 
> > with data in R.
> >
> > We can manually coerce the data by using commands such as `as.numeric` or `as.character`. 
> > For more information on how these commands work, you can read their help documentation by 
> > typing `?as.numeric` or `?as.character`.
> {: .solution}
{: .challenge}


> ## Challenge 3
>
> R also vectorizes functions on character vectors as well.
>
> Use the `c` function to create a character vector named `colors` with the values: "red", 
> "yellow" and "blue". Use the `paste` function to combine `"My ball is"` with each element 
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

## Subsetting Data

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

## Exploring Data Frames

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
>
> *Hint:* Use the function `typeof` to examine what is returned in each case.
>
> > ## Solution to Challenge 1
> > 
> > ~~~
> > cats[1]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >     coat
> > 1 calico
> > 2  black
> > 3  tabby
> > ~~~
> > {: .output}
> > We can think of a data frame as a list of vectors. The single brace `[1]`
> returns the first slice of the list, as another list. In this case it is the
> first column of the data frame.
> > 
> > ~~~
> > cats$coat
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] calico black  tabby 
> > Levels: black calico tabby
> > ~~~
> > {: .output}
> > This example uses the `$` character to address items by name. _coat_ is the
> first column of the data frame, again a _vector_ of type _factor_.
> > 
> > ~~~
> > cats["coat"]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >     coat
> > 1 calico
> > 2  black
> > 3  tabby
> > ~~~
> > {: .output}
> > Here we are using a single brace `["coat"]` replacing the index number with
> the column name. Like example 1, the returned object is a _list_.
> > 
> > ~~~
> > cats[1, 1]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] calico
> > Levels: black calico tabby
> > ~~~
> > {: .output}
> > This example uses a single brace, but this time we provide row and column
> coordinates. The returned object is the value in row 1, column 1. The object
> is an _integer_ but because it is part of a _vector_ of type _factor_, R
> displays the label "calico" associated with the integer value.
> > 
> > ~~~
> > cats[, 1]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> > [1] calico black  tabby 
> > Levels: black calico tabby
> > ~~~
> > {: .output}
> > Like the previous example we use single braces and provide row and column
> coordinates. The row coordinate is not specified, R interprets this missing
> value as all the elements in this _column_ _vector_.
> > 
> > ~~~
> > cats[1, ]
> > ~~~
> > {: .r}
> > 
> > 
> > 
> > ~~~
> >     coat weight likes_string
> > 1 calico    2.1         TRUE
> > ~~~
> > {: .output}
> > Again we use the single brace with row and column coordinates. The column
> coordinate is not specified. The return value is a _list_ containing all the
> values in the first row.
> {: .solution}
{: .challenge}



> ## Challenge 2
>
> Remember that you can create a new data.frame right from within R with the following syntax:
> 
> ~~~
> df <- data.frame(id = c('a', 'b', 'c'),
>                  x = 1:3,
>                  y = c(TRUE, TRUE, FALSE),
>                  stringsAsFactors = FALSE)
> ~~~
> {: .r}
>
> Note that the `stringsAsFactors` setting allows us to tell R that we want to preserve our 
> character fields and not have R convert them to factors.
>
> Make a data.frame that holds the following information for yourself:
>
> - first name
> - last name
> - lucky number
>
> Then use `rbind` to add an entry for the people sitting beside you.
> Finally, use `cbind` to add a column with each person's answer to the question, "Is it time for coffee break?"
>
> > ## Solution to Challenge 2
> > 
> > ~~~
> > df <- data.frame(first = c('Grace'),
> >                  last = c('Hopper'),
> >                  lucky_number = c(0),
> >                  stringsAsFactors = FALSE)
> > df <- rbind(df, list('Marie', 'Curie', 238) )
> > df <- cbind(df, coffeetime = c(TRUE,TRUE))
> > ~~~
> > {: .r}
> {: .solution}
{: .challenge}

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
> {: .solution}
{: .challenge}

## Control Flow

> ## Challenge 1
>
> Use an `if` statement to print a suitable message
> reporting whether there are any records from 2002 in
> the `gapminder` dataset.
> Now do the same for 2012.
>
> > ## Solution to Challenge 1
> > We will first see a solution to Challenge 1 which does not use the `any` function.
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
> > All this can be done more quickly with `any`. The logical condition can be expressed as:
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


> ## Challenge 2
>
> Compare the objects output_vector and
> output_vector2. Are they the same? If not, why not?
> How would you change the last block of code to make output_vector2
> the same as output_vector?
>
> > ## Solution to Challenge 2
> > We can check whether the two vectors are identical using the `all` function:
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
> > This is because `as.vector` outputs the elements of an input matrix going over its column.
> > Taking a look at `output_matrix`, we can notice that we want its elements by rows.
> > The solution is to transpose the `output_matrix`. We can do it either by calling the transpose function
> > `t` or by inputing the elements in the right order.
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

## Dataframe Manipulation

![](../fig/13-dplyr-fig1.png)

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


![](../fig/13-dplyr-fig2.png)

![](../fig/13-dplyr-fig3.png)


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


> ## Advanced Challenge
>
> Calculate the average life expectancy in 2002 of 2 randomly selected countries
> for each continent. Then arrange the continent names in reverse order.
> **Hint:** Use the `dplyr` functions `arrange` and `sample_n`, they have
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

## Coffee Break

## Creating Publication Quality Graphics

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

## Writing Data

<img src="../fig/12-data-fig1.png" title="export plots in rstudio" alt="export plots in rstudio" style="display: block; margin: auto;" />

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
> {: .solution}
{: .challenge}


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

## Wrapup

If you want to learn more, check out some of these great resources:

### Help Files in R
Don't forget your R helpfiles and package vignettes which can be accessed
by using the `?` and `vignette` commands.

### [Supplemental Lessons](https://carriebrown.github.io/r-novice-gapminder-2/)
Additional R topics that we could not cover today.

### R Club at UNL
The R Club meets on East Campus twice a month. It is headed by Leonardo Bastos, a PhD student in Agronomy
and Horticulture. You can [email](mailto: lmbastos@unl.edu) Leonardo for more information, or check out
the club's [GitHub page](https://github.com/ahgsa-unl) which contains previous meeting topics.

### [RStudio cheat sheets](https://www.rstudio.com/resources/cheatsheets/)
R quick reference guides including today's handouts and more!

### [R for Data Science](http://r4ds.had.co.nz/)
Hadley Wickham is RStudio's Chief Data Scientist and developer of the `dplyr` and `ggplot2` packages.
**R for Data Science** is his newest book, and is available here for free.

### [One R Tip a Day on Twitter](http://twitter.com/RLangTip)
Following One R Tip a Day is a great way to learn new tips and tricks in R.

### [Twotorials](http://www.twotorials.com/)
Twotorials is a compilation of 2 minute youtube videos which highlight a specific topic in R.

### [Quick R Website](http://www.statmethods.net/)

### [Cookbook for R](http://www.cookbook-r.com/)

### [Advanced R](http://adv-r.had.co.nz/)
For more advanced topics, check out Hadley Wickham's website based on his book "Advanced R".
