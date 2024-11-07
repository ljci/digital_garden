---
tags:
  - math/LinearAgebra
date created: Sat, Feb 24th 2024, 5:32 am
date modified: Sun, Nov 3rd 2024, 1:36 am
---

L2 norm $\Vert x \Vert_{2}$ has to be $x^Tx$ , dot product

dot product: $$\begin{bmatrix}1\\2\\3\end{bmatrix} \cdot \begin{bmatrix}
1\\2\\3\end{bmatrix} = 1\cdot 1+2\cdot 2+3\cdot 3=1+4+9=14$$
outer product:
$$
\begin{bmatrix}
1&2&3\\1&2&3\\1&2&3
\end{bmatrix}\cdot \begin{bmatrix}
1&2&3\\1&2&3\\1&2&3
\end{bmatrix}=\begin{bmatrix}
6&12&18\\6&12&18\\6&12&18
\end{bmatrix}
$$

| inner/dot product | outer product     |
| ----------------- | ----------------- |
| result is scalar  | result  is Matrix |
|                   |                   |
|                   |                   |

The matrix is invertible(singular matrix) if its  $det \neq 0$ , invertible means if it has inverse or not; so if the matrix has inverse, then its det must not be 0.($A^{−1}$ exists ⇔ $det(A) \neq 0$).

The matrix is non-singular if its $det \neq 0$ (Determinant Test for Non-Singularity), otherwise it's singular

# Determinant

### Property of Determinant

**DETERMINANT PROPERTY 1:** If every element in a row or column of a matrix is 0, then the determinant equals 0.
$$
det\left(\begin{vmatrix}
2 & 4 \\
0 & 0
\end{vmatrix}\right) = 0
$$
**DETERMINANT PROPERTY 2:** If corresponding rows and columns of a matrix are interchanged, the determinant is not changed.
$$
det\left(\begin{vmatrix}
1 & 3 \\
5 & 7
\end{vmatrix}\right) =
det\left(\begin{vmatrix}
1 & 5 \\
3 & 7
\end{vmatrix}\right) =
1*7-3*5 = -8
\\
\
$$
so, by property 2, we have $det(A) = det(B) = det(A^{T})$
$$
A=\left[\begin{array}{rrr}
2 & 1 & 6 \\
3 & 0 & 5 \\
-4 & 6 & 9
\end{array}\right] \quad \text { and } \quad B=\left[\begin{array}{rrr}
2 & 3 & -4 \\
1 & 0 & 6 \\
6 & 5 & 9
\end{array}\right]
$$

**DETERMINANT PROPERTY 3:** Interchanging two rows (or columns) of a matrix reverses the sign of the determinant.
**DETERMINANT PROPERTY 4:** If every element of a row (or column) of a matrix is multiplied by the real number k, then the determinant of the new matrix is k times the determinant of the original matrix.
**DETERMINANT PROPERTY 5:**  The determinant of a matrix with two identical rows (or columns) equals 0.
**DETERMINANT PROPERTY 6:** The determinant of a matrix is unchanged if a multiple of a row (or column) of the matrix is added to the corresponding elements of another row (or column).
**DETERMINANT PROPERTY 7：** The determinant of a triangular matrix is a product of its principal diagonal elements.
$$
A=\left(\begin{array}{rrrr}4 & -2 & 6 & 2 \\ 0 & -1 & 5 & -3 \\ 2 & -1 & 8 & -2 \\ 0 & 0 & 0 & 2\end{array}\right)
$$

Subtracting the first row, divided by 2, from the third row, we get

