Another problem that is not a natural fit for evolutionary algorithms. The fitness is based on the amount of consecutive bits starting from the left-most position.

NOTES:

- I stuck with the tournament selection I used from the [Zero Trap](https://github.com/mikejmcguirk/zero_trap) problem (use the tournament to halve the population, all tournaments are two participants chosen at random, all population members get to participate). If you base tournament selection probabilistically on the strongest facing the weakness, this produces more consistent iteration counts than random selection, but doesn't really seem to move the average. I kept the random tournament selection because it seems more generalizable to problems that require more exploration
- Reproduction still needs to be probabilistically based on fitness. The solution never converges if it does not
- For mutation rate, I stuck with individualized mutation rates, but added normalized exponential scaling. In practice, I found that with linear scaling, a population of 100 takes ~500 iterations to find the solution for a 150 length string. With properly tuned k for an exponential scale, I can get the average down to ~450. Though, looking at the outputs for the fitness ratios and the mutation rates, the scaling is fairly close to linear anyway
- Doing a few test runs, a global mutation rate of 0.25 does about as well on average, but with higher variance

IDEAS:

- This problem might be suited for a memetic algorithm, since a memetic algorithm might be able to identify the mutation hot-spots that lead to improvement
