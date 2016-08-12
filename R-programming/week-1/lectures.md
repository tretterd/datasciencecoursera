## Basic classes of objects
* character
* numeric (real numbers)
* integer
* complex
* logical (True/False)

## Numbers
Numbers in R a generally treated as numeric objects (i.e. double precision real numbers)

If you explicitly want an integer, you need to specify the **L** suffix 

* *Ex:* Entering 1 gives you a numeric object; entering 1L explicitly gives you an integer.
There is also a special number Inf which represents infinity

The value **NaN** represents an undefined value (“not a number”). NaN can also be thought of as a missing value (more on that later)

## Attributes 
* names, dimnames
* dimensions (e.g. matrices, arrays)
* class
* length
* other user-defined attributes/metadata
Attributes of an object can be accessed using the attributes() function

## Vectors
The most basic object is a vector
A vector can only contain objects of the same class.

Empty vectors can be created with the vector() function

    >x <- vector("numeric", length = 10)

The  c() function can be used to create vectors of objects.

    >vec <- c(0.5, "a", True) 
When different objects are mixed in a vector, coercion occurs so that every element in the vector is of the same class.

    > class(vec)
    > character
    
## Matrices

Matrices are vectors with a dimension attribute. The dimension attribute is itself an integer vector of length 2 (nrow, ncol)

    > >m <- matrix(nrow = 2, ncol = 3)
    > >m
    >[,1] [,2] [,3]
    >[1,] NA NA NA
    >[2,] NA NA NA
    > >dim(m)
    >[1] 2 3
    > >attributes(m)
    >$dim
    >[1] 2 3
    

Matrices are constructed column-wise, so entries can be thought of starting in the “upper left” corner and running down the columns.

    > >m <- matrix(1:6, nrow = 2, ncol = 3)
    > >m
    >[,1] [,2] [,3]
    >[1,] 1 3 5
    >[2,] 2 4 6  
    
Matrices can also be created directly from vectors by adding a dimension attribute.

    > > m <- 1:10
    > > m
    >[1] 1 2 3 4 5 6 7 8 9 10
    > > dim(m) <- c(2, 5)
    > > m
    >[,1] [,2] [,3] [,4] [,5]
    >[1,] 1 3 5 7 9
    >[2,] 2 4 6 8 10
    
Matrices can be created by column-binding or row-binding with  *cbind()* and  *rbind()*

    > > x <- 1:3
    > > y <- 10:12
    > > cbind(x, y)
    >x y
    >[1,] 1 10
    >[2,] 2 11
    >[3,] 3 12
    > > rbind(x, y)
    >[,1] [,2] [,3]
    >x 1 2 3
    >y 10 11 12
    

## Lists

Lists are a special type of vector that can contain elements of different classes.

    > > x <- list(1, "a", TRUE, 1 + 4i)
    > > x
    >[[1]]
    >[1] 1
    >[[2]]
    >[1] "a"
    >[[3]]
    >[1] TRUE
    >[[4]]
    >[1] 1+4i
    
## Factors

Factors are used to represent categorical data. Factors can be unordered or ordered. One can think of a factor as an integer vector where each integer has a label.
* Factors are treated specially by modelling functions like  **lm()** and  **glm()**
* Using factors with labels is better than using integers because factors are self-describing.


    > > x <- factor(c("yes", "yes", "no", "yes", "no"))
    >> x
    >[1] yes yes no yes no
    >Levels: no yes
    >> table(x)
    >x
    >no yes
    >2 3
    >> unclass(x)
    >[1] 2 2 1 2 1
    ?attr(,"levels")
    >[1] "no" "yes"
    
The order of the levels can be set using the  levels argument to  factor() . This can be important
in linear modelling because the first level is used as the baseline level.

    >> x <- factor(c("yes", "yes", "no", "yes", "no"),
    >levels = c("yes", "no"))
    >> x
    >[1] yes yes no yes no
    >Levels: yes no
    

## Missing values

* Missing values are denoted by  NA or  NaN for undefined mathematical operations.
*is.na()* is used to test objects if they are  NA
*is.nan()* is used to test for  NaN
* NA values have a class also, so there are integer  NA , character  NA , etc.
* A  NaN value is also  NA but the converse is not true


## Data Frames

* Data frames are used to store tabular data. They are represented as a special type of list where every element of the list has to have the same length. Each element of the list can be thought of as a column and the length of each element of the list is the number of rows
* Unlike matrices, data frames can store different classes of objects in each column (just like lists);
* Data frames also have a special attribute called  *row.names*
* Data frames are usually created by calling  *read.table()* or  *read.csv()*
* Can be converted to a matrix by calling  *data.matrix()*


## Names

R objects can also have names, which is very useful for writing readable code and self-describing
objects.

    >> x <- 1:3
    >> names(x)
    >NULL
    >> names(x) <- c("foo", "bar", "norf")
    >> x
    >foo bar norf
    >1 2 3
    >> names(x)
    >[1] "foo" "bar" "norf"
    
Lists and matrices can also have names.

    >> x <- list(a = 1, b = 2, c = 3)
    >> x
    >$a
    >[1] 1
    >$b
    >[1] 2
    >$c
    >[1] 3
    >
    >> m <- matrix(1:4, nrow = 2, ncol = 2)
    >> dimnames(m) <- list(c("a", "b"), c("c", "d"))
    >> m
    >c d
    >a 1 3
    >b 2 4
