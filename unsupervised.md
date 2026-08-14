## 58. How does K-Means Clustering work?

K-Means is an **unsupervised learning algorithm** that groups similar data points into `K` clusters.

The goal is to make:

- Data points within the same cluster as similar as possible.
- Data points in different clusters as different as possible.

### How it works

1. **Choose the number of clusters (`K`)**
   - For example, `K = 3`.

2. **Initialize K centroids**
   - A centroid represents the center of a cluster.
   - Initially, the algorithm selects `K` centroids, usually randomly or using K-Means++.

3. **Assign each data point to the nearest centroid**
   - Distance is commonly calculated using **Euclidean distance**.

4. **Update the centroids**
   - Calculate the mean of all data points assigned to each cluster.
   - This mean becomes the new centroid.

5. **Repeat**
   - Keep assigning points and updating centroids until the centroids stop changing significantly.

### Intuitive Example

Imagine students standing randomly in a playground, and you want to divide them into 3 groups.

- Initially, place 3 leaders at different locations.
- Every student joins the leader closest to them.
- Each leader moves to the average position of the students in their group.
- Students again choose the closest leader.
- This process continues until the groups no longer change.

The final leader positions are the **centroids**, and the groups are the **clusters**.

### Interview Answer

> K-Means is an unsupervised clustering algorithm that divides data into `K` groups. It works iteratively by initializing `K` centroids, assigning each data point to its nearest centroid, and then recalculating the centroid as the mean of all points assigned to that cluster. These steps are repeated until the algorithm converges. The objective is to minimize the within-cluster sum of squared distances, also known as WCSS or inertia.

---

## 59. What are the limitations of K-Means?

Although K-Means is simple and efficient, it has several limitations.

### 1. You need to specify K beforehand

The algorithm requires us to decide the number of clusters before training.

For example, when clustering customers, we may not initially know whether there are 3, 5, or 10 meaningful customer segments.

### 2. Sensitive to initialization

The initial positions of centroids can affect the final clusters.

Poor initialization can cause K-Means to converge to a suboptimal solution.

**Solution:** Use **K-Means++**, which provides smarter centroid initialization.

### 3. Sensitive to outliers

K-Means calculates centroids using the **mean**, so extreme values can significantly influence the centroid.

For example, if most customers have an income between ₹5–10 lakh, but one customer earns ₹10 crore, that outlier can pull the cluster centroid toward it.

### 4. Assumes roughly spherical clusters

K-Means works best when clusters are:

- Roughly spherical.
- Similar in size.
- Similar in density.

It may struggle with irregularly shaped clusters.

For example, it may not correctly separate data that forms two moon-shaped patterns.

### 5. Sensitive to feature scaling

K-Means is a distance-based algorithm, so features with larger numerical ranges can dominate the distance calculation.

For example:

- Age: `20–60`
- Income: `₹2,00,000–₹20,00,000`

Income may dominate the clustering unless the features are scaled.

**Solution:** Use techniques such as `StandardScaler` or `MinMaxScaler`.

### Interview Answer

> The main limitations of K-Means are that we need to specify the number of clusters in advance, it is sensitive to centroid initialization and outliers, and it works best when clusters are roughly spherical and have similar sizes and densities. Since it is distance-based, feature scaling is also important. It can struggle with irregularly shaped or overlapping clusters.

---

## 60. How do you choose the optimal number of clusters?

There is no single universal method for selecting the optimal number of clusters. The most common approaches are the **Elbow Method**, **Silhouette Score**, and **domain knowledge**.

### 1. Elbow Method

For different values of `K`, we calculate **WCSS (Within-Cluster Sum of Squares)**, also called **inertia**.

As `K` increases, WCSS decreases because having more clusters allows data points to be grouped more closely.

We plot:

- **X-axis:** Number of clusters (`K`)
- **Y-axis:** WCSS or Inertia

Initially, WCSS decreases sharply. After a certain point, adding more clusters provides only a small improvement.

This point is called the **elbow**, and the corresponding value of `K` is often selected as the optimal number of clusters.

### Intuition

Suppose you are grouping students:

- Going from 1 group to 2 groups may significantly improve the grouping.
- Going from 2 to 3 groups may also provide a significant improvement.
- But going from 10 to 11 groups may provide very little additional benefit.

The point where the improvement starts decreasing significantly is the **elbow**.

### 2. Silhouette Score

The Silhouette Score measures how well a data point fits within its own cluster compared to other clusters.

It considers:

- **Cohesion:** How close a point is to other points in its own cluster.
- **Separation:** How far it is from points in other clusters.

The score ranges from `-1` to `1`:

- **Close to 1:** Well-separated and compact clusters.
- **Around 0:** Clusters overlap.
- **Less than 0:** Points may be assigned to the wrong cluster.

Generally, we compare different values of `K` and prefer the one with a higher Silhouette Score.

### 3. Domain Knowledge

Mathematical metrics do not always provide the most useful number of clusters.

For example, a model may suggest that 7 customer clusters are optimal, but the business may only be able to create meaningful strategies for 4 customer segments.

Therefore, the final choice should also consider whether the clusters are **interpretable, meaningful, and actionable**.

### Interview Answer

> I would typically use the Elbow Method and Silhouette Score to choose the optimal number of clusters. In the Elbow Method, I plot WCSS against different values of K and look for the point where the reduction in WCSS starts slowing down. With the Silhouette Score, I evaluate how compact and well-separated the clusters are, where a higher score generally indicates better clustering. Finally, I would validate the result using domain knowledge to ensure that the clusters are meaningful and useful for the business.
