---
title: "3. 카메라 캘리브레이션(Camera Calibration)"
date: 2026-08-10
categories:
  - Computer Vision
---

# Camera Calibration

앞서 핀홀 카메라와 좌표계에 대해서 정리해 보았습니다. 앞서 언급한 핀홀 카메라의 공간 좌표와 이미지 좌표의 관계를 살펴보면.

$$
\begin{aligned}
x_s &= f\frac{X_c}{Z_c}, \qquad y_s = f\frac{Y_c}{Z_c}
\end{aligned}
$$

$P_c(X,Y,Z)$를 카메라 좌표계에서 바라본 3차원 공간 상의 점이라고 생각하면, $P_s(x_s, y_s)$는 이미지 센서 상에 맺히는 점이라고 생각할 수 있습니다.
만약 $P_c(X,Y,Z)$를 정규 좌표계$(점 $P_n(x_n, y_n)$)$에 대응시켜 보면, 초점 거리가 1이기 때문에 다음과 같이 나타낼 수 있습니다.

$$
\begin{aligned}
x_n &= frac{X_c}{Z_c}, \qquad y_s = frac{Y_c}{Z_c}
\end{aligned}
$$

이미지 상에 

