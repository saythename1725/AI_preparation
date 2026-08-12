# 24. Why can't we use Regression Metrics like MSE and R² for Classification Problems?

## The main idea

Regression and classification solve different types of problems.

In regression, we predict a continuous value:

```text
House Price = ₹75,00,000
Temperature = 32.5°C
```

In classification, we predict a category:

```text
Spam / Not Spam
Fraud / Not Fraud
Cat / Dog / Bird
```

Because the meaning of the output is different, the way we measure errors should also be different.

---

## Why is R² not suitable?

R² measures how much variation in a continuous target is explained compared with predicting the mean.

But class labels are categories.

For example:

```text
Cat = 0
Dog = 1
Bird = 2
```

These numbers do not have a meaningful mathematical distance.

Predicting `1.9` instead of `2` does not mean we are "closer" to Bird in the same way that predicting ₹90 instead of ₹100 is closer.

So concepts such as variance explained are generally not meaningful for classification labels.

---

## What about MSE?

Technically, we can calculate MSE on encoded class labels, but it gives misleading information.

Suppose:

```text
Actual = Dog = 1

Model A predicts Cat = 0
Model B predicts Bird = 2
```

MSE treats both errors numerically.

But class labels do not have a natural order or distance.

Similarly:

```text
Cat = 0
Dog = 1
Bird = 2
```

The model should not consider predicting Bird when the answer is Cat as "twice as bad" as predicting Dog.

---

## Classification metrics are designed differently

Classification problems care about questions like:

* Did we predict the correct class?
* How many positive cases did we miss?
* How many false alarms did we generate?
* How confident was the model in its prediction?

That is why we use:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* PR-AUC
* Log Loss

---

## Important nuance

MSE can be used on predicted probabilities in some specific contexts, but for classification, losses such as **Binary Cross-Entropy** and **Cross-Entropy Loss** are generally better aligned with probabilistic classification.

---

## How I would explain it in an interview

> Regression metrics are designed for continuous numerical targets where the magnitude of an error has a meaningful interpretation. In classification, class labels are categories, so the mathematical distance between labels is usually meaningless. That's why we use classification metrics such as Precision, Recall, F1 Score, and Log Loss, which better reflect classification performance and predicted probabilities.

---

# 25. What are the Mathematical Differences Between Regression and Classification?

The main mathematical difference comes from the **type of output we want to model**.

---

## Regression

Regression predicts a continuous value.

For example:

```text
x → f(x) → 75.4
```

A Linear Regression model might look like:

[
y = w_1x_1 + w_2x_2 + b
]

The output can theoretically take any value within a continuous range.

The model usually tries to minimize the difference between:

```text
Actual value
        vs
Predicted value
```

---

## Classification

Classification predicts probabilities or class assignments.

For binary classification:

```text
x → model → probability → class
```

For example:

```text
Customer → 0.87 probability of default
```

Then, depending on a threshold:

```text
Probability > 0.5 → Default
Probability ≤ 0.5 → No Default
```

A Logistic Regression model first calculates a linear score:

[
z = w_1x_1 + w_2x_2 + b
]

Then converts that score into a probability using a sigmoid:

[
P(y=1) = \frac{1}{1+e^{-z}}
]

---

## Another important difference: Decision Boundaries

Regression tries to find a function that predicts the numerical target.

Classification tries to separate regions belonging to different classes.

For example:

```text
          Class A
       ● ● ● ●

-------------------- Decision Boundary

       ▲ ▲ ▲ ▲
          Class B
```

The model learns where one class ends and another begins.

---

## How I would explain it in an interview

> Mathematically, regression models a continuous output, so the model tries to predict the actual numerical value and minimize numerical error. Classification usually models class probabilities and then converts those probabilities into class decisions using thresholds or maximum probability. Classification is therefore more focused on separating decision regions, while regression focuses on estimating continuous values.

---

# 26. How Does the Choice of Loss Function Affect Model Training in Regression vs Classification?

The loss function defines what the model considers a mistake.

This is extremely important because:

> The optimizer can only minimize the loss function we give it.

So choosing a loss function means deciding what type of errors the model should care about.

---

## In Regression

Suppose we predict:

```text
Actual = 100
Prediction = 90
```

The loss function measures the numerical difference.

Common choices include:

### MAE

[
|y-\hat{y}|
]

Every error is penalized proportionally.

---

### MSE

[
(y-\hat{y})^2
]

Large errors receive a much larger penalty.

For example:

```text
Error = 2  → Penalty = 4
Error = 10 → Penalty = 100
```

So MSE makes the model care more strongly about large mistakes.

---

## In Classification

Suppose the actual class is:

