---
title: "1. 핀홀 카메라(Pinhole Camera)"
date: 2026-08-08
categories:
  - Computer Vision
---

# Pinhole Camera Model

컴퓨터 비전 분야에서 카메라를 **핀홀 카메라(Pinhole Camera)** 모델로 표현하는 가장 큰 이유는, 실제 카메라의 핵심적인 **3D $\to$ 2D 투영 원리**를 단순한 식으로 모델링할 수 있기 때문입니다.

실제 카메라에는 렌즈, 왜곡, 초점, 조리개, 센서 등 복합적인 요소가 많지만, 컴퓨터 비전에서는.   
**"3차원 공간의 점 $P(X,Y,Z)$가 이미지의 어느 위치 $p(x,y)$에 찍히는가?"**
에 대한 답을 구하기 위한 기본 모델로 사용합니다.    

---

### 3D-to-2D 투영 방정식

핀홀 모델에서는 공간 좌표와 이미지 좌표의 관계가 다음과 같이 표현됩니다.

$$
\begin{aligned}
x &= f\frac{X}{Z}, \qquad y = f\frac{Y}{Z}
\end{aligned}
$$

<table style="margin: 30px auto; border-collapse: collapse;">
  <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>공간좌표 (mm)</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$(X, Y, Z)$</td>
  </tr>
  <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>이미지 평면 기하학적 좌표 (mm)</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$(x,y)$</td>
  </tr>
    <tr>
    <td style="padding: 10px 20px; border: 1px solid #ccc;"><strong>초점거리 (mm)</strong></td>
    <td style="padding: 10px 20px; border: 1px solid #ccc;">$f$</td>
  </tr>
</table>


<div style="margin: 30px 0; text-align: center;">
  <img src="/images/pinhole_model.png"
       alt="핀홀 카메라"
       style="width: 500px; max-width: 100%; height: auto; display: inline-block;">

  <div style="margin-top: 10px; font-size: 0.85em; color: #666; text-align: center;">
    ▲ [그림] 핀홀 카메라 모델
  </div>
</div>
---

### 핀홀 모델의 원리 및 실제 렌즈와의 관계

 