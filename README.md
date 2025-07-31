## Clustering-and-Classification-from-Scratch-KMeans-KMeansPlusPlus-KNN

This project implements clustering and classification from scratch using the following techniques:

1. **K-Means Clustering**
2. **K-Means++ Clustering (Improved Initialization)**
3. **K-Nearest Neighbors (K-NN) Classification**

The objective is to cluster high-dimensional data and classify unseen samples using centroids obtained from unsupervised methods.

---

## 📂 Files

* `cluster_data1.csv` – Dataset used for K-Means and K-Means++
* `cluster_data2.csv` – Dataset used for K-NN classification
* `Kmeans_Kmean++.ipynb` – Full implementation including data preprocessing, clustering, visualization, and KNN classification

---

## ⚙️ Part 1: K-Means Clustering

### 🔢 Steps:

1. **Standardization** using Z-score:

   ```
   z = (x - μ) / σ
   ```
2. **Initialize `k=3` centroids randomly** from dataset
3. **Distance calculation** using Euclidean distance:

   ```
   d = √(Σ(xᵢ - yᵢ)²)
   ```
4. **Assign each point** to the nearest centroid
5. **Recompute centroids** using cluster-wise mean
6. **Repeat** for a fixed number of iterations (4) or until convergence
7. **Visualize** cluster assignments and centroid movements

### 📈 Output:

* Initial centroids randomly chosen
* Iterative refinement of centroids and clusters
* Final clusters after 4 iterations:

  * Cluster 1: 49 points
  * Cluster 2: 31 points
  * Cluster 3: 70 points

---

## ⚙️ Part 2: K-Means++ Clustering

### ✅ Key Differences from K-Means:

* Smarter centroid initialization

  * First centroid chosen randomly
  * Next centroids chosen as farthest points from existing ones (based on distance)
* Better cluster balance and faster convergence

### 🔢 Steps:

1. Initialize first centroid randomly
2. Select next centroids using distance-based probability
3. Proceed with K-Means clustering using chosen centroids
4. Visualize initial centroids, intermediate centroids, and final clusters

### 📈 Output:

* Final clusters after 4 iterations:

  * Cluster 1: 55 points
  * Cluster 2: 50 points
  * Cluster 3: 45 points
* Balanced clusters and early centroid stabilization observed

---

## ⚙️ Part 3: K-Nearest Neighbors (KNN) Classification

### 🧠 Objective:

To classify 15 new, unseen data points (from `cluster_data2.csv`) into clusters based on trained centroids from K-Means++

### 🔢 Steps:

1. Standardize test data
2. Use clustering results from Part 2 as labeled training data
3. For each test point:

   * Compute Euclidean distances to all training points
   * Choose `k=3` nearest neighbors
   * Assign majority class label

### 🧮 Formula:

* **Distance**: Same Euclidean formula
* **Majority Voting**: Based on class frequency among 3 neighbors

### 📈 Output:

* Predicted class labels added to test dataset
* Visualization of test points over existing clusters

  * Cluster 1: Red
  * Cluster 2: Teal
  * Cluster 3: Orange

---

## 📊 Results Summary

| Method        | Cluster Sizes (Final)  | Centroid Convergence | Comments                                |
| ------------- | ---------------------- | -------------------- | --------------------------------------- |
| **K-Means**   | 49, 31, 70             | Slower               | Can suffer from random init             |
| **K-Means++** | 55, 50, 45             | Faster               | Balanced clusters and better separation |
| **K-NN**      | Classified test points | N/A                  | Used trained clusters for prediction    |

---

## ✅ Key Insights

* K-Means++ outperforms K-Means in terms of centroid placement and convergence
* K-NN works well when trained on K-Means++ clusters, making it useful for classifying new points
* Standardization is essential to prevent scale bias in distance-based models

## 📌 Summary of Clustering and Classification Results

* **K-Means** begins by randomly selecting 3 initial centroids in a 4-dimensional feature space (X1, X2, X3, X4), which may result in imbalanced clusters. Points are assigned to the nearest centroid using **Euclidean distance**, and centroids are updated as the mean of cluster points in each iteration.

* Over 4 iterations, centroids gradually stabilize:

  * Final cluster sizes: **Cluster 1: 49**, **Cluster 2: 31**, **Cluster 3: 70**
  * Centroids converge slowly and cluster boundaries are less balanced.

* **K-Means++** improves this by selecting well-separated initial centroids based on distance, resulting in more balanced clusters and faster convergence:

  * Initial centroids: chosen iteratively with increasing spread
  * Final cluster sizes: **Cluster 1: 55**, **Cluster 2: 50**, **Cluster 3: 45**
  * Clear, distinct cluster formations with minimal centroid movement after iteration 3.

* **K-NN Classification (k=3)** uses the K-Means++ clustered data as training labels to classify new (test) data points:

  * Each test point is classified based on majority class of its 3 nearest neighbors.
  * Final predictions align well with K-Means++ cluster centroids.
  * Visualizations show test points (squares) overlaying original clusters (circles) with centroids (X).

---

## 🧠 Key Takeaways

* **K-Means vs. K-Means++**:

  * K-Means can result in poor cluster balance due to random initialization.
  * K-Means++ offers smarter centroid initialization, producing better and more stable results.

* **K-Means++ vs. K-NN**:

  * K-Means++ is an **unsupervised** algorithm ideal for discovering structure in unlabeled data.
  * K-NN is a **supervised** algorithm used to classify new points based on labeled clusters (from K-Means++).
  * K-NN predictions are consistent with previously formed clusters, providing reliable classification.

* **Distance Metric**: Euclidean distance is consistently used across all models for proximity computation:

  $$
  d = \sqrt{\sum (x_i - y_i)^2}
  $$

* **Model Behavior**:

  * K-Means++ leads to better initialization and convergence.
  * K-NN effectively classifies new points based on trained clustering structure.
  * Final visualization clearly distinguishes between original cluster centroids and K-NN classified points.

---

## 📌 Tools & Libraries

* Python (NumPy, Pandas, Matplotlib)
* No external ML libraries (pure implementation)

---