```text
Fraud = 1
```

Now compare these two predictions:

```text
Model A → Fraud probability = 0.51
Model B → Fraud probability = 0.99
```

Both may predict the correct class after applying a threshold.

But Model B is much more confident and assigns a much higher probability to the correct outcome.

A good classification loss should capture this difference.

That is why we commonly use **Cross-Entropy / Log Loss**.

---

## The important connection

The loss function shapes the optimization process.

```text
Loss Function
      ↓
Determines penalty for errors
      ↓
Determines gradients
      ↓
Determines parameter updates
      ↓
Affects what the model learns
```

---

## How I would explain it in an interview

> The loss function determines what type of mistakes the model is penalized for, so it directly affects the gradients and the way the model learns. In regression, MSE penalizes large numerical errors more heavily, while MAE treats errors proportionally. In classification, Cross-Entropy penalizes incorrect and overconfident probability predictions, which makes it more suitable for learning class probabilities.

---

# 27. What is Logistic Regression?

Despite its name, Logistic Regression is mainly a **classification algorithm**.

It is commonly used for binary classification.

For example:

```text
Will customer default?
Yes / No

Is this transaction fraudulent?
Yes / No
```

---

## How does it work?

Logistic Regression first calculates a linear combination of the features:

[
z = w_1x_1 + w_2x_2 + ... + b
]

But unlike Linear Regression, it does not use this value directly as the final prediction.

Instead, it passes the value through the **Sigmoid function**.

```text
Linear Score
      ↓
    Sigmoid
      ↓
Probability between 0 and 1
```

For example:

```text
z = 2.5

Sigmoid(z) = 0.92
```

The model predicts a 92% probability of the positive class.

---

## Converting probability into a class

We can apply a threshold:

```text
Probability ≥ 0.5 → Class 1
Probability < 0.5 → Class 0
```

But an important interview point is:

> The threshold does not always have to be 0.5.

For fraud detection, medical diagnosis, or credit risk, we may choose a different threshold depending on the cost of false positives and false negatives.

---

## Why is it called Logistic Regression?

Because the model performs regression on the **log-odds** of the probability.

The output is then transformed into a probability using the logistic or sigmoid function.

---

## How I would explain it in an interview

> Logistic Regression is a classification algorithm that first calculates a linear combination of the input features and then passes it through a sigmoid function to convert the output into a probability between 0 and 1. We can then apply a threshold to convert that probability into a class prediction.

---

# 28. Can Logistic Regression Be Used for Multi-class Classification?

Yes.

Although basic Logistic Regression is naturally used for binary classification, it can be extended to multiple classes.

The two main approaches are:

1. One-vs-Rest
2. Multinomial Logistic Regression

---

## 1. One-vs-Rest

Suppose we have:

```text
Cat
Dog
Bird
```

Instead of building one model that directly predicts all three classes, we create separate binary classifiers.

```text
Model 1 → Cat vs Not Cat

Model 2 → Dog vs Not Dog

Model 3 → Bird vs Not Bird
```

Each model gives a score or probability.

We select the class with the highest score.

---

## 2. Multinomial Logistic Regression

Instead of training multiple independent binary classifiers, the model directly learns probabilities for all classes.

For example:

```text
Cat  → 0.20
Dog  → 0.70
Bird → 0.10
```

The probabilities add up to 1.

This approach commonly uses the **Softmax function**.

---

## How I would explain it in an interview

> Yes, Logistic Regression can be extended to multi-class problems. One approach is One-vs-Rest, where we train one binary classifier for each class against all other classes. Another approach is multinomial Logistic Regression, which directly models the probabilities of all classes using Softmax.

---

# 29. What is One-vs-Rest?

One-vs-Rest, also called **One-vs-All**, is a strategy for converting a binary classifier into a multi-class classifier.

---

## Example

Suppose we want to classify an image as:

```text
Cat
Dog
Bird
```

We train three binary classifiers.

```text
Classifier 1:
Cat vs Everything Else

Classifier 2:
Dog vs Everything Else

Classifier 3:
Bird vs Everything Else
```

For a new image:

```text
Cat probability  = 0.20
Dog probability  = 0.75
Bird probability = 0.05
```

We select:

```text
Dog
```

because it has the highest score.

---

## Why use it?

The main advantage is simplicity.

If we already have a binary classifier, One-vs-Rest provides a straightforward way to extend it to multiple classes.

---

## Limitation

Each classifier is trained independently.

This means the probability estimates from different classifiers may not always be perfectly comparable or naturally sum to 1.

---

## How I would explain it in an interview

