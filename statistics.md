# Statistics & Analytics Interview Questions and Answers

---

## 1. What is the Central Limit Theorem (CLT) and why is it important?

### Answer

> The Central Limit Theorem states that if we repeatedly take sufficiently large random samples from a population, the **sampling distribution of the sample mean** tends to become approximately normally distributed, regardless of the original population distribution, under appropriate conditions.

The important point is that CLT does **not** mean the original data becomes normally distributed. It means the **distribution of the sample mean** becomes approximately normal as the sample size increases.

### Why is it important?

It forms the basis for:

- Confidence intervals
- Hypothesis testing
- Statistical inference

For example, even if customer income is highly skewed, we can often make inferences about the **mean income** using the approximate normality of the sample mean.

### Cross-question: Does the sample size always have to be 30?

> No. Thirty is only a rule of thumb. The required sample size depends on the underlying distribution. Highly skewed or heavy-tailed distributions may require larger samples.

---

## 2. Explain a p-value.

### Answer

> A p-value is the probability of observing a result at least as extreme as the one observed, **assuming that the null hypothesis is true**.

For example:

- **H₀:** A new model does not improve conversion.
- We obtain a p-value of 0.03.

This means:

> Assuming there is actually no improvement, there is a 3% probability of observing a result this extreme or more extreme because of random variation.

If:

\[
p < \alpha
\]

where \(\alpha\) is the significance level, commonly 0.05, we reject the null hypothesis.

### Important misconception

A p-value does **not** mean:

> "There is a 3% probability that the null hypothesis is true."

The p-value is calculated **assuming the null hypothesis is true**.

---

## 3. How do you calculate a confidence interval?

### Answer

The general formula is:

\[
\text{Confidence Interval}
=
\text{Point Estimate}
\pm
\text{Critical Value} \times \text{Standard Error}
\]

For a mean, when population variance is unknown:

\[
\bar{x}
\pm
t^*
\frac{s}{\sqrt{n}}
\]

Where:

- \(\bar{x}\) = Sample mean
- \(s\) = Sample standard deviation
- \(n\) = Sample size
- \(t^*\) = Critical value

### Interview explanation

> A confidence interval provides a range of plausible values for a population parameter. It is calculated using the point estimate plus or minus a margin of error, where the margin depends on the standard error and the confidence level.

### How do you correctly interpret a 95% confidence interval?

> If we repeated the same sampling process many times and constructed confidence intervals using the same method, approximately 95% of those intervals would contain the true population parameter.

---

## 4. Explain Descriptive vs Predictive vs Prescriptive Analytics.

### Answer

### Descriptive Analytics — What happened?

It summarizes historical data.

Examples:

- What was last month's revenue?
- What was the loan default rate?
- Which customer segment had the highest conversion?

---

### Predictive Analytics — What is likely to happen?

It uses historical data to predict future or unknown outcomes.

Examples:

- Will this customer default?
- Which customer is likely to churn?
- What will next month's demand be?

Common techniques include:

- Regression
- Classification
- Time-series forecasting
- Machine learning

---

### Prescriptive Analytics — What should we do?

It recommends an action based on predictions, business objectives, and constraints.

For example:

- Which customers should receive a loan offer?
- How should we allocate a marketing budget?
- What credit limit should we offer?

### Fintech example

> Descriptive analytics tells us which customer segments historically defaulted more. Predictive analytics estimates the probability that a new customer will default. Prescriptive analytics uses that prediction along with business constraints to decide whether to approve the loan and under what terms.

---

## 5. Explain Bayesian Probability.

### Answer

> Bayesian probability is a framework for updating our belief about an event or hypothesis when new evidence becomes available.

Bayes' theorem is:

\[
P(A|B)
=
\frac{P(B|A)P(A)}
{P(B)}
\]

Where:

- \(P(A)\) = Prior probability
- \(P(B|A)\) = Likelihood
- \(P(A|B)\) = Posterior probability

The basic idea is:

\[
\text{Prior Belief}
+
\text{New Evidence}
\rightarrow
\text{Updated Belief}
\]

### Example

Suppose based on historical data, we believe a customer has a 5% probability of default. Then we observe new information such as:

- Missed payments
- High credit utilization
- Declining income

We can update our prior belief using this new evidence to obtain a **posterior probability of default**.

### Bayesian vs Frequentist

> In frequentist statistics, parameters are generally treated as fixed and data as random. In Bayesian statistics, uncertainty about parameters can be represented using probability distributions, which are updated as new evidence becomes available.

---

# Hypothesis Testing

---

## 6. What is the null hypothesis?

### Answer

> The null hypothesis, denoted by \(H_0\), represents the default assumption that there is no effect, no difference, or no relationship.

For example:

\[
H_0: Conversion_A = Conversion_B
\]

The alternative hypothesis is:

