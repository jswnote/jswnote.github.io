---
title: "3. 카메라 캘리브레이션(Camera Calibration)"
date: 2026-08-11
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

$P_c(X,Y,Z)$를 카메라 광학 중심에서 바라본 3차원 공간 상의 점이라고 생각하면, $P_s(x_s, y_s)$는 이미지 센서 상에 맺히는 점이라고 생각할 수 있습니다.
만약 $P_c(X,Y,Z)$를 정규 좌표계 $P_n(x_n, y_n)$에 대응시켜 보면, 초점 거리가 1이기 때문에 다음과 같이 나타낼 수 있습니다.

$$
\begin{aligned}
x_n &= \frac{X_c}{Z_c}, \qquad y_n = \frac{Y_c}{Z_c}
\end{aligned}
$$

이미지 상에 맺힌 좌표 $P_s(x_s, y_s)$는 mm 좌표이기 때문에 그 다음 센서의 mm를 pixel로 바꾸기 위해, 다음과 같이 이미지 센서에 따른 변환 과정을 거칩니다.

> **Note: 이미지 mm에서 픽셀 변환**
>
> <small>1μm = 0.001mm이므로 pixel size가 3μm x 3μm라면 다음과 같이 표현할 수 있습니다.</small>  
> <small>3μm = 0.003mm</small> 
> <small>따라서 한 픽셀의 크기는</small> 
> <small>s_x = s_y = 0.003 mm/pixel</small> 
> <small>이 됩니다.</small>
>
>
> <small>이미지 평면에서 어떤 점의 위치가 x[mm], y[mm]로 주어졌을 때, 이를 픽셀 단위의 거리로 변환하려면 pixel size로 나누면 됩니다.</small> 
> 
> $$ 
> u' = \frac{x}{s_x}, \quad
> v' = \frac{y}{s_y} 
> $$ 
> <small>이므로 이미지 중심으로부터 약 400 pixel 떨어진 위치에 해당합니다.</small> 
> 
> <small>단, u', v'는 이미지 중심(주점)을 기준으로 한 픽셀 거리이며, 실제 영상의 픽셀 좌표계는 보통 좌측 상단을 (0, 0)으로 사용하기 때문에 주점의 픽셀 좌표를 (c_x, c_y)라고 하면 실제 픽셀 좌표 (u, v)는 다음과 같이 표현할 수 있습니다.</small> 
>
> $$ 
> u = \frac{x}{s_x} + c_x 
> $$ 
> 
> $$ 
> v = \frac{y}{s_y} + c_y 
> $$ 
> 
> <small>즉, 이미지 평면의 mm 좌표를 pixel size로 나누어 픽셀 단위의 거리로 바꾸고, 여기에 주점 위치를 더하면 실제 영상의 픽셀 좌표를 얻을 수 있습니다.</small>
> <small>보통 초점거리 또한 디지털 카메라에서는 mm 단위로 표현되지만 카메라 모델에서는 픽셀 단위로 표현되기 때문에 다음과 같이 변환 작업이 이루어집니다.</small>
> $$ 
> f_x = \frac{f}{s_x}
> $$ 
> 
> $$ 
> f_y = \frac{f}{s_y}
> $$ 

> **Note: 데이터시트 픽셀에서 mm 변환**
>
> <small>이미지 센서나 렌즈의 데이터시트를 살펴보면 다음과 같은 항목들을 쉽게 볼 수 있습니다.</small>
>
> <small> - pixel size   
> - image area     
> - active array size <small>  
>
> <small>예를 들어 pixel size : 3μm x 3μm, resolution : 1600 x 1300 표기되어 있으면 현실 이미지 센서의 크기는 4.8mm x 3.9mm 정도를 나타냅니다.</small>
> <small>이를 데이터시트의 image area와 비교하면 4857.696μm x 3955.896μm으로 나와있고 반올림 차이 정도입니다.</small>

따라서 앞서 나온 식에

$$
\begin{aligned}
u = \frac{x}{s_x} + c_x, \qquad v = \frac{y}{s_y} + c_y
\end{aligned}
$$

각각 x,y를 

$$
\begin{aligned}
x &= f_x\frac{X_c}{Z_c}, \qquad y = f_y\frac{Y_c}{Z_c}
\end{aligned}
$$

대입해주면,  

$$
\begin{aligned}
u &= f_x\frac{X_c}{Z_c} + c_x, \qquad v = f_y\frac{Y_c}{Z_c} + c_y
\end{aligned}
$$

를 얻게 됩니다.