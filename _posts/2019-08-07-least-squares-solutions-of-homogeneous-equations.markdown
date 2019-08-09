---
layout: post
title:  Least-squares solutions of homogeneous equations
date:   2019-08-07 17:27:11 +0900
---
$\mathsf{Ax = 0}$꼴의 homogeneous equations에서 m x n행렬 A가 m > n일때, 
즉 미지수보다 방정식이 더 많은 경우(overdetermined case)를 보자. 
$\mathsf{Ax}$를 $\mathsf{0}$으로 만드는 정확한 non-zero 해 x가 존재하지 않기 때문에
$\mathsf{\left\lVert Ax \right\rVert}$를 최소화하는 해 x를 찾는다([Least-squares solutions](../../../2019/08/06/least-squares-solutions.html)). $\mathsf{x = 0}$이 해로 찾아지는 것을 피하기 위해 $\mathsf{\left\lVert x \right\rVert = 1}$ 제약을 걸게된다.
해 x에 대해 임의의 상수 $k$를 곱한 $k\mathsf{x}$역시 해가 되기 때문이다.(*x is only defined up to scale*)

$\mathsf{\left\lVert x \right\rVert = 1}$ 조건하에 $\mathsf{\left\lVert Ax \right\rVert}$를 최소화하는 x를 SVD를 이용하여 찾아보자. $\mathsf{A = UDV^T}$로 SVD분해하여 식을 다시 써보면:

$$\mathsf{\left\lVert UDV^Tx \right\rVert}$$

U, $\mathsf{V^T}$ 가 직교단위벡터(Orthonormal vector)들의 행렬임을 상기하면:

$$\mathsf{\left\lVert UDV^Tx \right\rVert = \left\lVert DV^Tx \right\rVert},  \mathsf{\left\lVert x \right\rVert = \left\lVert V^Tx \right\rVert}$$

$\mathsf{V^Tx = y}$로 치환하여 식을 다시 써보면:

$$\mathsf{\left\lVert Dy \right\rVert},  \mathsf{\left\lVert y \right\rVert}$$

$\mathsf{\left\lVert x \right\rVert = 1}$ 조건하에 $\mathsf{\left\lVert Ax \right\rVert}$를 최소화하는 x를 찾는 문제가
$\mathsf{\left\lVert y \right\rVert = 1}$ 조건하에 $\mathsf{\left\lVert Dy \right\rVert}$를 최소화하는 y를 찾는 문제가 되었다. 

대각행렬 D에 대한 Dy를 행렬식으로 풀어써 보자. 5x3 행렬 형태를 예로 들자면:

$$
\begin{bmatrix}
d_1&0&0\\
0&d_2&0\\
0&0&d_3\\
0&0&0\\
0&0&0\\
\end{bmatrix}
\begin{pmatrix}
y_1\\
y_2\\
y_3\\
\end{pmatrix}
$$

SVD분해된 대각행렬 D는 관례적으로 대각 요소들이 내림차순으로 채워진다.($d_i > d_{i+1}$) 
따라서 $\mathsf{\left\lVert Dy \right\rVert}$를 가장 작게 만드는 크기가  1인 y는 가장 작은 대각 요소만을 활성화하는 
$(0, \cdots, 0, 1)^T$이다. 최종해 x는 $\mathsf{Vy}$로 구할 수 있고, y가 마지막 요소를 제외한 모든 요소가 0인 벡터임을 상기했을때, 해 x는 V의 마지막열 임을 알수 있다.
결국 Homogeneous equations을 Least-squares solutions으로 찾아야 할때, A를 $\mathsf{UDV^T}$분해한 후 V의 마지막열을 취하면 된다.

Homogeneous equations은 고유값분해(Eigen-decomposition)을 통해서도 풀 수 있다.

$$\mathsf{A^TA = VD^TU^TUDV^T = VD^TDV^T = VD^2V^T}$$

임을 상기해 보자. 직교행렬 Q에 대해 $\mathsf{Q^TQ = I}$임에 근거하여 고유값 분해식 $\mathsf{A = S\Lambda S^{-1}}$과 상통하는 것을 알수 있다.
즉, V는 $\mathsf{A^TA}$의 고유벡터 행렬이며, Homogeneous equations $\mathsf{Ax = 0}$의 해는 $\mathsf{A^TA}$의 가장 작은 고유값에 대한 고유벡터이다.
*Given Ax = 0, find the eigenvector of $\mathsf{A^TA}$ with smallest eigenvalue. That's x.*

출처:
 * Multiple View Geometry in Computer Vision, Second Edition (Appendix 5)
 * Udacity Introduction to Computer Vision (3C-L3)
