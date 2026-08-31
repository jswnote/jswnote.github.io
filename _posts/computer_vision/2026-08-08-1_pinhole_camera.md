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
에 대한 기하학적 답을 구하기 위한 기본 모델로 사용합니다.    

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
    ▲ [그림] 핀홀 카메라 모델(이해를 돕기 위한 위아래 상 변환)
  </div>
</div>
---

### 핀홀 모델의 원리 및 실제 렌즈와의 관계
초점 거리 : 렌즈가 평행하게 들어오는 빛을 한 점에 모았을 때, 렌즈의 기준 위치에서 그 초점까지의 거리.
(카메라에서는 센서를 이미지가 선명하게 맺히는 위치에 놓기 때문에 거의 센서가 거의 초점 위치에 해당)   
따라서 렌즈에서 센서까지의 거리를 초점 거리라 표현합니다.   

따라서 실제 카메라는 렌즈가 빛을 굴절시켜 센서에 이미지를 만들고, 핀홀 카메라는 그 복잡한 렌즈 작용을 하나의 핀홀로 단순화해서 이미지 평면에 상이 맺힌다고 보는 모델이기 때문에 렌즈 중심과 핀홀이 대응되어 초점거리를 핀홀과 이미지 평면 사이의 거리로 대응시켜 사용합니다.   