$$
\begin{aligned}
& \operatorname{det} A =\left(\begin{array}{rrrr}
4 & -2 & 6 & 2 \\
0 & -1 & 5 & -3 \\
2 & -1 & 8 & -2 \\
0 & 0 & 0 & 2
\end{array}\right) =2 \cdot \operatorname{det}\left(\begin{array}{rrrr}
2 & -1 & 3 & 1 \\
0 & -1 & 5 & -3 \\
2 & -1 & 8 & -2 \\
0 & 0 & 0 & 2
\end{array}\right)=2 \cdot \operatorname{det}\left(\begin{array}{rrrr}
2 & -1 & 3 & 1 \\
0 & -1 & 5 & -3 \\
0 & 0 & 5 & -3 \\
0 & 0 & 0 & 2
\end{array}\right)=2 \cdot 2 \cdot(-1) \cdot 5 \cdot 2=-40
\end{aligned}
$$
Here, we make it as upper triangular matrix, then use the last property, multiple all the diagonal elements

**DETERMINANT PROPERTY 8：**  Two columns(rows) are proptional to each other, then the det is 0.

Example:

Without expanding, show that the determinant of the following matrix is zero.
$$
\left[\begin{array}{rrr} 2 & 5 & -1 \\ 1 & -15 & 3 \\ -2 & 10 & -2 \end{array}\right]
$$
Each element in the second column equals -5 times the corresponding element in the third column. Multiply the elements of the third column by 5 and then add the results to the corresponding elements in the second column to get a matrix with an equivalent determinant,
$$
\left[\begin{array}{rrr} 2 & 0 & -1 \\ 1 & 0 & 3 \\ -2 & 0 & -2 \end{array}\right] .
$$
By Property 1, the determinant of this matrix is zero.

Therefore, if two columns or two rows are proptional to each other, then the det is 0, can be simply proved by propetry 6 + 1

## Calculate the Determinant(To to edited)

for 2x2 and 3x3, its easy to calculate

what about $n\geq3$ matrix, what will be the faster way or at least temp fast way to calculate

Laplace expansion

---

# Rank, Linearly independent

The rank of a matrix A, $\operatorname{rank}(A)$ can be deﬁned as
– the maximum number of linearly independent rows;
– or the maximum number of linearly independent columns;
– or the order of the largest non-zero minor of A.

Vectors $a1, a2, . . . , ak$ are linearly dependent if and only if there exist numbers c1, c2, . . . , ck not all zero, such that $c1a1 + c2a2 + . . . + ckak = 0$.
If $c1 = c2 = ..ck = 0$, then they are linearly independent. if $c1 = 1, c2 = ..= ck = 0$, then they are still linear dependent according to the definition
$$
\operatorname{rank}\left(\begin{array}{rrr}1 & 3 & 2 \\ 2 & 6 & 4 \\ -5 & 7 & 1\end{array}\right)=2
$$
The ﬁrst two rows are linearly dependent, therefore the maximum number of linearly independent rows is equal to 2.

## Properties of the Rank

1. The column rank and the row rank of a matrix are equal.
2. $rank(AB) ≤ min(rank(A), rank(B))$.
3. $rank(A) = rank(AA^{T}) = rank(A^{T}A)$.
4. Using the notion of rank, we can re-formulate the condition for non-singularity:
   1. If A is a square matrix of order n, then $rank(A) = n$​ ⇔ $det(A)\neq0$​ .

# Systems of Linear Equations[^1]

How to Solve a Linear System $A x=b$​ (general rules):

$b=\mathbf{0}$ (homogeneous case)
If $\operatorname{det}(A) \neq 0$ then the system has a unique trivial (zero) solution.
If $\operatorname{det}(A)=0$​ then the system has an infinite number of solutions.

$b \neq \mathbf{0}$​​ (non-homogeneous case)
If $\operatorname{det}(A) \neq 0$​​ then the system has a unique solution.
If $\operatorname{det}(A)=0$​​ then:
 a).  $\operatorname{rank}(A)=\operatorname{rank}(\tilde{A}) \Rightarrow$​​ the system has an infinite number of solutions.
 b).  $\operatorname{rank}(A) \neq \operatorname{rank}(\tilde{A}) \Rightarrow$​​ the system is inconsistent.

## Augmented matrix

