## One last update

Before this course, you could solve a hard probability puzzle with chance 0.2. After it, with chance 0.8. A friend thinks it is 50/50 whether you took the course. Then they watch you solve **3 hard puzzles in a row**, independently.

What chance should your friend now give that you took the course? Give your answer to three decimal places.

#### **Answer:** 0.9846
---

**Explanation**

**The idea**
Evidence that is far more likely under one explanation moves you fast.

**Solution**

By Bayes' rule,
$$
\frac{0.5 × 0.8^3}{0.5 × 0.8^3 + 0.5 × 0.2^3} = \frac{0.256}{0.256 + 0.004} ≈0.985.
$$

 
Three solves are 64 times as likely with the course as without it, so your friend's belief moves from 50% to over 98%.

That is the whole course in one puzzle: a prior, a likelihood, and evidence that updates a belief. Thank you for puzzling with us.