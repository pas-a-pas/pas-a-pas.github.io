---
layout: post
title:  Least-squares solutions (full-rank case)
date:   2019-08-06 14:37:11 +0900
---
$\mathsf{Ax = b}$의 m x n행렬 A에서 m > n일때, 즉 미지수보다 방정식이 더 많은 경우(overdetermined case), 
모든 식을 완벽하게 만족시키는 해가 존재하지 않는다. $\mathsf{Ax = b}$, 다시 말해 $\mathsf{Ax - b = 0}$의 해가 존재하지 않을 때 
$\mathsf{Ax - b}$를 0에 가깝게 만드는 근접한 해 x를 구하는 것은 여전히 의미가 있다. 
$\mathsf{\left\lVert Ax - b \right\rVert}$를 최소화 시키는 근접한 해 x를 *least-squares solution*이라고 하고, SVD를 사용하여 구할 수 있다.

$\mathsf{\left\lVert Ax - b \right\rVert}$를 최소화하는 x를 구해보자.
SVD분해한 $\mathsf{A = UDV^T}$로 치환하면

$$\mathsf{
\left\lVert UDV^Tx - b \right\rVert
}$$

각 항에 $\mathsf{U^T}$를 곱하여도 norm값은 보존된다. 직교행렬의 속성 $\mathsf{U^TU = I}$에 따라 정리하면:

$$\mathsf{
\left\lVert DV^Tx - U^Tb \right\rVert
}$$

$\mathsf{V^Tx = y}$로, $\mathsf{U^Tb = b'}$로 치환하여 식을 다시 써보면:

$$\mathsf{
\left\lVert Dy - b’ \right\rVert
}$$

$\mathsf{\left\lVert Ax - b \right\rVert}$를 최소화하는 x를 찾는 문제가
$\mathsf{\left\lVert Dy - b’ \right\rVert}$를 최소화하는 y를 찾는 문제가 되었다.
$\mathsf{Dy = b’}$을 행렬식으로 다시 풀어 써보자. 5x3 행렬 형태를 예로 들자면:

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
=
\begin{pmatrix}
b'_1\\
b'_2\\
b'_3\\
b'_4\\
b'_5\\
\end{pmatrix}
$$

$\mathsf{\left\lVert Dy - b’ \right\rVert}$를 최소화하는 Dy는 b'에 가장 근접한 벡터 $(b'_1, b'_2, b'_3, 0, 0)^T$이며
$y_i = b’_i / d_i$를 통해 y를 계산해낼 수 있다.

찾고자하는 최종 해 x는 수식 x = Vy를 통해 계산한다.

출처 : Multiple View Geometry in Computer Vision, Second Edition (Appendix 5)
