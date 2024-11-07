---
tags:
  - ml
date created: Sat, Aug 17th 2024, 3:07 pm
date modified: Mon, Nov 4th 2024, 10:02 pm
---

Data has to be represented by vectors, matrix, tensor. Typically as dimension goes up, we need different forms to represent data for analysis or apply ml algorithm on them

Supervised learning, aims to make prediction, such as image recognition, weather prediction. It comes with inputs $xi$ and their corresponding labels $y_{i}$. while unsupervised learning aims to find the pattern of data/Understanding data

semi-supervised learning in which we learn from data but it has few labels, thus combination of supervised and unsupervised learning

large-scale reinforcement learning, reinforcement learning and supervised learning

Ordinal data: data with order, so we use embedding to preserve the order, typically real number
![[slide11.png]]
Nominal data: data without order, we want embedding to not introduce spurious ordering, such as one-hot embedding
![[slide12.png]]

Oracle is the true f that give the correct label. The oracle can be deterministic without noisy and random with noisy

Hypothesis space, spaces that consisting a set of candidate functions to find the best f^ approximation of f\*

We transfer above question into optimisation question (loss function) by comparing difference between output from candidate function and the true labels in loss function, thus to measure the performance of candidate functions.
![[slide1.png]]
As we don't know the true distribution and all data points, so we can only do Empirical Risk Minimisation

![[slide10.png]]
$\tilde{f}$ is the best approximator of oracle $f^{*}$in H

Three Problems of Machine Learning:

1. Approximation: how large is our hypothesis spaces? Does it include an at least contain functions that are vert close to oracle $f^*$.
   - The way to test approximation is approximation theory and harmonic analysis
2. Optimization: how can we find an get close to approximation $\hat{f}$ of $f^*$. This is empirical risk minimization problems
   1. The questions include the design of large-scale optimization algorithms , then convergence analysis, and then efficient implementation
   2. Math tool to solve: convex optimization
3. Generalization: Can $\hat{f}$ generalize to unseen samples? This concerns the fundamental interaction between the size of the dataset and the complexity of our hypothesis spaces
   1. Math tool to solve: Stats learning theory

![[slide9.png]]

# LinearModel

1D case of hypothesis space is SLR, w0,w1 as parameters. Goal is to find optimal values of w0,w1 that best fit the data
![[slide8.png]]

Overfitting, is that model is too powerful that it can fit the noise, can not generalize for unseen data

# Loss function

Mean square error, MSE
Huber loss
![[slide7.png]]

![[slide6.png]]
Why Huber loss is more robust to the outliers?
In MSE, when has outlier, loss comes larger as its squared, while for huber loss, the loss is linear, thus, smaller.

# Basis function

As SLR is limited due to 1D inputs and only measure the linear relationship, so we need to basis function for more general case.
When inputs are D dimension, basis function is to map it to bunch scalars, then apply linear model to scalar, basis function such as $\phi_{j}(x)= w_{i}^{T}x$
feature map = basis funcitions

basis function is just more generalized way to model all dimension data pts, if d = 1, M(paras = 2) = 2, choose basis function 1 and
$\phi \in R^{N\times M}$ = N data points and M feature maps

$\phi$ is a NxM matrix, whose rank is at most min(N,M)
$\phi^{T}\phi$ is a matrix of size MxM
Case 1: N>=M , $\phi^{T}\phi$ is invertible as long as the column of $\phi$ are linearly independent, which we should be able to sacrifice my appropriate choice of $\phi$(feature map)
Case2: N<M, rank of $\phi^{T}\phi$ is at most N < M --> $\phi^{T}\phi$ is not invertible, so we can not use formula, so we use Moore-Penrose presudoinverse, then we will have infinite solutions,

one choice to pick the one that has smallest norm $\lVert w \rVert$because we want to norm of the weight to small, we want to avoid the overfitting, and when there is sudden change, it changes small

# Regularization

regularization helps solve the singular case as it makes matrix invertible by adding regularizaton paras

# Classfiction

Regression: output has continuous values
Classification: output is nominal data, no oder, discrete values
![[slide5.png]]
for Classification: we want to output a vector of probability(cuz,0.5,0.6 as cat, scalars are limited, thus phi j is scalars, wj is vector, K is the # of the class I consider. Vector of prob, all values are prob with values could be 1. where g as activation function to normalize scalars to prob vector

We use entropy loss for classification problems
$$L(y^{\prime},y)=-\sum_{k=1}^{K}y_{k}\log y_{k}^{\prime}$$
$y'$ and $y$ must be non-negative and smaller or equal to 1 and sum of their entities should be 1

# Support Vector Machine

Laranage Multiplier

# Kernel Method

Kernel method is mapping the data to higher dimensional space or build the each feature corresponding new feature in high dimensional space to learn non-linear boundaries

Support vector machine is just the optimal margin classifer + kernel method/kernel trick. Using kernel method maps data to high dimensional space, and then find the optimal margin classfier on that transformed dimensional space to do classification
check this video [svm with polynomial kernel visualization](https://www.youtube.com/watch?v=OdlNM96sHio)

a function $k(x,x')$ can be used as kernel function only if there is $\phi$ s.t $k(x,x')=\phi(x)^T\phi (x')$

# Kernel Ridge Regression

Prove that $\phi^T\phi+\lambda I_{M}$ is always invertible for $\lambda>0$

the matrix is invertible if its eigenvalue is non-zero
WTS eigenvalues of $\phi^T\phi+\lambda I_{M}$ for $\lambda >0$ is non-zero always

No matter $\phi^{T}\phi$ is postive semi-definte or not(its eigenvalue is postive or not), the eigenvalue of $\lambda I_{M}$ is always positive. if eigenvalue of $\phi^{T}\phi$ is not positive, as long as $\lambda$ is big enough to compensate the negative effect from eigenvalues of $\phi^{T}\phi$, then the statement still works.

# Backpropogragion

[Backpropogragion](https://cs231n.stanford.edu/slides/2024/lecture_4.pdf)

