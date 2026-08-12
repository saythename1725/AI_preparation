# 16. What is a Normal Distribution?

## The idea

A Normal Distribution is a probability distribution where most values are concentrated around the average, and fewer values occur as we move farther away from it.

It is commonly represented as a bell-shaped curve.

For example, if we look at the heights of a very large group of people, most people will be around the average height, while very few will be extremely short or extremely tall.

---

## Main characteristics

A Normal Distribution is:

* Symmetric around the mean
* Bell-shaped
* Defined by its mean and standard deviation

For a perfectly normal distribution:

```text
Mean = Median = Mode
```

The mean represents the center, while the standard deviation tells us how spread out the data is.

A smaller standard deviation means the values are more concentrated around the mean.

A larger standard deviation means the values are more spread out.

---

## The 68–95–99.7 Rule

For a normal distribution:

* Around **68%** of values lie within 1 standard deviation of the mean.
* Around **95%** lie within 2 standard deviations.
* Around **99.7%** lie within 3 standard deviations.

This helps us understand how unusual a particular observation is.

---

## Why is it important in Machine Learning and Statistics?

Normal distributions are important because many statistical techniques assume normality somewhere in the model or inference process.

However, an important interview point is:

> The input features themselves do not always need to be normally distributed.

For example, in Linear Regression, the normality assumption applies to the **residuals for certain statistical inference**, not necessarily to the features.

---

## How I would explain it in an interview

> A Normal Distribution is a symmetric, bell-shaped probability distribution where most observations are concentrated around the mean, and the probability decreases as we move away from the center. The mean determines the center and the standard deviation determines the spread.

---

# 17. What are the Assumptions Behind Linear Regression?

Linear Regression has several important assumptions.

The easiest way to remember them is to separate assumptions about the **relationship**, **errors**, and **features**.

---

## 1. Linearity

The relationship between the features and target should be approximately linear.

For example:

```text
House Price = β₀ + β₁ × Area
```

This does not mean every real-world relationship has to look perfectly like a straight line.

It means the model should be able to represent the relationship as a linear combination of the parameters and features.

If the relationship is strongly non-linear, a simple Linear Regression model may not capture it properly.

---

## 2. Independence of Errors

The errors or residuals should be independent of each other.

This is especially important in time-series data.

For example, if today's prediction error strongly depends on yesterday's error, then the independence assumption may be violated.

---

## 3. Homoscedasticity

The variance of the residuals should remain approximately constant across different prediction levels.

Ideally:

```text
Predicted Value → Residual spread remains similar
```

A problem occurs when the errors become much larger for certain ranges.

For example:

```text
Low house prices → Small errors
High house prices → Very large errors
```

This is called **heteroscedasticity**.

---

## 4. No Perfect or Severe Multicollinearity

Independent variables should not be extremely correlated with each other.

For example:

```text
House Area
Number of Square Feet
```

If these essentially represent the same information, it becomes difficult to determine the individual effect of each variable.

An important point:

> Multicollinearity usually does not necessarily hurt prediction accuracy as much as it hurts coefficient interpretation and stability.

---

## 5. Normality of Residuals

For classical statistical inference, such as confidence intervals and hypothesis testing, residuals are often assumed to be approximately normally distributed.

This assumption is more important for inference than for simply generating predictions.

---

## 6. No Major Influential Outliers

Extreme observations can strongly influence the regression line.

For example, one extremely expensive house could significantly change the estimated relationship between area and price.

---

## Quick summary

| Assumption              | Main idea                                                     |
| ----------------------- | ------------------------------------------------------------- |
| Linearity               | Relationship can be modeled linearly                          |
| Independence            | Errors should not depend on each other                        |
| Homoscedasticity        | Error variance should be relatively constant                  |
| Low multicollinearity   | Features should not contain excessive overlapping information |
| Normal residuals        | Important mainly for statistical inference                    |
| No influential outliers | Extreme observations should not dominate the model            |

---

## How I would explain it in an interview

> The main assumptions of Linear Regression are linearity between predictors and the target, independence of residuals, constant variance of residuals, limited multicollinearity, and approximately normal residuals when performing statistical inference. We should also check for influential outliers because they can significantly affect the fitted regression line.

---

# 18. How Do Violations of Linear Regression Assumptions Impact the Model?

Not every assumption violation affects the model in the same way.

Some mainly affect **predictions**, while others mainly affect **statistical interpretation**.

---

## 1. Violation of Linearity

If the true relationship is non-linear but we force a straight-line relationship:

```text
Actual pattern → Curve
Model → Straight line
```

The model will systematically miss patterns.

This can cause:

* High bias
* Poor predictions
* Structured patterns in residuals

### Possible solutions

