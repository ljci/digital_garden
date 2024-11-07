---
date created: Sun, Nov 3rd 2024, 8:44 pm
date modified: Tue, Nov 5th 2024, 6:09 pm
tags: []
aliases:
  - GMM
---
Motivation:
use a gaussian model to measure one mode data, need more gaussian model to measure multiple modes data. mode, means peak of a distribution

Gaussian Mixture model is the combination of multiple gaussian distribution together with $\pi_{k}$as the weight to weight each gaussian distribution.

Latent Variable

# MLE for GMM

## EM Algorithm

Reference
[GMM derivation for diagonal covariance matrices](https://stats.stackexchange.com/questions/642249/gmm-derivation-for-diagonal-covariance-matrices)

# GMM vs K-means

GMM can be simplified as K-means, GMM is the soft version of K-means as one datapoint can belong to multiple clusters(e.g datapoint near overlapping clustering )

# Related

[[Maximum Likelihood Estimation]]
[[EM Algorithm]]