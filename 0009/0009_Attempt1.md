# Problem

A Pythagorean triplet is a set of three natural numbers,
*a* \< *b* \< *c*
, for which, *a*<sup>2</sup> + *b*<sup>2</sup> = *c*<sup>2</sup> For
example, 3<sup>2</sup> + 4<sup>2</sup> = 9 + 16 = 25 = 5<sup>2</sup>.

There exists exactly one Pythagorean triplet for which a + b + c = 1000.
Find the product abc.

# Solution 1

We know that *a* + *b* + *c* = 1000 and that
*a*<sup>2</sup> + *b*<sup>2</sup> = *c*<sup>2</sup> so therefore:

(*a*+*b*+*c*)<sup>2</sup> = *a*<sup>2</sup> + *b*<sup>2</sup> + *c*<sup>2</sup> + 2*a**b* + 2*a**c* + 2*b**c* = 2*c*<sup>2</sup> + 2*a**b* + 2*a**c* + 2*b**c* = 1, 000, 000

*c*<sup>2</sup> + *a**b* + *a**c* + *b**c* = 500, 000

*a*(*b*+*c*) + *c*(*b*+*c*) = 500, 000
(*a*+*c*)(*b*+*c*) = 500, 000

500,000 has a lot of factors but we can narrow down the candidates by
using the fact that $ a \< b \< c $ which rules out some combinations
like 2 and 250,000 since that would imply that $ c = 1$ and $b = 249,000
$ which contradicts the inequality. We also know there is only one
solution, so we can start with pairs of multiplicands close to the
square root of 500,000 (\~707) which has a prime factorization of
5^6\*2^5 and will arrive quickly at the answer.

Starting from $ 625 \* 800 $ which implies that $ c = 625 + 800 - 1000 =
425$, $ a = 200$, and *b* = 375. This satisfies the inequality, and a
quick check will show that it satisfies the other requirements as well

``` r
425 + 200 + 375 # should be 1000
```

    ## [1] 1000

``` r
425^2 - 200^2 - 375 ^ 2 # should be 0
```

    ## [1] 0

``` r
# product/answer
200*425*375
```

    ## [1] 31875000