> One-vs-Rest is a technique for extending binary classification to multi-class problems. For every class, we train a separate model that distinguishes that class from all remaining classes. During prediction, we run all classifiers and choose the class with the highest score or probability.

---

# 30. What is the Role of the Sigmoid Function in Classification?

The Sigmoid function converts any real number into a value between 0 and 1.

[
\sigma(z) = \frac{1}{1+e^{-z}}
]

---

## Why is this useful?

A model's raw output can be:

```text
-10
2.4
50
-3.7
```

These are not directly interpretable as probabilities.

The Sigmoid function transforms them:

```text
-10  → Close to 0
0    → 0.5
10   → Close to 1
```

So we can interpret the result as the probability of the positive class.

---

## Example

Suppose a fraud model produces:

```text
Raw score = 2
```

After applying Sigmoid:

```text
Probability of fraud = 0.88
```

We can then apply a threshold.

---

## Another important role

Sigmoid provides a smooth and differentiable transformation.

This makes it possible to train the model using gradient-based optimization.

---

## Limitation

For multi-class classification where exactly one class should be selected, Softmax is generally more appropriate.

---

## How I would explain it in an interview

> The Sigmoid function converts a model's raw output into a value between 0 and 1, allowing us to interpret it as a probability for binary classification. It also provides a smooth differentiable function, which allows the model to be trained using gradient-based optimization.

---

# 31. What is the Difference Between Probabilistic and Non-probabilistic Classifiers?

The main difference is what the model gives us as output.

---

## Probabilistic Classifiers

These models estimate the probability of belonging to each class.

For example:

```text
Fraud       → 0.85
Non-Fraud   → 0.15
```

Examples include:

* Logistic Regression
* Naive Bayes
* Neural Networks with Softmax or Sigmoid output
* Many tree-based models when probability estimates are enabled

This is useful when we need to:

* Adjust thresholds
* Rank predictions
* Estimate risk
* Make cost-sensitive decisions

---

## Non-probabilistic Classifiers

These models primarily focus on assigning a class or finding a decision boundary.

For example:

```text
Fraud → Yes
```

A classic example is a standard Support Vector Machine, which finds the decision boundary with the maximum margin.

However, many non-probabilistic classifiers can be calibrated afterward to produce probability-like outputs.

---

## Why does this matter?

Suppose two transactions are predicted as fraud.

A class-only prediction gives:

```text
Transaction A → Fraud
Transaction B → Fraud
```

A probabilistic model gives:

```text
Transaction A → 51% Fraud
Transaction B → 99% Fraud
```

This provides much more information for decision-making.

---

## How I would explain it in an interview

> Probabilistic classifiers estimate the probability that an observation belongs to a class, while non-probabilistic classifiers primarily focus on directly assigning classes or finding a decision boundary. Probabilistic outputs are particularly useful when we need to adjust thresholds, rank predictions, or make decisions based on risk.

---

# 32. What Does a Confusion Matrix Tell You That Accuracy Does Not?

Accuracy gives only one number:

> How many predictions were correct overall?

A Confusion Matrix shows **what kinds of mistakes the model is making**.

---

## Example

For a binary classification problem:

|                 | Predicted Positive | Predicted Negative |
| --------------- | -----------------: | -----------------: |
| Actual Positive |      True Positive |     False Negative |
| Actual Negative |     False Positive |      True Negative |

This gives us four types of outcomes.

---

## Why Accuracy can hide problems

Imagine 1,000 transactions:

```text
Fraud transactions     = 10
Non-fraud transactions = 990
```

A model predicts every transaction as non-fraud.

Accuracy:

```text
990 / 1000 = 99%
```

The accuracy looks excellent.

But the model detected:

```text
0 out of 10 fraud cases
```

The Confusion Matrix immediately reveals this problem.

---

## What can we understand from it?

A Confusion Matrix helps us see:

* How many positive cases we correctly detected
* How many positive cases we missed
* How many false alarms we generated
* How the model behaves for each class

It is also the foundation for:

* Precision
* Recall
* Specificity
* F1 Score

---

## How I would explain it in an interview

> Accuracy only tells us the overall percentage of correct predictions. A Confusion Matrix breaks those predictions into true positives, false positives, true negatives, and false negatives, so it tells us what types of mistakes the model is making. This is especially important for imbalanced datasets.

---

# 33. Why Can F1 Score Be Better Than Accuracy?

F1 Score is often better than Accuracy when the classes are imbalanced.

---

## Example

Suppose we have:

```text
990 Non-Fraud
10 Fraud
```

A model predicts everything as Non-Fraud.

```text
Accuracy = 99%
```

But the model is useless for detecting fraud.

F1 Score considers both:

