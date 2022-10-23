## PDF vs. CDF
[ref1](https://www.graduatetutor.com/statistics-tutor/probability-density-function-pdf-and-cumulative-distribution-function-cdf/#:~:text=The CDF is the probability,value exactly equal to x.) [ref2](https://stats.libretexts.org/Courses/Saint_Mary's_College_Notre_Dame/MATH_345__-_Probability_(Kuter)/4%3A_Continuous_Random_Variables/4.1%3A_Probability_Density_Functions_(PDFs)_and_Cumulative_Distribution_Functions_(CDFs)_for_Continuous_Random_Variables) [psu_course_ref3](https://online.stat.psu.edu/stat414/lesson/14/14.1) [ref4](https://web.stanford.edu/class/archive/cs/cs109/cs109.1192/handouts/pythonForProbability.html) 

- PDF: the probability density function, return the probability that a random variable will take a value exactly equal to x.
- CDF: the cumulative distribution function, return the probability that a random variable will take a value less than or equal to x.
- PDF is not relevant in the case of continuous distributions, but for a discrete random variable
> [!info] 
> The PDF, denoted $f$, of a continuous random variable $x$ satisfies the following:
> 1. $$f(x)\ge 0$, for all $x\in \mathbb{R}$$
> 2. $$f$$ is piecewise continuous
> 3. $\int_{-\infty}^\infty f(x)dx = 1$
> 4. $P(a\le x\le b) = \int_b^a f(x)dx$

> [!Info]
The CDF, denoted $F$, of a continuous random variable $x$, let $x$ have pdf $f$, then the cdf $F$ is given by $$F(x)=P(X\le x)=\int_{-\infty}^x f(t)dt, \quad\text{for}\quad x \in\mathbb{R} $$

> [!Info]
> The pdf can be found by differentiating the cdf:
> $$f(x) = \frac{d}{dx}[F(x)]$$



## Binomial distribution
[ref1](https://www.geeksforgeeks.org/python-binomial-distribution/)

$$(a+b)^n = a^n + \binom{n}{1}a^{n-1}b^1 + \binom{n}{2}a^{n-2}b^2+ ... +\binom{n}{k}a^{n-k}b^k + ... + b^n$$

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$
$$P(k:p,n)=\binom{n}{k}(p)^k(1-p)^{(n-k)}.\quad for\quad k = 0,1,2,...,n$$

- discrete 


## Poisson distribution
[zedstats](https://www.youtube.com/watch?v=cPOChr_kuQs&list=PLTNMv857s9WVzutwxaMb0YZKW7hoveGLS&index=3) [NIST](https://www.itl.nist.gov/div898/handbook/eda/section3/eda366j.htm)
- discrete, e.g. number of cars passing a tollgate in one hour
- discribe the number of events occuring in a fixed time interval or region of opportunity
- requires only one parameter, $\lambda$
- the rate at which events occur is constant
- the occurrence of one event does not affect the occurrence of a subsequent event (events are independent)
- $$P(x;\lambda) = \frac{e^{-\lambda}\lambda^x}{x!},\quad for \quad x=0,1,2,3,...$$![[Pasted image 20220603085028.png]] PMF
## Exponential distribution
[zedstats](https://www.youtube.com/watch?v=2kg1O0j1J9c&list=PLTNMv857s9WVzutwxaMb0YZKW7hoveGLS&index=5)
- the "inverse" of Poisoon, e.g. number of hours between car arrivals
- time per single event
- events must be independent and occur at a constant rate

$$F(x)=P(X < x)=1-e^{-x\lambda}$$


## Hypergeometric distribution
> [!Info] is a discrete probability distribution that describes the probability of $k$ successes in $n$ draws, without replacement, froma finite population of size $N$ that contains exactly $K$ objects with that feature, wherein each draw is either a success or a failure.

[zedstats](https://www.youtube.com/watch?v=upVJ4YqTlC4&list=PLTNMv857s9WVzutwxaMb0YZKW7hoveGLS&index=4)
- Binomial distribution without replacement
- N: total population size; A: total items of interest in population; n: sample size
- PMF: $$P(X = x)=\frac{\binom{A}{x}\binom{N-A}{n-x}}{\binom{N}{n}}$$





## Chi-squared distribution
[zedstatistics](https://www.youtube.com/watch?v=80ffqpZdKiA)
$$Q=\sum_{i=1}^{k}Z_i^2 \sim\chi_k^2, \quad\text{where}\quad Z_i\sim N(0,1) $$
Mean = $k$, Variance = $2k$

> [!Info] **$\chi^2$-distribution** with $k$ degrees of freedom is the distribution of a sum of the squares of $k$ independent standard normal random variables.


Categorical $\chi^2$ tests
- Goodness of fit test
	- $\chi^2=\sum_{i=1}^k\frac{(o_i-e_i)^2}{e_i}\sim\chi_{df}^2$
	- reject $H_0$ rule in excel $\chi^2\gt$ CHISQ.INV(0.95,df)
	- $df = k-1$	 
- Tests for independence [zedstats](https://www.youtube.com/watch?v=NTHA9Qa81R8)
	- Joint distribution over 2 variables
		- If independent, $P(A\cap B) = P(a)\times P(B)$
		- $df=(df_{variable1}-1)(df_{variable2}-1)$


# Survial analysis
- measuring survival time,"time-to-event" analysis
- visualising survival rates, e.g. Kaplan Meier (KM) curve, non-parametric
- applications: time to death, device failure, re-admission, component failure, device obsolescence, patent approval, business failure, staff churn, staff promotion, divorce, second child, first substitution (soccer)
## Censoring and truncation
- censoring occurs when we don't know the exact time-to-event for an included observation
	- type of censoring
		- left: time-to-event is less than some value $t_i\lt x$
		- interval: time=-to-event is between two values $x_1\lt t_i\lt x_2$
		- right: time-to=event is greater than some value $x\lt t_i$
- truncation occurs when observations are excluded by virtue of their time-to-event
	- Left or right


## Somers' D
> [!tip] a measure of agreement between pairs of ordinal variables. Ordinal variables are ordered, like best to worst or smallest to greatest.
> A measure of agreement tells you something about how two pairs of variables are connected. This connectivity is defined by concordance (match) and discordance (don't match).
> The range for Somers' D is -1 to 1, indicating from all pairs disagree to all pairs agree.

$N_s$ the number of concordant pairs
$N_r$ the number of disconcordant pairs
$n$  the sample size
$T$ the total number of possible paris, $T=n(n-1)/2$
$T_I$ the number of pairs with tied ranks on the independent variable
$T_D$ the number of pairs with tied ranks on the dependent variable
$m$ the minimum of the number of rows or columns
### Meausres of association
$$\gamma = \frac{N_s-N_r}{N_s+N_r}$$
$$\tau_\alpha =\frac{N_s-N_r}{T}$$
$$Somer' d=\frac{N_s-N_r}{N_s+N_r+T_D}$$

