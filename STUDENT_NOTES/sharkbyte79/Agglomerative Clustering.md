---
title: Agglomerative Clustering
date: 2025-02-17
course: CS506
author: pierce77@bu.edu
tags:
  - clustering
  - hierarchical
  - agglomerative
  - distance
---
# Agglomerative Clustering Algorithm
**Agglomerative clustering** is a type of [hierarchical clustering](Clustering.md#Hierarchical%20Clustering) that uses a *bottom-up* approach of constructing a dendrogram while repeatedly merging separate clusters into one.
1. Start with every point in its own cluster
2.  Compute the distance between all pairs of clusters
3. Merge the two nearest clusters
4. Repeat steps 2 and 3 until every point belongs to the same cluster

The *bottom-up* approach refers to the fact that the dendrogram is **built up** by successively combining data points from individual singleton[^1] clusters into one maximal cluster.[^2]

# Distance Functions for Agglomerative Clustering
## Single-Link Distance
The **min** of all pairwise [distances](Distance%20and%20Similarity.md) between a point from one cluster and a point from the other cluster.
- Can handle clusters of varying sizes
- Sensitive to noise points
- Tends to create elongated clusters
$$\Large{
D_{SL}(C_1, C_2) = \text{min}\{d(p_1, p_2) | p_1 \in C_1, p_2 \in C_2\}
}
$$

## Complete-Link Distance
The **max** of all pairwise distances between a point from one cluster and a point from the other cluster.
- Less susceptible to noise than [single-link](Agglomerative%20Clustering.md#Single-Link%20Distance)
- Creates more balanced clusters (equal diameter)
- Tends to split up large clusters
$$\Large{
D_{CL}(C_1, C_2) = \text{max}\{d(p_1, p_2) | p_1 \in C_1, p_2 \in C_2\}
}
$$

## Average-Link Distance
The **average** of all pairwise distances between a point from one cluster and a point from the other cluster.
- Less susceptible to noise and outliers
- Biased towards globular clusters
$$\Large{
D_{AL}(C_1, C_2) = (\frac{1}{|C_1| \cdot |C_2|}) \quad \cdot \sum_{p_1 \in C_1, p_2 \in C_2} d(p_1, p_2)
}
$$

## Centroid Distance
The distance between the centers of separate clusters.
$$\Large{
D_C(C_1, C_2) = d(\mu_1, \mu_2)
}
$$

## Ward's Distance
The difference between the spread of points in the merged cluster and the unmerged clusters.
$$\Large{
D_{WD}(C_1, C_2) = \sum_{p \in C_{12}} d(p, \mu_{12}) - \sum_{p_1 \in C_{1}} d(p_1, \mu_2) - \sum_{p_2 \in C_{2}} d(p_2, \mu_2)
}
$$

[^1]: informally, a cluster that contains a single data point.
[^2]: summarized from *An Introduction to Statistical Learning with Applications in Python*, 525-526