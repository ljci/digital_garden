---
tags:
  - "#distributed_comp"
aliases: 
date created: Mon, Nov 4th 2024, 12:23 pm
date modified: Mon, Nov 4th 2024, 12:47 pm
---
can sample without knowing the total number of datapoints

1. randomly select K samples from dataset
2. initialize reservoir $R =\{{r_{1},r_{2},...r_{k}} \}$, where $r_k$=$x_{k}$ for k = 1...K
3. for new input $x_{i}$ , and i > K, uniformly generate j from $\{1\dots i\}$.
4. if $j \leq K$, set $r_{j}$to $x_{i}$