* Precision
* Recall

So it focuses more on how well the model identifies the positive class.

---

## Precision

When the model says:

> "This is Fraud"

How often is it correct?

---

## Recall

Out of all actual fraud cases:

> How many did the model successfully detect?

---

## F1 Score

F1 combines Precision and Recall using their harmonic mean.

[
F1 = 2 \times \frac{Precision \times Recall}
{Precision + Recall}
]

The harmonic mean ensures that a very low Precision or Recall pulls the F1 score down.

For example:

```text
Precision = 0.95
Recall = 0.10
```

Even though Precision is high, F1 will not be high because Recall is poor.

---

## Important point

F1 is not automatically better than Accuracy.

If:

* Classes are balanced
* False positives and false negatives have similar importance

Accuracy may be perfectly useful.

---

## How I would explain it in an interview

> F1 Score can be more informative than Accuracy for imbalanced classification because Accuracy can remain high even when the model completely fails to detect the minority class. F1 combines Precision and Recall, so it evaluates both how accurate positive predictions are and how many actual positive cases the model captures.

---

# 34. When Would You Use F1 Score Over Precision or Recall?

Use F1 when **both Precision and Recall are important** and you want one metric that balances them.

---

## When Precision is more important

Use Precision when false positives are costly.

Example:

```text
A legitimate transaction is blocked as fraud.
```

You want to avoid incorrectly flagging normal transactions.

---

## When Recall is more important

Use Recall when false negatives are costly.

Example:

```text
A fraudulent transaction is missed.
```

You want to detect as many actual fraud cases as possible.

---

## When F1 is useful

Use F1 when:

* Both false positives and false negatives matter
* Classes are imbalanced
* You want a single metric balancing Precision and Recall

Example:

```text
Spam detection
Fraud detection
Disease screening
```

However, the business context still matters.

---

## Important interview follow-up: F-beta Score

Sometimes Precision and Recall do not have equal importance.

In that case, we can use **F-beta Score**.

* F1 → Precision and Recall are equally weighted
* F2 → Gives more importance to Recall
* F0.5 → Gives more importance to Precision

---

## How I would explain it in an interview

> I would use F1 Score when both Precision and Recall are important and I need a single balanced metric, especially for imbalanced datasets. If false positives are much more costly, I would focus more on Precision. If missing positive cases is more costly, I would prioritize Recall or use an F-beta score that gives Recall more importance.

---

# 35. What are ROC and AUC?

ROC stands for:

> Receiver Operating Characteristic

It shows how a binary classifier performs across different classification thresholds.

---

## What does the ROC curve plot?

```text
Y-axis → True Positive Rate
X-axis → False Positive Rate
```

The True Positive Rate is also called Recall.

[
TPR = \frac{TP}{TP+FN}
]

The False Positive Rate is:

[
FPR = \frac{FP}{FP+TN}
]

---

## Why do we need different thresholds?

Suppose a fraud model gives probabilities.

At threshold:

```text
0.5
```

we get one combination of:

* True Positives
* False Positives

If we reduce the threshold to:

```text
0.2
```

we may detect more fraud cases, but we will also generate more false positives.

The ROC curve shows this trade-off across many thresholds.

---

# What is AUC?

AUC stands for:

> Area Under the ROC Curve

It summarizes the ROC curve into one number.

Generally:

```text
AUC = 1.0 → Perfect discrimination
AUC = 0.5 → Similar to random ranking
```

Another useful intuition is:

> AUC represents the probability that the model ranks a randomly selected positive example higher than a randomly selected negative example.

---

## How I would explain it in an interview

> ROC shows the trade-off between the True Positive Rate and False Positive Rate across different classification thresholds. AUC summarizes the overall ability of the model to distinguish between positive and negative classes. An AUC of 0.5 represents random discrimination, while values closer to 1 indicate better class separation.

---

# 36. Why is AUC-ROC Not Ideal for Highly Imbalanced Datasets?

The problem is the **False Positive Rate**.

[
FPR = \frac{FP}{FP+TN}
]

When the negative class is extremely large, the denominator becomes very large.

This can make the False Positive Rate look small even when the model produces many false positives.

---

## Example

Suppose we have:

```text
Positive cases = 100
Negative cases = 100,000
```

Imagine the model produces:

```text
False Positives = 1,000
```

That may be a large number of incorrect alerts.

But:

```text
FPR = 1,000 / 100,000 = 1%
```

On the ROC curve, this may still look reasonably good.

But operationally, generating 1,000 false alerts may be unacceptable.

---

## Why Precision-Recall is often better

Precision directly asks:

> Of all the cases predicted as positive, how many were actually positive?

