## The Test Train Split

* [Train/Test](https://youtu.be/noBuSrWNPzM?si=VyrGXdmzQcnI00QR)


### Example 01

On the test set, logistic regression is right on 72% of the days. Persistence, which predicts that tomorrow will be like today, is right on 71%.\
What do these two numbers tell you about logistic regression?

* It is only a little better than a simple baseline
* It works well, because 72% is far above 50%
* It is much better than the persistence baseline

**Explanation:**

Here's why:
* Logistic regression accuracy: 72%
* Persistence baseline accuracy: 71%
* Improvement: Just 1 percentage point

This means logistic regression performs only slightly better than simply predicting that tomorrow's weather will be like today's.

**Correct Answer:** \
It is only a little better than a simple baseline

---

### Example 02

Two models, each scored on its training set and on the test set: \
Nearest neighbor: right on 100% of the training set and 63% of the test set. \
Logistic regression with coast features: right on 79% of the training set and 78% of the test set. \
Which one is overfitting?

* Logistic regression with coast features, because it is worse on the training set
* Neither one, because both are right on more than half of the days in the test set
* Nearest neighbor, because it is much better on its training set than on the test set

**Explanation:**
Here's why:

* **Nearest neighbor:** 100% training accuracy vs. 63% test accuracy. That's a huge gap!
* **Logistic regression:** 79% training accuracy vs. 78% test accuracy. Very little gap.

Key lesson: Overfitting happens when a model memorizes the training data but struggles to make accurate predictions on new, unseen data.

**Correct Answer:** \
Nearest neighbor, because it is much better on its training set than on the test set.