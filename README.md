# MSCS_634_Lab_5
# Clustering Wine Data with Hierarchical and DBSCAN Algorithms

## Overview
In this project, I used Hierarchical (Agglomerative) and DBSCAN clustering techniques to analyze the Wine dataset from scikit-learn. The primary aim was to investigate how these clustering methods categorize the data, compare their sensitivity to various parameters, and assess their performance through visualizations and clustering metrics.

## Steps Taken
1. **Data Preparation & Exploration**
   - I loaded the Wine dataset and converted it into a pandas DataFrame.
   - I reviewed the initial rows, data types, and summary statistics.
   - I standardized all features to have a mean of 0 and a variance of 1 to ensure fair clustering.

2. **Hierarchical Clustering**
   - I applied AgglomerativeClustering for different values of `n_clusters` (2, 3, and 4).
   - I visualized the first two standardized features, coloring them based on cluster labels.
   - I created a truncated dendrogram (with p = 5) to observe how samples merge at various linkage distances.

3. **DBSCAN Clustering**
   - I tested several combinations of `eps` (0.3, 0.5, 1.0) and `min_samples` (3, 5).
   - I visualized the resulting cluster assignments, including noise points (labeled as -1).
   - I calculated clustering metrics such as the **Silhouette Score** (excluding noise), **Homogeneity Score**, and **Completeness Score** for each parameter setting.

4. **Analysis & Observations**
   - I compared the groupings produced by hierarchical and density-based methods.
   - I found that Hierarchical Clustering yielded more defined clusters but required predefined cluster numbers.
   - DBSCAN automatically detected noise/outliers, but its performance was sensitive to the choice of `eps` and `min_samples`.
   - A comparison of strengths and weaknesses:
     - *Hierarchical*: Simple to interpret with dendrograms but rigid in terms of cluster count.
     - *DBSCAN*: Resilient to outliers and capable of detecting non-spherical clusters, though selecting the right parameters is challenging.

## Key Insights
- **Cluster Count of 3** in Hierarchical Clustering closely matched the true wine classes when visualized on the first two features.
- **DBSCAN** with **eps = 0.5** and **min_samples = 5** effectively balanced the identification of dense clusters while limiting the number of points classified as noise.
- The **Silhouette Scores** varied between methods, with Hierarchical Clustering generally showing higher scores on the selected features, while DBSCAN was better at detecting noise.

## Challenges & Decisions
- **Choosing `eps` for DBSCAN**: I used distance-to-nearest-neighbor plots to identify a potential "knee" point, but trial and error was still needed.
- **Interpreting the Dendrogram**: Truncating the dendrogram at p = 5 made it easier to read, though deciding which linkage distances to consider was a subjective choice.
- **Limitations of Metrics**: Silhouette Scores only apply to true clusters and not noise, and Homogeneity/Completeness rely on known ground truth labels, which aren't always available in real-world scenarios.

---

Feel free to clone this repository and run the notebook (`MSCS_634_Lab_5.ipynb`) to reproduce the results or experiment with different parameter settings.