* Add polynomial features
* Transform variables
* Use non-linear models

---

## 2. Violation of Independence

If residuals are correlated, especially in time-series data, the model may underestimate uncertainty.

This can make statistical tests and confidence intervals unreliable.

### Possible solutions

* Time-series models
* Lag features
* Models that account for autocorrelation

---

## 3. Heteroscedasticity

If the error variance changes across predictions, coefficient estimates may still be useful, but standard errors and statistical inference can become unreliable.

### Possible solutions

* Log transformation
* Weighted Least Squares
* Robust standard errors

---

## 4. Multicollinearity

Highly correlated features can cause:

* Unstable coefficients
* Large standard errors
* Difficulty interpreting feature importance

For example, two correlated features may individually appear insignificant even though together they contain useful information.

### Possible solutions

* Remove one of the correlated variables
* Combine features
* Use Ridge or Elastic Net regularization
* Use dimensionality reduction

---

## 5. Non-Normal Residuals

This mainly affects classical statistical inference, particularly with small datasets.

Prediction itself may still be reasonable.

With sufficiently large datasets, inference can often be more robust due to asymptotic properties.

---

## 6. Outliers

Outliers can pull the regression line toward themselves.

This can significantly affect:

* Coefficients
* Predictions
* Overall model interpretation

---

## How I would explain it in an interview

> Different assumption violations affect Linear Regression differently. Non-linearity can directly hurt predictions because the model cannot capture the true pattern. Multicollinearity mainly makes coefficients unstable and difficult to interpret. Heteroscedasticity and correlated errors can make standard errors and statistical inference unreliable. Outliers can strongly influence the fitted model.

---

# 19. What are the Common Regression Metrics?

Regression metrics measure how close predicted numerical values are to the actual values.

The most common ones are:

* MAE
* MSE
* RMSE
* R²
* Adjusted R²
* MAPE

---

## 1. MAE — Mean Absolute Error

MAE calculates the average absolute difference between actual and predicted values.

Example:

```text
Actual price     = 100
Predicted price  = 90

Absolute error = |100 - 90| = 10
```

MAE is easy to interpret because it is in the same unit as the target.

If we predict house prices in lakhs, MAE is also measured in lakhs.

---

## 2. MSE — Mean Squared Error

MSE squares each error before averaging.

This means larger errors receive much larger penalties.

Example:

```text
Error = 2  → Squared error = 4
Error = 10 → Squared error = 100
```

This makes MSE sensitive to outliers.

---

## 3. RMSE — Root Mean Squared Error

RMSE is simply the square root of MSE.

The advantage is that the result returns to the same unit as the target.

For example:

```text
Target → House Price in lakhs
RMSE   → Also in lakhs
```

---

## 4. R² Score

R² measures how much better the model performs compared with a simple baseline that always predicts the mean of the target.

It is generally interpreted as the proportion of variance explained by the model, though this should be understood carefully.

---

## 5. Adjusted R²

A regular R² score never decreases when we add more features.

Adjusted R² penalizes unnecessary features.

It is especially useful when comparing Linear Regression models with different numbers of predictors.

---

## 6. MAPE

MAPE measures average percentage error.

Example:

```text
Actual = 100
Prediction = 90

Percentage Error = 10%
```

However, MAPE has problems when actual values are zero or close to zero.

---

## Quick comparison

| Metric      | Main characteristic               |
| ----------- | --------------------------------- |
| MAE         | Average absolute error            |
| MSE         | Penalizes large errors heavily    |
| RMSE        | Like MSE but in original units    |
| R²          | Compares model with mean baseline |
| Adjusted R² | Accounts for unnecessary features |
| MAPE        | Measures percentage error         |

---

## How I would explain it in an interview

> The most common regression metrics are MAE, MSE, RMSE, R², Adjusted R², and sometimes MAPE. MAE treats all errors linearly, while MSE and RMSE penalize larger errors more heavily. R² compares the model against a baseline that predicts the mean. The choice depends on the business problem and how costly large prediction errors are.

---

# 20. What is the Difference Between MSE and MAE?

The main difference is how they treat large errors.

---

## MAE

MAE uses the absolute value of the error.

```text
Error = 2  → Penalty = 2
Error = 10 → Penalty = 10
```

The penalty increases linearly.

This makes MAE more robust to outliers.

---

## MSE

MSE squares the error.

```text
Error = 2  → Penalty = 4
Error = 10 → Penalty = 100
```

Large errors are punished much more heavily.

---

## Example

Suppose two models make these errors:

```text
Model A → 2, 2, 2, 2, 20
Model B → 6, 6, 6, 6, 6
```

MAE may consider Model A competitive because most predictions are very good.

But MSE will heavily penalize Model A because of the error of 20.

