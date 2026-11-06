## Logistic Regression

* [Logistic Regression](https://youtu.be/PFf2_nGUZpo?si=X9A5SsXpW7VqbFcK)

### Example 01

The rain machine looks at today’s weather and computes a weighted sum: −1.90. Then it puts −1.90 through the sigmoid.
What comes out?

* The number −1.90
* 0.13: a 13% chance of rain tomorrow
* 0.87: an 87% chance of rain tomorrow

**Explanation:**

Correct answer: 0.13The sigmoid formula is:

$$
\sigma(x)=\frac{1}{1+e^{-x}}
$$

Substitute −1.90:

$$
\sigma(-1.90)=\frac{1}{1+e^{1.90}}\approx 0.13
$$

So the output is 0.13, meaning a 13% chance of rain tomorrow.

**Correct Answer:** \
0.13: a 13% chance of rain tomorrow

---

### Example 2

How does a computer choose the weights in logistic regression?

* A person sets each weight by hand
* It makes the weighted sum as big as possible
* It changes the weights in small steps, and each step makes the data more likely. This is called climbing the log likelihood.

**Correct Answer:** \
It changes the weights in small steps, and each step makes the data more likely. This is called climbing the log likelihood.

