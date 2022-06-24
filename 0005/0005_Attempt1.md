# Problem

2520 is the smallest number that can be divided by each of the numbers
from 1 to 10 without any remainder.

What is the smallest positive number that is evenly divisible by all of
the numbers from 1 to 20?

# Solution 1

``` r
solution <- function(n) {
  # Essentially, we want to multiply numbers together and remove numbers that are factors of both
  contributions <- 1:n
  running_prod <- 1
  
  for (i in 2:n) {
    # first, if i is 1, that means that this number i has nothing to contribute
    if (contributions[i]==1) { next }
    # for each item in the remaining indices, divide out that factor since it has already been contributed
    j <- i + 1
    while (j <= n) {
      # print(j)
      if (contributions[j] %% contributions[i] ==0 ) { contributions[j] <- contributions[j]/contributions[i]}
      j <- j + 1
    }
    # print(contributions)
    running_prod <- running_prod * contributions[i]
  }
  running_prod
}


# Test
solution(2) # should be 2
```

    ## [1] 2

``` r
solution(3) # should be 6
```

    ## [1] 6

``` r
solution(4) # should be 12
```

    ## [1] 12

``` r
solution(6) # should be 60
```

    ## [1] 60

``` r
solution(8) # should be 840
```

    ## [1] 840

``` r
solution(10) # should be 2520
```

    ## [1] 2520

``` r
# Answer
time_start <- Sys.time()
solution(20)
```

    ## [1] 232792560

``` r
time_end <- Sys.time()

# runtime
time_end - time_start
```

    ## Time difference of 0.001132965 secs

``` r
# Answer
time_start <- Sys.time()
solution(200)
```

    ## [1] 3.372936e+89

``` r
time_end <- Sys.time()

# runtime
time_end - time_start
```

    ## Time difference of 0.004018784 secs

## Time complexity

This algorithm is kinda inefficient because of the sheer number of
dividing. It is similar to the sieve of erastothenes so likely nlog(n)
time complexity.