This means the choice depends on the business problem.

If a large mistake is especially costly, MSE may be more appropriate.

---

## How I would explain it in an interview

> MAE treats errors proportionally, while MSE squares the errors and therefore penalizes large mistakes much more heavily. MAE is more robust to outliers, whereas MSE is useful when large prediction errors are particularly undesirable.

---

# 21. Why is MSE Commonly Used Instead of MAE During Model Training?

The main reason is optimization.

---

## MSE is Smooth and Differentiable

MSE is based on squared errors.

This gives it a smooth derivative.

That makes it convenient for gradient-based optimization.

The gradient also increases with the size of the error.

So large mistakes naturally produce stronger updates.

---

## MAE Has a Problem Around Zero

MAE uses the absolute value.

The absolute value function has a sharp point at zero.

This makes optimization less straightforward because the derivative is not defined at exactly zero.

In practice, optimization methods can still handle MAE using subgradients or other techniques, but it is generally less smooth than MSE.

---

## Important nuance

It is not correct to say:

> "MSE is always better than MAE."

MSE is often easier to optimize and strongly penalizes large errors.

But MAE may be preferred when:

* Outliers are common
* Extreme errors should not dominate training
* Median prediction is more appropriate

---

## How I would explain it in an interview

> MSE is commonly used during training because it is smooth and works well with gradient-based optimization. Squaring the errors also creates stronger gradients for larger mistakes. MAE is more robust to outliers, but its absolute value function is less smooth around zero, making optimization somewhat less straightforward.

---

# 22. What Does R² Signify?

R² compares our model against a simple baseline.

The baseline predicts:

> Always predict the average value of the target.

R² tells us how much improvement our model provides relative to that baseline.

---

## Example

Suppose we want to predict house prices.

A very simple baseline might predict:

```text
Every house price = Average house price
```

If our model uses:

* Area
* Location
* Number of bedrooms
* Age of the house

and makes significantly better predictions than the baseline, the R² score will increase.

---

## Interpretation

An R² of:

```text
R² = 0
```

means the model is performing no better than predicting the mean.

An R² close to:

```text
R² = 1
```

means the model explains a large amount of variation in the observed target values.

An R² can also be negative on unseen test data if the model performs worse than simply predicting the mean.

---

## Important point

R² is not simply:

> "My model is 80% accurate."

That interpretation is incorrect.

It is better to think of R² as measuring how much better the model explains the variation in the target compared with the mean baseline.

---

## How I would explain it in an interview

> R² measures how well a regression model performs relative to a baseline that always predicts the mean of the target. An R² of 0 means the model is no better than that baseline, while values closer to 1 indicate that the model explains more of the variation in the observed target. However, R² should not be interpreted as classification-style accuracy.

---

# 23. Where Can R² Be Misleading?

R² is useful, but it should never be the only metric used.

---

## 1. A High R² Does Not Mean Small Prediction Errors

A model can have a high R² but still make large errors.

For example, if house prices vary between ₹50 lakh and ₹10 crore, an RMSE of ₹30 lakh might still result in a high R².

So always look at an error metric such as:

* MAE
* RMSE

along with R².

---

## 2. R² Increases When Features Are Added

In standard Linear Regression, adding another feature cannot decrease the training R².

Even a useless feature can slightly increase it.

This is why Adjusted R² can be useful when comparing models with different numbers of features.

---

## 3. R² Does Not Detect Overfitting

A model can have:

```text
Training R² = 0.99
Test R² = 0.60
```

The training R² looks excellent, but the model is overfitting.

We should always compare training and validation/test performance.

---

## 4. R² Can Hide Important Business Errors

Suppose a model predicts customer demand.

Overall, the R² may be high.

But if the model consistently performs badly during high-demand periods, that could be a serious business problem.

R² averages overall performance and may hide errors in important segments.

---

## 5. R² Depends on Target Variability

The same prediction errors can result in different R² values depending on how much the target varies.

If the target has a very wide range, a model may achieve a relatively high R² even when the absolute errors are large.

---

## 6. R² Can Be Negative on Test Data

Many people assume R² is always between 0 and 1.

That is not always true.

On unseen data, R² can be negative if the model performs worse than simply predicting the mean.

---

## The best practice

Do not evaluate a regression model using only R².

Use a combination such as:

```text
R²    → Relative goodness of fit
MAE   → Average prediction error
RMSE  → Sensitivity to large errors
```

Then connect the metrics to the business problem.

---

## How I would explain it in an interview

> R² can be misleading because a high R² does not necessarily mean prediction errors are small. It also tends to increase when more features are added, can hide poor performance in important segments, and does not directly detect overfitting. I usually look at R² together with MAE or RMSE and evaluate performance on validation or test data.
