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

