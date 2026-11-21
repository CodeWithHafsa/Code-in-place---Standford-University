## Who moves the weight?

Two spam emails each have feature $x=1$. The model gives email A a 0.9 chance of spam and email B a 0.2 chance. On a gradient ascent step, which email changes the weight more?

A. Email A

B. Email B

C. Both the same

![alt text](Images/image-106.png)

#### **Answer:**  Email B
---

**Explanation**

**The idea**
Gradient ascent learns most from the biggest mistakes.

**Solution**

Email B. Both are spam, so $y=1$. A's error is 
$1−0.9=0.1$, while B's is $1−0.2=0.8$, eight times as big. The model learns most from the examples it gets most wrong.

