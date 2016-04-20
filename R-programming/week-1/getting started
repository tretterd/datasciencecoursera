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
``` x <- vector("numeric", length = 10) ```

The  c() function can be used to create vectors of objects. 
``` vec <- c(0.5, "a", True) ```   -  When different objects are mixed in a vector, coercion occurs so that every element in the vector is
of the same class.

    > class(vec)
    > character
