## Avoid your neighbors

The integers 1, 2, 3, 4, 5, 6 are arranged in a random order, with every order equally likely. What is the chance that no two even numbers are next to each other? Give your answer to three decimal places.

#### **Answer:**  0.2

---

**Explanation**

**The idea**
Place the odd numbers first; the even numbers must go in the gaps.

**Solution**

Place the odd numbers first: they can go in $3×2×1=6$ orders. That leaves 4 gaps: before, between and after them. The even numbers each need a different gap, so there are 4 ways to choose their 3 gaps and 6 orders for 2, 4 and 6.

That gives $6×4×6=144$ good orders out of $6!=720$ equally likely ones, so the chance is $\frac{144}{720}=0.2$.

