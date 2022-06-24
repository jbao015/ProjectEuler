# Problem

If we list all the natural numbers below 10 that are multiples of 3 or
5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

# Solution 1

Many ways to solve this problem. Here is one:

1.  sum all multiples of 3
2.  sum all multiples of 5
3.  subtract all multiples of 15

``` r
solution <- function(n) {
  # get highest multiple of 3 under n, divided by 3
  base_3 <- (n-1) %/% 3
  
  # get highest multiple5 under n, dividede by 5
  base_5 <- (n-1) %/% 5
  
  # repeat for 15
  base_15 <- (n-1) %/% 15
  
  # get sum of all multiples of 3, 5, 15 using shortcut for sum of first n natural numbers
  sum_3 <- 3*(base_3)*(base_3+1)/2
  sum_5 <- 5*(base_5)*(base_5+1)/2
  sum_15 <- 15*(base_15)*(base_15+1)/2
  
  return(sum_3 + sum_5 - sum_15)
}

# Test
solution(10)
```

    ## [1] 23

``` r
# Answer
time_start <- Sys.time()
solution(1000)
```

    ## [1] 233168

``` r
time_end <- Sys.time()

# runtime
time_end - time_start 
```

    ## Time difference of 0.001240969 secs

``` r
# Answer
time_start <- Sys.time()
solution(100000000000000)
```

    ## [1] 2.333333e+27

``` r
time_end <- Sys.time()

# runtime
time_end - time_start 
```

    ## Time difference of 0.001164913 secs

## Time complexity

Constant time solution