This makes it more sensitive to performance on the minority class.

That is why **Precision-Recall curves and PR-AUC** are often more informative for highly imbalanced classification problems.

---

## Important nuance

ROC-AUC is not useless for imbalanced datasets.

It still measures ranking ability.

But it may present an overly optimistic view when the positive class is rare.

---

## How I would explain it in an interview

> ROC-AUC can be less informative for highly imbalanced datasets because the False Positive Rate uses the large number of negative examples in its denominator. A model may generate many false positives while still having a relatively low FPR. In such cases, Precision-Recall curves or PR-AUC are often more informative because they focus more directly on performance for the minority positive class.

---

# 37. Why is Log Loss Used in Classification Instead of MSE?

The main reason is that classification models usually predict **probabilities**, and Log Loss is specifically designed to evaluate probability predictions.

---

## Consider two models

The actual class is:

```text
Fraud = 1
```

Two models predict:

```text
Model A → 0.51
Model B → 0.99
```

Both predict the correct class.

But Model B is much more confident and assigns a higher probability to the correct class.

Log Loss captures this difference naturally.

---

## What does Log Loss strongly penalize?

Log Loss heavily penalizes predictions that are:

> Wrong and extremely confident.

For example:

```text
Actual = Fraud

Prediction = 0.99 → Good
Prediction = 0.51 → Correct but uncertain
Prediction = 0.01 → Extremely bad
```

The last prediction should receive a very large penalty.

Log Loss does exactly that.

---

## Why not simply use MSE?

MSE can compare predicted probabilities with 0 and 1 labels.

But it is not the most natural objective for probabilistic classification.

Cross-Entropy / Log Loss:

* Comes from maximum likelihood estimation
* Is better aligned with probability estimation
* Provides useful gradients for classification
* Strongly penalizes confident incorrect predictions

---

## Binary Cross-Entropy

For binary classification:

[
Loss = -[y\log(p) + (1-y)\log(1-p)]
]

Where:

* (y) is the actual class
* (p) is the predicted probability

---

## How I would explain it in an interview

> Log Loss is used because classification models typically predict probabilities rather than just class labels. It is designed to evaluate those probabilities and heavily penalizes predictions that are confidently wrong. Compared with MSE, Cross-Entropy is better aligned with maximum likelihood estimation and generally provides a more suitable optimization objective for classification.

---

# 38. What is the Difference Between Micro, Macro, and Weighted F1 Scores?

These methods tell us how to calculate an overall F1 score when we have multiple classes.

Suppose we are classifying:

```text
Class A → 900 examples
Class B → 80 examples
Class C → 20 examples
```

The classes are highly imbalanced.

---

# Macro F1

Calculate the F1 score for each class separately.

Then take a simple average.

```text
F1(A)
F1(B)
F1(C)

Macro F1 = Average
```

Every class receives equal importance.

This is useful when we care equally about minority and majority classes.

---

# Weighted F1

Calculate the F1 score for each class.

Then weight each score according to the number of examples in that class.

```text
Large class → More influence
Small class → Less influence
```

This accounts for class imbalance while still considering every class.

---

# Micro F1

Instead of calculating F1 separately for each class, Micro averaging combines:

* True Positives
* False Positives
* False Negatives

across all classes first.

Then it calculates the final Precision, Recall, and F1.

This gives more influence to frequent classes because they contribute more observations.

---

## Simple comparison

| Metric      | How classes are treated  | Best use case                      |
| ----------- | ------------------------ | ---------------------------------- |
| Macro F1    | Every class equally      | Minority classes are important     |
| Weighted F1 | Based on class frequency | Overall performance with imbalance |
| Micro F1    | Combines all predictions | Overall instance-level performance |

---

## Example intuition

Imagine a model performs:

```text
Class A → Excellent
Class B → Good
Class C → Very Poor
```

### Macro F1

The poor performance on Class C will have the same importance as Class A.

### Weighted F1

Since Class C has fewer examples, its poor performance has less influence.

### Micro F1

The majority class has a large influence because it contributes many more predictions.

---

## Important interview point

For single-label multi-class classification, Micro F1 is equivalent to Accuracy.

This happens because each incorrect prediction creates one false positive and one false negative across the class calculations.

---

## How I would explain it in an interview

> Macro F1 calculates F1 for each class and gives every class equal importance, so it is useful when minority classes matter. Weighted F1 also calculates class-wise F1 but weights each class according to its support, making it useful for imbalanced datasets. Micro F1 aggregates all true positives, false positives, and false negatives before calculating the metric, so frequent classes have more influence and, in standard single-label multi-class classification, Micro F1 is equivalent to accuracy.