Here $\tilde{A}$ is a so-called augmented matrix, $\tilde{A}=\left(\begin{array}{lll|l} a_{11} & \ldots & a_{1 n} & b_1 \\ \vdots & & \vdots & \vdots \\ a_{n 1} & \ldots & a_{n n} & b_n \end{array}\right)$

Consider the system of equations:
$$
\begin{aligned} x+y+2 z & =2 \\ x+y+z & =3 \\ 2 x+2 y+2 z & =6 . \end{aligned}
$$

The coefficient matrix is $A=\left[\begin{array}{lll} 1 & 1 & 2 \\ 1 & 1 & 1 \\ 2 & 2 & 2 \end{array}\right]$, The augmented matrix is $(A \mid B)=\left[\begin{array}{lll|l} 1 & 1 & 2 & 2 \\ 1 & 1 & 1 & 3 \\ 2 & 2 & 2 & 6 \end{array}\right]$

The $(A-\lambda I)x  = 0$ implies that $A-\lambda I$ must be singluar matrix(non-invertible -det  = 0 ), this is beacuse that x is non-zero vector and the equation $(A-\lambda I)x  = 0$, therefore $det(A-\lambda I)$​

Singluar matrix is just the matrix that its det is 0, which is also called non-invertible matrix.

Row echelon Form(REF)
A matrix is in row echelon form (REF) if it satisfies the following three properties:

1. All nonzero rows are above any rows of all zeros.
2. Each leading (nonzero) entry of a row is in a column to the right of the leading (nonzero)
entry of the row above it. The leading entry is also called Pivot
3. All entries in a column below a leading (nonzero) entry are zeros.
Reduced Row Echelon (RREF)
A matrix is in reduced row echelon form (RREF) if it satisfies the following three
properties:
1. It is in REF;
2. The leading (nonzero) entry in each row is 1.
3. Each leading 1 is the only nonzero entry in its column.

Gaussian Elimination

## LU decomposition

Divide a matrix to L(lower triangular matrix) and U(upper triangular matrix), such that A = LU
unit lower triangular matrix L :  a square matrix with diagonal equals to 1 and elements above diagonal are all zeros; lower triangular matrix: a square matrix with elements above diagonal are all zero, diagonal not necessary be 1
upper triangular matrix: a square matrix with diagonal below are all zeros; If the diagonal of upper triangular matrix is 1, then it is unit upper triangular matrix
$$
\begin{aligned}
Ax = LUx \rightarrow & L=\left[\begin{array}{ccc}1 & 0 & 0 \\ l_{21} & 1 & 0 \\ l_{31} & l_{32} & 1\end{array}\right],U=\left[\begin{array}{ccc}u_{11} & u_{12} & u_{13} \\ 0 & u_{22} & u_{23} \\ 0 & 0 & u_{33}\end{array}\right]
\end{aligned}

$$
$$
\begin{aligned}
& a_{11} x_1+a_{12} x_2+a_{13} x_3=b_1 \\
& a_{21} x_1+a_{22} x_2+a_{23} x_3=b_2 \\
& a_{31} x_1+a_{32} x_2+a_{33} x_3=b_3
\end{aligned}
$$

These can be written in the form of $A X=B$ as:
$$
\left[\begin{array}{lll}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{array}\right]\left[\begin{array}{l}
x_1 \\
x_2 \\
x_3
\end{array}\right]=\left[\begin{array}{l}
b_1 \\
b_2 \\
b_3
\end{array}\right]
$$

Here,
$$
A=\left[\begin{array}{lll}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{array}\right], X=\left[\begin{array}{l}
x_1 \\
x_2 \\
x_3
\end{array}\right], B=\left[\begin{array}{l}
b_1 \\
b_2 \\
b_3
\end{array}\right]
$$

1. find U(REF, Gaussian Elimination)
2. find L, look at the multipliers that are used to eliminate entries below the main diagonal when transforming A into U.

