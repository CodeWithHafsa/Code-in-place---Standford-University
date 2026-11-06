## Continuous Random Variables

* [Probability For AI | Continuous Random Variables | Intro (Part 1 of 4)](https://youtu.be/kvE1jIfxnhI?si=_7J09urbJq__2cGZ)
* [Probability For AI | Continuous Random Variables | Uniform PDF (Part 2 of 4)](https://youtu.be/JLVoZtt9UW0?si=hCvF8S1sC6TDbQuV)
* [Probability For AI | Continuous Random Variables | Exponential, CDF (Part 3 of 4)](https://youtu.be/0b1x1-GiWkk?si=UOxOvuXGI6_5lnHn)
* [Probability For AI | Continuous Random Variables | Normal (Part 4 of 4)](https://youtu.be/oHhqSOvqg1I?si=98pKydg6Ef27ALAb)

---

### Question 01

Let X be the number of years until the next big (magnitude 8+) earthquake. On average, 1.2 big earthquakes happen each year, so X ∼ Exp (1.2). What is the probability that there are no big earthquakes for the next three years? In other words, what is the probability that the time until the next big earthquake is more than 3 years?

#### Solution
Since $X \sim \text{Exp}(1.2)$, we use the exponential distribution's survival function:

$$P(X > t) = e^{-\lambda t}$$

Where:
* $\lambda = 1.2$ earthquakes per year
* $t = 3$ years

**Step 1: Substitute the values**
$$P(X > 3) = e^{-1.2(3)}$$

**Step 2: Calculate**
$$P(X > 3) = e^{-3.6} \approx 0.0273$$

**Final Answer**
$$P(X > 3) \approx 0.0273 = 2.73\%$$

There is approximately a **2.73% probability** that no magnitude 8+ earthquake occurs in the next three years.

#### Answer: 0.0273

---

### Question 02

A coral reef in Florida has been tracking their average monthly ocean water temperature for years. Recently, the average August water temperature has been 29.87 C (degrees in Celsius), with a standard deviation of 0.5 C. What is the probability of the reef experiencing a temperature greater than 30 C next August?

#### Solution

Assuming the August water temperatures follow a normal distribution, we can calculate the probability using a $z$-score.

**Step 1: Identify the given values**
* Mean: $\mu = 29.87^\circ\text{C}$
* Standard deviation: $\sigma = 0.5^\circ\text{C}$
* Temperature of interest: $X = 30^\circ\text{C}$

We want to find $P(X > 30)$.

**Step 2: Calculate the $z$-score**

Use the formula:
$$z = \frac{X - \mu}{\sigma}$$

Substitute the values:
$$z = \frac{30 - 29.87}{0.5} = \frac{0.13}{0.5} = 0.26$$

**Step 3: Find the probability**

Using the standard normal distribution table:
$$P(Z < 0.26) \approx 0.6026$$

Since we want the probability of a temperature greater than $30^\circ\text{C}$, subtract from 1:
$$P(X > 30) = 1 - 0.6026$$
$$P(X > 30) = 0.3974$$

**Final Answer**

$$P(X > 30) \approx 0.3974 = 39.74\%$$

There is approximately a **39.74% probability** that the reef's average August water temperature will exceed $30^\circ\text{C}$ next August, assuming temperatures are normally distributed.

#### Answer: 0.3974
