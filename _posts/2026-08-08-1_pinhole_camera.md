---
title: "1. 핀홀 카메라(Pinhole Camera)"
date: 2026-08-08
categories:
  - Computer Vision
---

# Pinhole Camera Model

컴퓨터 비전 분야에서 카메라를 **핀홀 카메라(Pinhole Camera)** 모델로 표현하는 가장 큰 이유는, 실제 카메라의 핵심적인 **3D $\to$ 2D 투영 원리**를 단순하고 명쾌한 수학으로 표현할 수 있기 때문입니다.

실제 카메라에는 렌즈, 왜곡, 초점, 조리개, 센서 등 복합적인 요소가 많지만, 컴퓨터 비전에서는 **"3차원 공간의 점 $P(X,Y,Z)$가 이미지의 어느 위치 $p(x,y)$에 찍히는가?"**에 대한 답을 구하기 위한 기본 모델로 사용합니다.

---

### 3D-to-2D 투영 방정식

핀홀 모델에서는 공간 좌표와 이미지 좌표의 관계가 다음과 같이 표현됩니다.

$$
\begin{aligned}
x &= f\frac{X}{Z} \\
y &= f\frac{Y}{Z}
\end{aligned}
$$

<table style="margin: 30px auto; border-collapse: collapse;">
  <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>공간좌표</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$(X, Y, Z)$</td>
  </tr>
  <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>y 이미지 좌표</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$(x,y)$</td>
  </tr>
    <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>초점거리</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$f$</td>
  </tr>
</table>


<div style="margin: 30px 0; text-align: center;">
  <img src="/images/pinhole_model.png"
       alt="핀홀 카메라"
       style="width: 250px; max-width: 100%; height: auto; display: inline-block;">

  <div style="margin-top: 10px; font-size: 0.85em; color: #666; text-align: center;">
    ▲ [그림] 핀홀 카메라 모델
  </div>
</div>
---

### 핀홀 모델의 원리 및 실제 렌즈와의 관계

핀홀 카메라는 하나의 구멍을 직선으로 통과하여 반대편 벽에 상이 맺히는 원리입니다. 컴퓨터 비전의 핀홀 카메라 모델에서는 **실제 렌즈의 중심을 '투영 중심(바늘구멍)'으로 근사**하여, 이 투영 중심에서 이미지 평면까지의 거리를 **초점거리 $f$**로 모델링합니다.

> **Note: 렌즈 중심과 핀홀의 대응 원리**
> 
> <small>원래 3차원 공간 상의 점은 여러 방향으로 빛을 반사합니다. 반사된 빛들 중 렌즈 범위에 들어오고 렌즈와 수평으로 들어오는 빛들이 한 점에 모이게 되는데, 그점을 초점이라 정의합니다.</small>
> 
> <small>수평하지 않은 빛들과 수평한 빛들은 최종적으로 렌즈에서 굴절되어 이미지 센서의 한 점으로 모입니다. 이때 **렌즈 중심을 통과하는 빛은 굴절 없이 직진하여 상을 맺으므로**, 핀홀의 바늘구멍과 대응되는 지점은 바로 **'렌즈 중심'**이 됩니다.</small>