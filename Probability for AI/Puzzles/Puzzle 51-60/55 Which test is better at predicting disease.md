## Which test is better at predicting disease?

Suppose two medical tests are used in two different clinics.

* Test A catches 95% of patients who have disease A, and correctly clears 90% of patients who don't. In its clinic, 20% of patients have disease A.
* Test B catches 80% of patients who have disease B, and correctly clears 80% of patients who don't. In its clinic, 80% of patients have disease B.

A patient tests positive. For which test is a positive result more likely to mean the patient really has the disease?

A. Test A \
B. Test B \
C. Both are equally good \
D. Both are bad. We need better tests.

![alt text](Images/image-46.png)

#### **Answer:**  OptionB: Test B

---

**Explanation**

**The idea**
How common a disease is drives what a positive test means, not just how good the test is.

**Solution**

For each test, $P(disease∣+)= \frac{P(+∣disease)P(disease)}{P(+)}$.

Test A: $\frac{0.95×0.2}{0.95×0.2+0.10×0.8} ≈
0.70$

Test B: $\frac{0.8×0.8}{0.8×0.8+0.2×0.2} = \frac{0.64}{0.68} ≈ 0.94$.

Test B is worse at catching and clearing, yet its positive result means more, because in its clinic most patients have the disease, so there are few healthy people to set off false alarms.