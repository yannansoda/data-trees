---
{"topic":"Math","dg-publish":true,"permalink":"/StudyNotes/Matrix basics/","dgPassFrontmatter":true,"noteIcon":""}
---


# Dot product (projection product)

## Properties
#TODO: add examples here
- commutative
- distribute over addition
- associative over scalar multiplication

## Cosine & dot product
$$
A·B = |A| |B| cos\theta
$$

## Projection
- scalar projection (B projected on A) => a number (vector size) as result
$$
\frac{A·B}{|A|} = |B| cos\theta 
$$
- vector projection (B projected on A) => a vector as result
$$
\frac{A·B}{|A|} \frac{A}{|A|} = \frac{A·B}{A ·A} A = \frac{A·B}{|A|^2} A
$$


## Changing basis
Basis is a set of n vectors which are linearly independent and form an n-dimensional space, i.e. if a, b, and c are linearly independent, for any $p_a$ and $p_b$:

$$
c \neq p_a a + p_b b 
$$

According to vector projection formula, project A on the new basis $(k_1, k_2)$:
$$
A = \frac{A·k_1}{|k_1|^2} k_1 + \frac{A·k_2}{|k_2|^2} k_2
$$
thus, A in the new basis is:
$$
A_k = [\frac{A·k_1}{|k_1|^2}, \frac{A·k_2}{|k_2|^2}]
$$

## Application of changing basis
[[PCA\|PCA]]

# Matrix multiplication 

Matrices make transformations on vectors, potentially changing their magnitude and direction.

Key to solving simultaneous equation problems is appreciating how vectors are transformed by matrices, which is the heart of linear algebra.


## Matrix Inverses
**Gaussian elimination**, also known as row reduction, is an algorithm in linear algebra for solving a system of linear equations.

For 
$$ A \left(\begin{array}{cc} 
a \\ b \\ c\\
\end{array}\right) = S$$
The idea is using row operations on both A and S until A has a row echelon form:
$$
\left(\begin{array}{cc} 
1 & * & *\\
0 & 1 & *\\
0 & 0 & 1
\end{array}\right)
$$
then you can calculate $a, b, c$.

Gaussian elimination can help in calculating inverse matrix $A^{-1}$ of $A$ by tranforming:
$$
\left(\begin{array}{cc} 
A | I
\end{array}\right)
$$
-> 
$$
\left(\begin{array}{cc} 
I | A^{-1}
\end{array}\right)
$$
## Determinant
For 
$$
A = \left(\begin{array}{cc} 
a & b \\
c & d
\end{array}\right)
$$
the determinant is
$$
det(A) = |A| = ad - bc
$$
when $det(A) = 0$, $\left(\begin{array}{cc} 
a \\c 
\end{array}\right)$ and $\left(\begin{array}{cc} 
b \\d
\end{array}\right)$ are linear dependent and unable to apply Gaussian elimination.