# 54. How do Decision Boundaries differ in SVMs with Linear and Non-linear Kernels?

The main goal of an SVM is to find a **decision boundary** that separates different classes.

For example:

```text
● ● ● ● ●        Class A

---------------- Decision Boundary

× × × × ×        Class B
```

The type of decision boundary depends on the kernel being used.

## Linear SVM

A Linear SVM uses a straight decision boundary.

* In two dimensions → a line
* In three dimensions → a plane
* In higher dimensions → a hyperplane

The SVM tries to find the boundary that not only separates the classes but also maximizes the margin between them.

The closest data points to the boundary are called **support vectors**.

## Non-linear SVM

Sometimes the data cannot be separated using a straight line.

For example, one class may surround another:

```text
       × × × ×
    ×           ×

       ● ●
      ●   ●
       ● ●

    ×           ×
       × × × ×
```

A straight line cannot separate these classes properly.

A non-linear kernel allows SVM to learn a more complex boundary.

The important idea is that SVM conceptually finds a linear separation in another feature space, but when viewed in the original space, the boundary appears non-linear.

## Main Difference

| Linear SVM                                           | Non-linear SVM                        |
| ---------------------------------------------------- | ------------------------------------- |
| Uses a straight decision boundary                    | Can learn complex decision boundaries |
| Works well for approximately linearly separable data | Useful for non-linear patterns        |
| Usually faster                                       | Can be computationally more expensive |
| Simpler                                              | More flexible                         |

## How I would explain it in an interview

> A Linear SVM finds a straight decision boundary, or hyperplane, that maximizes the margin between classes. A non-linear SVM uses a kernel to handle more complex patterns. Conceptually, the kernel allows SVM to find a linear separation in another feature space, which appears as a non-linear decision boundary in the original feature space.

---

# 55. What is the Kernel Trick in SVM?

The Kernel Trick is a technique that allows SVM to handle non-linear data.

The basic idea is:

> If data cannot be separated in its current feature space, we can imagine transforming it into another feature space where it becomes linearly separable.

For example, consider data arranged in a circular pattern:

```text
        × × ×

     ×       ×

        ●
       ● ●

     ×       ×

        × × ×
```

A straight line cannot separate the inner points from the outer points.

However, if we transform the data into a higher-dimensional space, the classes may become linearly separable.

## The Problem with Explicit Transformation

Suppose we start with:

```text
x₁, x₂
```

A transformation might create new features such as:

```text
x₁²
x₂²
x₁ × x₂
x₁³
x₂³
```

For complex transformations, the number of features can become extremely large.

Explicitly calculating all of them can be expensive.

The Kernel Trick avoids this.

## Common Kernels

### Linear Kernel

Used when the data is already approximately linearly separable.

```text
K(x, z) = xᵀz
```

### Polynomial Kernel

Useful for polynomial relationships.

```text
K(x, z) = (xᵀz + c)ᵈ
```

### RBF Kernel

The RBF kernel is commonly used for complex non-linear patterns.

Its basic intuition is:

```text
Points close together
→ High similarity

Points far apart
→ Low similarity
```

## How I would explain it in an interview

> The Kernel Trick allows SVM to handle non-linear relationships by implicitly working in a higher-dimensional feature space. Instead of explicitly creating all the transformed features, the kernel directly calculates the similarity or inner product between two points as if the transformation had already happened.

---

# 56. How does the Kernel Trick enable non-linear Decision Boundaries without explicitly mapping data to a higher-dimensional space?

Suppose we transform our data using a function:

```text
φ(x)
```

In the transformed space, SVM may need to calculate the inner product:

```text
φ(x)ᵀφ(z)
```

Actually calculating `φ(x)` can be expensive if the transformed space has thousands or even infinitely many dimensions.

The Kernel Trick replaces this calculation with a kernel function:

```text
K(x, z) = φ(x)ᵀφ(z)
```

So instead of:

```text
Original Data
      ↓
Explicitly create high-dimensional features
      ↓
Calculate inner products
```

we do:

```text
Original Data
      ↓
Kernel Function
      ↓
Directly calculate the required inner product
```

## Why does this create a non-linear boundary?

In the transformed feature space, SVM finds a **linear boundary**.

But when that boundary is viewed back in the original feature space, it can appear non-linear.

```text
Linear boundary in transformed space
                ↓
Non-linear boundary in original space
```

So SVM gets the benefit of a higher-dimensional representation without explicitly constructing it.

## How I would explain it in an interview

> The SVM optimization process depends mainly on inner products between data points. Instead of explicitly mapping data into a high-dimensional space, the Kernel Trick uses a kernel function that directly computes the inner product in that transformed space: K(x, z) = φ(x)ᵀφ(z). This allows SVM to learn a linear separator in the transformed space, which appears as a non-linear decision boundary in the original space.

---

# 57. How does Feature Scaling impact algorithms like SVM and KNN?

Feature scaling is important for algorithms that depend on:

* Distance
* Magnitude
* Gradients

SVM and KNN are both sensitive to the scale of input features.

## Example

Suppose we have:

```text
Age           → 18 to 60
Annual Income → 2,00,000 to 50,00,000
```

Income has much larger numerical values.

Without scaling, it can dominate calculations simply because of its magnitude.

That does not necessarily mean Income is more important.

---

## Impact on KNN

KNN works by calculating the distance between data points.

For example:

```text
Distance = √[(x₁ - x₂)² + (y₁ - y₂)²]
```

Suppose two customers differ by:

```text
Age difference = 5

Income difference = 500,000
```

The Income feature will dominate the distance calculation.

As a result, KNN may choose neighbours mainly based on Income and almost ignore Age.

After scaling, both features contribute more fairly.

---

## Impact on SVM

Feature scaling affects:

* Distance calculations
* Margin calculation
* Position of the decision boundary
* Kernel calculations

This is especially important for kernels such as RBF because they depend on the distance between points.

If one feature has a much larger scale, it can dominate these distance calculations and negatively affect the model.

---

## Common Scaling Methods

### 1. Standardization

Standardization transforms features so that they have approximately:

```text
Mean = 0
Standard Deviation = 1
```

Formula:

```text
z = (x - μ) / σ
```

This is commonly used with SVM.

### 2. Min-Max Scaling

This usually transforms values into a range such as:

```text
0 to 1
```

Formula:

```text
x' = (x - min) / (max - min)
```

---

## Which algorithms generally need scaling?

Feature scaling is particularly important for:

* KNN
* K-Means
* SVM
* PCA
* Logistic Regression
* Neural Networks

## Which algorithms generally do not need scaling?

Tree-based algorithms are generally not sensitive to feature scaling.

Examples include:

* Decision Trees
* Random Forest
* XGBoost
* LightGBM

This is because trees split data using thresholds.

For example:

```text
Income > 500,000
```

If the feature is scaled, the threshold changes accordingly, but the ordering of observations remains the same.

## How I would explain it in an interview

> Feature scaling is important for SVM and KNN because both depend heavily on distances. If one feature has a much larger numerical range, it can dominate the distance calculation and disproportionately influence the model. Scaling puts features on a comparable range so that each feature contributes based on its information rather than its numerical magnitude.
