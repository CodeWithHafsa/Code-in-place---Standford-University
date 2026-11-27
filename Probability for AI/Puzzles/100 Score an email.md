## Score an email

A spam filter weighs each feature, adds them up, and adds $−3$. That total is the weighted sum $z$, and the chance of spam is 
$σ(z)= \frac{1}{1+e^{-z}}$.

What chance of spam does it give this email? Give your answer to three decimal places.

![alt text](Images/image-96.png)

![alt text](Images/image-88.png)

#### **Answer:** 0.731
---

**Explanation**

**The idea**
Logistic regression: weigh the features, add them up, squash.

**Solution**

The weighted sum is
$$z=−3+2(1)+0.5(4)+(−2.5)(0)=1
$$,

so the chance of spam is $σ(1)= \frac{1}{1+e^{-1}} ≈ 0.731$.

If the same email had come from a contact, the weighted sum would drop to $−1.5$ and the chance to about $0.18$.