\[
H_1: Conversion_A \neq Conversion_B
\]

We use the observed data to determine whether there is sufficient evidence to reject \(H_0\).

### Important wording

We say:

- **Reject the null hypothesis**
- **Fail to reject the null hypothesis**

We generally do not say:

> "Accept the null hypothesis."

Failing to reject \(H_0\) does not prove that it is true.

---

## 7. Type I Error vs Type II Error.

### Answer

### Type I Error

> Rejecting the null hypothesis when it is actually true.

This is a **false positive**.

Example:

> We conclude that a new lending strategy improves conversion when in reality it does not.

The probability of a Type I error is:

\[
\alpha
\]

---

### Type II Error

> Failing to reject the null hypothesis when it is actually false.

This is a **false negative**.

Example:

> We conclude that a new strategy does not improve conversion when it actually does.

The probability of a Type II error is:

\[
\beta
\]

### Easy memory trick

| | Reality: No Effect | Reality: Effect Exists |
|---|---|---|
| Reject \(H_0\) | Type I Error | Correct |
| Fail to Reject \(H_0\) | Correct | Type II Error |

---

## 8. What is statistical power?

### Answer

> Statistical power is the probability of correctly rejecting the null hypothesis when the alternative hypothesis is actually true.

Mathematically:

\[
Power = 1 - \beta
\]

where \(\beta\) is the probability of a Type II error.

### Example

If an experiment has 80% power:

> It has an 80% probability of detecting an effect of the specified size if that effect truly exists.

### How can we increase power?

- Increase sample size
- Increase effect size
- Reduce variability
- Use a higher significance level, although this increases Type I error risk

### Interview nuance

> Low power means that failing to find statistical significance does not necessarily mean there is no effect. The experiment may simply not have enough data to detect it.

---

## 9. What is the relationship between p-value and confidence interval?

### Answer

Both are related to statistical inference.

For a two-sided hypothesis test at significance level \(\alpha\):

> If the null hypothesis value lies outside the corresponding \((1-\alpha)\) confidence interval, we reject the null hypothesis.

For example, if we are testing whether the difference between two conversion rates is zero:

- 95% CI does **not** contain 0 → significant at approximately the 5% level.
- 95% CI contains 0 → fail to reject the null at the 5% level.

### Difference

> A p-value tells us how compatible the observed data is with the null hypothesis, while a confidence interval gives a range of plausible values and also shows the magnitude and uncertainty of the effect.

---

## 10. Can a statistically significant result be practically insignificant?

### Answer

> Yes. Statistical significance does not necessarily imply business or practical significance.

For example:

- Old conversion rate = 10.00%
- New conversion rate = 10.05%
- Sample size = 10 million

Even this very small improvement may be statistically significant because the sample size is extremely large.

However, the business impact may be negligible.

### Strong interview answer

> I would look at both statistical significance and effect size. I would also consider the confidence interval, business impact, implementation cost, and potential risks before making a decision.

---

## 11. How would you determine whether an A/B test is statistically significant?

### Answer

My approach would be:

### Step 1: Define the hypothesis

For example:

\[
H_0: p_A = p_B
\]

\[
H_1: p_A \neq p_B
\]

---

### Step 2: Define the primary metric

For example:

- Conversion rate
- Revenue per user
- Average order value

It is important to define the primary metric before analyzing the results to avoid cherry-picking.

---

### Step 3: Set the significance level

For example:

\[
\alpha = 0.05
\]

---

### Step 4: Ensure sufficient sample size and power

The experiment should have enough observations to detect the minimum effect size that matters to the business.

---

### Step 5: Choose the appropriate statistical test

Examples:

- Conversion rate → Two-proportion test
- Continuous metric → t-test or another suitable test
- Categorical outcomes → Chi-square test

---

### Step 6: Calculate the test statistic and p-value

If:

\[
p < \alpha
\]

we reject the null hypothesis.

---

### Strong senior-level answer

> I would not stop at the p-value. I would also evaluate the confidence interval, effect size, practical significance, experiment validity, and whether the observed improvement is meaningful enough to justify implementation.

---

## 12. How do you determine sample size for an experiment?

### Answer

Sample size depends mainly on:

1. **Baseline metric**
2. **Minimum Detectable Effect (MDE)**
3. **Significance level (\(\alpha\))**
4. **Statistical power (\(1-\beta\))**
5. **Variance of the metric**

### Interview answer

> Before running the experiment, I would define the minimum improvement that is practically meaningful, known as the Minimum Detectable Effect. Then, based on the baseline conversion rate or metric variance, desired significance level, and desired statistical power, I would calculate the required sample size.

### Important relationship

```text
Smaller effect we want to detect
            ↓
     Larger sample needed

Higher statistical power
            ↓
     Larger sample needed

Higher variability
            ↓
     Larger sample needed
