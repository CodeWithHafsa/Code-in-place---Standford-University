## Maximum Likelihood 

* [Maximum Likelihood Estimation](https://youtu.be/TQ69GM3T_pc?si=yPEinawvyZjzefds)

### Example 01: Three dark patches

Three dark patches of the night sky hold 2, 3 and 5 stars. The number of stars in a dark patch is Poisson with average θ, and the patches are independent of each other.

Write the likelihood of θ for these three counts, in words or in symbols, and say why it has that form.

---

#### Answer

Each patch has a Poisson distribution with average $\theta$, and the three patches are independent.

The likelihood is

$$
L(\theta)=P(X_1=2)P(X_2=3)P(X_3=5)
$$

Using the Poisson probability formula, $P(X=k)=\frac{e^{-\theta}\theta^k}{k!}$, we get

$$
L(\theta)=
\frac{e^{-\theta}\theta^2}{2!}
\cdot
\frac{e^{-\theta}\theta^3}{3!}
\cdot
\frac{e^{-\theta}\theta^5}{5!}
$$

Simplifying,

$$
\boxed{L(\theta)=\frac{e^{-3\theta}\theta^{10}}{2!\,3!\,5!}}
$$

Why does it have this form?

- Each patch contributes its own Poisson probability.
- Because the patches are independent, we multiply their probabilities.
- The exponents of $\theta$ add up: $2+3+5=10$.
- The three factors of $e^{-\theta}$ combine to give $e^{-3\theta}$.

The likelihood describes how plausible the observed counts $2,3,5$ are for different values of $\theta$.

---

### Example 02: Why the log?

We climb the log of the likelihood (the score) instead of the likelihood itself.

Why do we take the log? And does taking the log change which θ wins? Answer both.

----

### Answer

**1. Why do we take the log?**

We take the log of the likelihood because it turns multiplication into addition, making the expression easier to work with mathematically.

Our likelihood is

$$
L(\theta)=\frac{e^{-3\theta}\theta^{10}}{2!\,3!\,5!}
$$

Taking the natural logarithm gives the log-likelihood:

$$
\ell(\theta)=\log L(\theta)
$$

Using log rules:

$$
\boxed{\ell(\theta)=-3\theta+10\log\theta-\log(2!\,3!\,5!)}
$$

This form is easier to differentiate and optimize than the original likelihood.

**2. Does taking the log change which $\theta$ wins?**

No\! The logarithm is a strictly increasing function, so a larger likelihood always corresponds to a larger log-likelihood.

For any two candidate values $\theta_1$ and $\theta_2$,

$$
L(\theta_1)>L(\theta_2)
$$

if and only if

$$
\log L(\theta_1)>\log L(\theta_2)
$$

Therefore, both functions have the same maximizing value of $\theta$.

For this example, differentiate the log-likelihood:

$$
\ell'(\theta)=-3+\frac{10}{\theta}
$$

Set the derivative to zero:

$$
-3+\frac{10}{\theta}=0
$$

$$
\frac{10}{\theta}=3
$$

$$
\boxed{\hat{\theta}=\frac{10}{3}\approx3.33}
$$

So the maximum likelihood estimate is approximately $3.33$ stars per patch.

In short: We take the log to simplify calculations, and because the log preserves the ordering of likelihood values, it does not change which $\theta$ maximizes the likelihood.

---

### Example 03: Model first

You want a computer to find θ for the three star counts (2, 3 and 5). What do you have to write before you ask it for anything? Write it.

---

#### Answer

Before writing the likelihood, you must define the probabilistic model for the star counts.

Write:

$$
\boxed{X_i\overset{\text{ind}}{\sim}\operatorname{Poisson}(\theta),\quad i=1,2,3}
$$

where:

- $X_1,X_2,X_3$ are the star counts in the three patches.
- $\theta>0$ is the average number of stars per patch.
- The counts are independent and each follows a Poisson distribution with mean $\theta$.

The observed data are:

$$
\boxed{(x_1,x_2,x_3)=(2,3,5)}
$$

This defines the model the computer needs before you ask it to construct the likelihood and estimate $\theta$.

---