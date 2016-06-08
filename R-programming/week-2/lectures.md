## Functions

    > f <- function(arg1, arg2){
    > 
    > }

* Functions can be passed as arguments to other functions
* Functions can be nested, so that you can define a function inside of another function
* The return value of a function is the last expression in the function body to be evaluated.

You can mix positional matching with matching by name. When an argument is matched by name, it is “taken out” of the argument list and the remaining unnamed arguments are matched in the order that they are listed in the function definition.

## Scoping

* The global environment or the user’s workspace is always the first element of the search list and the base package is always the last.
* The order of the packages on the search list matters!
* User’s can configure which packages get loaded on startup so you cannot assume that there will be a set list of packages available.
* When a user loads a package with  library the namespace of that package gets put in position 2 of the search list (by default) and everything else gets shifted down the list.
* Note that R has separate namespaces for functions and non-functions so it’s possible to have an object named c and a function named c.


## Dates and Times
* Dates are represented by the *Date* class
* Times are represented by the *POSIXct* or the *POSIXlt* class
* Dates are stored internally as the number of days since 1970-01-01
* Times are stored internally as the number of seconds since 1970-01-01


There are a number of generic functions that work on dates and times
*POSIXct* is just a very large integer under the hood; it use a useful class when you want to store times in something like a data frame
*POSIXlt* is a list underneath and it stores a bunch of other useful information like the day of the week, day of the year, month, day of the month.
* weekdays: give the day of the week
* quarters: give the quarter number (“Q1”, “Q2”, “Q3”, or “Q4”)
* months: give the month name
  
example:


    >x <- Sys.time()
    >x
    >[1] "2013-01-24 22:04:14 EST"
    >p <- as.POSIXlt(x)
    >names(unclass(p))
    >[1] "sec" "min" "hour" "mday" "mon"
    >[6] "year" "wday" "yday" "isdst"
    >p$sec
    >[1] 14.34


Finally, there is the strptime function in case your dates are written in a different format

    > datestring <- c("January 10, 2012 10:40", "December 9, 2011 9:10")
    > x <- strptime(datestring, "%B %d, %Y %H:%M")
    > x
    > [1] "2012-01-10 10:40:00 EST" "2011-12-09 09:10:00 EST"
    
Check ?strptime for details

You can use mathematical operations on dates and times (+ and -), comparisons(i.e. ==, <=).

    >x <- as.Date("2012-03-01") y <- as.Date("2012-02-28")
    >x-y
    >Time difference of 2 days
    >x <- as.POSIXct("2012-10-25 01:00:00")
    >y <- as.POSIXct("2012-10-25 06:00:00", tz = "GMT")
    >y-x
    >Time difference of 1 hours
    