$$A=\left[\begin{array}{lll}
4,3\\6,3
\end{array}\right]$$
 To transform A into an upper triangular matrix U, we eliminate the 6 in the position a21​ by subtract 1.5 times Row 1 from the Row 2
$$L=\left[\begin{array}{}
1,0\\ 1.5,1
\end{array}\right]$$
3. set LZ = B to get Z
4. set Ux=Z to get x

Example of 4x4 matrix:
Let's perform an LU decomposition on a $4 \times 4$ matrix $A$. Here's an example:
$$
A=\left(\begin{array}{cccc}
1 & 2 & 4 & 3 \\
3 & 8 & 14 & 11 \\
2 & 6 & 13 & 9 \\
4 & 12 & 29 & 18
\end{array}\right)
$$

1. Transform $A$ into $U$
Eliminate $a_{21}, a_{31}$, and $a_{41}$ :
- To eliminate 3 under 1 (first column), multiply the first row by 3 and subtract it from the second row.
- To eliminate 2 under 1 , multiply the first row by 2 and subtract it from the third row.
- To eliminate 4 under 1 , multiply the first row by 4 and subtract it from the fourth row.

Proceed to the second column:
- Now focus on making the matrix below the main diagonal of the second column zeros, considering the matrix already modified in step 1.

And so on for the third column:
- You only need to eliminate $a_{43}$ in this step.

2. Construct $U$
The matrix $U$ is the result of these elimination steps. Since the actual arithmetic is not shown here, let's directly jump to constructing $L$ from the multipliers used.

3. Construct $L$
The matrix $L$ captures the multipliers used in each step:
For $a_{21}$, if the multiplier was 3 (you subtracted 3 times the first row from the second row), then $l_{21}=3$.
For $a_{31}$, if the multiplier was 2 , then $l_{31}=2$.
For $a_{41}$, if the multiplier was 4 , then $l_{41}=4$.
The process continues similarly for other subdiagonal elements based on the multipliers used.
$$
L=\left(\begin{array}{cccc}
1 & 0 & 0 & 0 \\
l_{21} & 1 & 0 & 0 \\
l_{31} & l_{32} & 1 & 0 \\
l_{41} & l_{42} & l_{43} & 1
\end{array}\right), \quad U=\left(\begin{array}{cccc}
u_{11} & u_{12} & u_{13} & u_{14} \\
0 & u_{22} & u_{23} & u_{24} \\
0 & 0 & u_{33} & u_{34} \\
0 & 0 & 0 & u_{44}
\end{array}\right)
$$

Gradient
$\nabla F(x,y,z) = (\frac{dF}{dx}, \frac{dF}{dy},\frac{dF}{dz})$
Example:
$$ \begin{gathered} F(x, y, z)=x+y^2+z^3 \\ \nabla F(x, y, z)=\left(\frac{d F}{d x}, \frac{d F}{d y}, \frac{d F}{d z}\right)=\left(1,2 y, 3 z^2\right) \end{gathered} $$ If we want to find the direction to move to increase our function the fastest, we plug in our current coordinates (such as 3,4,5) into the gradient and get: $$ \text { direction }=\left(1,2(4), 3(5)^2\right)=(1,8,75) $$
The gradient points to the direction of greatest increase;

# Eigenvalue and eigenvector

# dot product

$\begin{bmatrix}4\\1\end{bmatrix} \cdot \begin{bmatrix}2\\3\end{bmatrix}=4\cdot 2+1\cdot 3=11$
is same as matrix-vector multiplication:
$\begin{bmatrix}4&1\end{bmatrix}\begin{bmatrix}2\\3\end{bmatrix}=4*2+1*3=11$

![[PositiveSemiDefinite.png]]
![[positiveDefinite.png]]

# Reference

[^1]: A COOK-BOOK of MATH(Zotero)
[^2]: https://quickmath.com/pages/modules/matrices/determinant/index.php

[QuickMath](https://quickmath.com/pages/modules/matrices/determinant/index.php)
