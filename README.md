# K-Means Clustering Analysis

This notebook demonstrates a comprehensive K-Means clustering analysis on a synthetic dataset. It covers data generation, preprocessing, selection of the optimal number of clusters (`K`) using various evaluation metrics, and visualization of the final clustering results.

## Table of Contents
1.  [Introduction](#introduction)
2.  [Libraries Used](#libraries-used)
3.  [Data Generation](#data-generation)
4.  [Data Preprocessing (Scaling)](#data-preprocessing-scaling)
5.  [Determining Optimal K](#determining-optimal-k)
    *   Elbow Method (WCSS)
    *   Silhouette Score
    *   Davies-Bouldin Index
    *   Calinski-Harabasz Index
6.  [Final K-Means Clustering and Visualization](#final-k-means-clustering-and-visualization)

## 1. Introduction
K-Means is a popular unsupervised machine learning algorithm used for partitioning `n` observations into `k` clusters. This notebook aims to illustrate the process of applying K-Means, critically evaluating the choice of `K`, and visualizing the results.

## 2. Libraries Used
-   `numpy`: For numerical operations.
-   `matplotlib.pyplot`: For plotting and visualization.
-   `sklearn.cluster.KMeans`: The K-Means clustering algorithm.
-   `sklearn.datasets.make_blobs`: To generate a synthetic dataset suitable for clustering.
-   `sklearn.metrics`: To calculate clustering evaluation scores (`silhouette_score`, `davies_bouldin_score`, `calinski_harabasz_score`).
-   `sklearn.preprocessing.StandardScaler`: To scale the data.

## 3. Data Generation
A synthetic 2D dataset with 800 samples and 8 distinct centers (true clusters) is generated using `make_blobs`. This allows for a ground truth (`y_true`) to compare against the clustering results.

## 4. Data Preprocessing (Scaling)
The generated data `x` is standardized using `StandardScaler`. Scaling is crucial for K-Means as the algorithm is sensitive to the scale of the features, ensuring that all features contribute equally to the distance calculations.

## 5. Determining Optimal K
The notebook evaluates the clustering performance for a range of `K` values (from 2 to 11) using four common metrics:

-   **Elbow Method (WCSS - Within-Cluster Sum of Squares):** Plots the WCSS against `K`. The 'elbow' point where the rate of decrease in WCSS significantly slows down is often chosen as the optimal `K`.
-   **Silhouette Score:** Measures how similar an object is to its own cluster compared to other clusters. Higher values indicate better-defined clusters.
-   **Davies-Bouldin Index:** Measures the average similarity between each cluster and its most similar cluster. Lower values indicate better clustering.
-   **Calinski-Harabasz Index:** Measures the ratio of between-cluster dispersion to within-cluster dispersion. Higher values indicate better-defined clusters.

The results for each `K` are printed, and the 'best' `K` according to each metric is identified:

-   **Best K by Silhouette Score:** 7
-   **Best K by Davies-Bouldin Index:** 7
-   **Best K by Calinski-Harabasz Index:** 8

Visualizations for all four metrics are generated in a 2x2 subplot grid, with vertical lines indicating the best `K` as per each metric. This visual aid helps in understanding the trade-offs and finding a consensus.

## 6. Final K-Means Clustering and Visualization
Based on the evaluation metrics, `K=7` is chosen as a strong candidate due to its consistent high performance across Silhouette and Davies-Bouldin scores. K-Means is then applied with `n_clusters=7` to the scaled data.

The final clustering result is visualized using a scatter plot. Data points are colored according to their assigned cluster, and the cluster centroids are marked with red 'X' symbols. This visualization provides a clear picture of how the data has been partitioned into 7 distinct groups.
