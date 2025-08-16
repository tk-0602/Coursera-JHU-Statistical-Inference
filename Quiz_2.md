### Question 1

What is the variance of the distribution of the average an IID draw of n
observations from a population with mean *μ* and variance
*σ*<sup>2</sup>.

### Answer

    $$
    \text{Var}(\bar{X}) = \bf{\frac{\sigma^2}{n}}
    $$

### Question 2

Suppose that diastolic blood pressures (DBPs) for men aged 35-44 are
normally distributed with a mean of 80 (mm Hg) and a standard deviation
of 10. About what is the probability that a random 35-44 year old has a
DBP less than 70?

### Answer

    pnorm(70, mean = 80, sd = 10, lower.tail = TRUE, log.p = FALSE)

    ## [1] 0.1586553

### Question 3

Brain volume for adult women is normally distributed with a mean of
about 1,100 cc for women with a standard deviation of 75 cc. What brain
volume represents the 95th percentile?

### Answer

    qnorm(0.95, mean = 1100, sd = 75, lower.tail = TRUE, log.p = FALSE)

    ## [1] 1223.364

### Question 4

Refer to the previous question. Brain volume for adult women is about
1,100 cc for women with a standard deviation of 75 cc. Consider the
sample mean of 100 random adult women from this population. What is the
95th percentile of the distribution of that sample mean?

### Answer

    standard_err <- 75 / sqrt(100)
    qnorm(0.95, mean = 1100, sd = standard_err, lower.tail = TRUE, log.p = FALSE)

    ## [1] 1112.336

### Question 5

You flip a fair coin 5 times, about what’s the probability of getting 4
or 5 heads?

### Answer

$\binom{n}{k} p^{k} (1 - p)^{n - k}$, where $p = \frac{1}{2}$, *n* = 5
and *k* = 4 or *k* = 5 for 4 or 5 heads, respectively, such that

    $$
    \begin{equation}
    \Rightarrow \binom{5}{4} \left( \frac{1}{2} \right) ^{4} \left( 1 -  \frac{1}{2} \right) ^{1} + \binom{5}{5} \left( \frac{1}{2} \right) ^{5} \left( 1 - \frac{1}{2} \right) ^{0} \\
    \Rightarrow \frac{5}{2^{5}} + \frac{1}{2^{5}} \approx \bf{19\%}
    \end{equation}
    $$

    n <- 5
    p <- 0.5
    sum(dbinom(4:5, size = n, prob = p))

    ## [1] 0.1875

### Question 6

The respiratory disturbance index (RDI), a measure of sleep disturbance,
for a specific population has a mean of 15 (sleep events per hour) and a
standard deviation of 10. They are not normally distributed. Give your
best estimate of the probability that a sample mean RDI of 100 people is
between 14 and 16 events per hour?

### Answer

    standard_err <- 10 / sqrt(100)
    pnorm(16, mean = 15, standard_err) - pnorm(14, mean = 15, standard_err)

    ## [1] 0.6826895

### Question 7

Consider a standard uniform density. The mean for this density is .5 and
the variance is 1 / 12. You sample 1,000 observations from this
distribution and take the sample mean, what value would you expect it to
be near?

### Answer

With the Law of Large Numbers (LLN), the sample mean should be near the
population mean of 0.5.

Alternatively, simulate this problem in R and generate 1000 random
numbers from this normal distribution to then calculate their mean:

    mu <- 0.5
    var <- 1/12
    n <- 1000
    mean(rnorm(n, mean = mu, sd = sqrt(var)))

    ## [1] 0.4988004

### Question 8

The number of people showing up at a bus stop is assumed to be Poisson
with a mean of 5 people per hour. You watch the bus stop for 3 hours.
About what’s the probability of viewing 10 or fewer people?

### Answer

    ppois(10, lambda = 3 * 5)

    ## [1] 0.1184644
