## Student v/s AI

**The scenario**

An AI detector flags a student's assignment.

* 10% of students actually use AI to cheat.
* The detector correctly flags AI-generated work 90% of the time.
* It falsely flags human-written work 5% of the time.

**The question**

If an assignment is flagged, what is the probability that the student actually cheated?

A. 70%

B. 65%

C. 66.7%

#### **Answer:** Option C. 66.7%
---

**Explanation**

**The idea**
A 90%-accurate detector does not mean a flagged student has a 90% chance of cheating. Around one-third of flagged students may be innocent.

**Solution**

1. Total AI users: $10\%×1000=100$
2. Correctly flagged: $90\%×100=90$
3. Non-AI users: $900$
4. Falsely flagged: $5\%×900=45$
5. Total flagged: $90+45=135$

Calculate:

$$P(Cheated∣Flagged)= \frac{90}{135}×100$$
