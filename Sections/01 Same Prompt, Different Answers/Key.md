# Section 1 
## Key: Same Prompt, Different Answers?

### Question: Probability of Two Different Outputs

Our toy model finishes the prompt "A sleepy robot dreams about" with one of five outputs. If we prompt it twice, what is the probability that the model produces two different outputs?

| $i$ | Output | Probability, $p_i$ |
| :---: | :--- | :---: |
| 1 | electric sheep | 0.44 |
| 2 | counting stars | 0.20 |
| 3 | sample spaces | 0.14 |
| 4 | counting outcomes | 0.13 |
| 5 | robot puppies | 0.09 |

**Answer:** Approximately **0.72 (72%)**.

---

### Step 1: Use the Complement
Two different outputs can happen in many ways: there are 20 ordered pairs. Two matching outputs can happen in only 5 ways. So it is easier to find the probability that the outputs are the same, then subtract from 1.

### Step 2: Name the Events
* Let $E$ be the event that both calls produce the same output.
* Let $B_i$ be the event that both calls produce output $i$.

### Step 3: Both Calls Give the Same Output $i$
Each call is a separate random sample, so the two calls are independent and we can multiply.

For "counting outcomes" (output 4):
$$P(B_4) = p_4 \cdot p_4 = 0.13 \cdot 0.13 = 0.0169$$

The same idea works for every output:
$$P(B_i) = p_i \cdot p_i = p_i^2$$

### Step 4: Add Up the Ways to Match
The events $B_1$ through $B_5$ are mutually exclusive: both calls cannot be output 1 and output 2 at the same time. So we can add their probabilities:

$$
\begin{aligned}
P(E) &= P(B_1 \cup B_2 \cup B_3 \cup B_4 \cup B_5) \\
&= P(B_1) + P(B_2) + P(B_3) + P(B_4) + P(B_5) \\
&= p_1^2 + p_2^2 + p_3^2 + p_4^2 + p_5^2 \\
&= 0.44^2 + 0.20^2 + 0.14^2 + 0.13^2 + 0.09^2 \\
&= 0.1936 + 0.0400 + 0.0196 + 0.0169 + 0.0081 \\
&= 0.2782
\end{aligned}
$$

### Step 5: Take the Complement
Two different outputs are the opposite of two matching outputs:

$$
\begin{aligned}
P(E^C) &= 1 - P(E) \\
&= 1 - \sum_{i} p_i^2 \\
&= 1 - 0.2782 \\
&= 0.7218 \approx 0.72
\end{aligned}
$$

Even this tiny five-output model gives two different answers almost three times out of four. Getting different answers is normal behavior, not a glitch.

---

### A Common Mistake
Treating all five outputs as equally likely gives:
$$1 - \frac{1}{5} = 0.8$$

That only works when every $p_i$ is 0.2. Here, "electric sheep" is much more likely than the others, so matching happens more often and the answer is lower.

---

## Extra Time

### Robot Puppies
Each call says "robot puppies" with probability 0.09. How many calls are needed until the probability of seeing it is more than 50%?

Let $R_i$ be the event that call $i$ says "robot puppies." Seeing it at least once is the complement of never seeing it, and the calls are independent:

$$
\begin{aligned}
P(\text{at least one}) &= 1 - P(R_1^C \cap \dots \cap R_n^C) \\
&= 1 - P(R_1^C) \dots P(R_n^C) \\
&= 1 - 0.91^n
\end{aligned}
$$

With 7 calls, the chance is approximately 0.48, and with 8 calls, it is approximately 0.53.

**Answer:** **8 calls**.

### Temperature
At temperature $T$, the probability of output $i$ becomes:

$$q_i = \frac{p_i^{1/T}}{\sum_{j} p_j^{1/T}}$$

At $T = 0.5$, square each probability, then rescale so they add up to 1.

On the slide, the probabilities are for the first word, so "counting" gets $0.20 + 0.13 = 0.33$:

$$q_{\text{electric}} = \frac{0.44^2}{0.44^2 + 0.33^2 + 0.14^2 + 0.09^2} \approx 0.59$$

A low temperature makes the most likely output even more likely, so two calls match more often. A high temperature evens out the probabilities, so the outputs differ more often.
