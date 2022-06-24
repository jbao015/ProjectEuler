# Problem

The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of the number 600851475143 ?

# Solution 1

Many ways to solve this problem. One such way with O(nlog(n)) time
complexity is using the sieve of Erasthotenes.

The base approach is pretty wasteful memory-wise, but there are many
ways to refine the approach

``` r
solution <- function(n) {
  sieve_length <- floor(sqrt(n))
  
  # define an array of length sqrt(n)
  sieve <- rep(FALSE, sieve_length)
  
  # mark index and 1 as not prime
  sieve[1] <- TRUE
  
  # start with assumption n is prime. If not, we reduce the search space.
  largest_prime_factor <- n
  
  i <- 2
  
  while (i < sieve_length) {
    # skip nonprimes
    if (sieve[i]) { 
      i <- i + 1
      next 
    }
    
    # starting from i^2, mark all multiples of 2 in the sieve as TRUE
    index <- i^2 
    while(index <= sieve_length) {
      sieve[index] <- TRUE
      index <- index+i
    }
    
    # check to see if this prime is a divisor
    while (largest_prime_factor %% i == 0 && largest_prime_factor!=i) { 
      largest_prime_factor <- largest_prime_factor %/% i
      sieve_length <- floor(sqrt(largest_prime_factor))
    }
    
    i <- i + 1
  }
  largest_prime_factor
}

# testing
solution(10)
```

    ## [1] 5

``` r
solution(91)
```

    ## [1] 13

``` r
solution(64)
```

    ## [1] 2

``` r
# Answer
time_start <- Sys.time()
solution(600851475143)
```

    ## [1] 6857

``` r
time_end <- Sys.time()

# runtime
time_end - time_start 
```

    ## Time difference of 0.07250381 secs

## Time complexity

General Sieve of Eratosthenes is O(nlog(n))
