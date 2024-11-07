---
date created: Sat, Nov 2nd 2024, 10:37 pm
date modified: Sun, Nov 3rd 2024, 1:36 am
---

# Inverse CDF sampling

*Inverse CDF transformation* of "Bit Shuffling" creates arbitrary $X_i \sim f_\theta(x)$

$\huge$Reminder: If the CDF of $X_i$ is $F_X(x)$, then the PDF of $X_i$ is $f_X(x) = \overset{\text{if it exists...}}{\frac{d}{dx}F_X(x)}$$\huge$​
$$
\large
\begin{align*}
F_X(x) = \overset{\int_{-\infty}^x f_\theta(\tilde x) d\tilde x}{Pr\left(X_i \leq x\right)} & = {}   \overset{\color{red}{\text{
If the inverse exists...}}}{\overset{\text{Suppose }X_i = F_X^{-1}(U_i)}{Pr\left(F_X^{-1}(U_i) \leq x\right)}}\\
&=Pr\left(F_X(F_{X}^{-1}(U_i) \leq F_X(x)\right) \\
& = {} Pr\left(U_i \leq \underset{\in [0,1]}{F_X(x)}\right) = F_X(x)  \\

&\Longrightarrow \quad F_X^{-1}(U_i) \sim f_θ(x)

\end{align*}
$$
Good "Bit Shuffling" $U_i \sim U(0,1)$ **Pseudorandomness**

 is indistinguishable from **(actual true) Randomness**

# Rejection Sampling

$$
\begin{align}
\mathbb{P}(X\text{accepted}) & = \mathbb{P}\left(U\leq \frac{f(X)}{cg(X)}\right)
\\&=\int\mathbb{P}\left(U\leq \frac{f(X)}{cg(X)}\right|X=x)g(x)dx\\
&= \int\frac{f(x)}{cg(x)}g(x)dx\\
&= \frac{1}{c}\int f(x)dx
\end{align}
$$

$\int f(x)dx = 1$, so $\mathbb{P}(X\text{accepted}) = \frac{1}{c}$​

> ***Rejection sampling*** changes the *univariate* sampling problem $X \sim f_\theta(x)$ into a *two-dimensional* problem $(\tilde X,U) \sim \tilde f(\tilde x,u) = \tilde f_{\tilde \theta}(\tilde x) \tilde f(u)$ that samples according to the desired probabilities

$$
\begin{align*}
{Pr\left(\tilde X \leq x \;\big|\; U \leq \frac{f_\theta(\tilde X)}{c \tilde f_{\tilde \theta}(\tilde X)} \right)} & ={} Pr\left(\tilde X \leq x, U \leq \frac{f_\theta(\tilde X)}{c \tilde f_{\tilde \theta}(\tilde X)} \right) \Bigg/ Pr\left( U \leq \frac{f_\theta(\tilde X)}{c \tilde f_{\tilde \theta}(\tilde X)} \right)\\

& ={} \int_{-\infty}^{x} \int_{0}^{\frac{f_\theta(\tilde x)}{c \tilde f_{\tilde \theta}(\tilde x)}} \tilde f_{\tilde \theta}(\tilde x) \;du\; d\tilde x  \Bigg/  \int_{-\infty}^{\infty} \int_{0}^{\frac{f_\theta(\tilde x)}{c \tilde f_{\tilde \theta}(\tilde x)}} \tilde f_{\tilde \theta}(\tilde x) \;du\; d\tilde x \\

& ={} \int_{-\infty}^{x} {\frac{f_\theta(\tilde x)}{c }}  d\tilde x  \Bigg/  \int_{-\infty}^{\infty} {\frac{f_\theta(\tilde x)}{c }} d\tilde x  = \int_{-\infty}^{x} f_\theta(\tilde x) d\tilde x\\\\
& ={} F_\theta( x) \Longrightarrow CDF
\end{align*}
$$
