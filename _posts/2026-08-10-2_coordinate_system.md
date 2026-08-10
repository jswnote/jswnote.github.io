---
title: "2. 좌표계(Coordinate System)"
date: 2026-08-10
categories:
  - Computer Vision
---

# Coordinate System

영상 기하학이란? 쉽게 말해 3차원 공간의 물체가 카메라를 통해 2차원 영상에 어떻게 투영되는지를 기하학적으로 다루는 것. 다양한 비전 분야에서 가장 기본이 되는 요소.

영상 기하학에서 4개의 좌표계로 분류.

<div style="padding: 50px 0; text-align: center;">
  <figure style="margin: 0;">
    <img src="/images/coordiante.png" alt="좌표계" width="220">
    <figcaption style="margin-top: 12px; font-size: 0.85em; color: #666;">
      ▲ [그림] 영상 기하학 좌표계 시스템
    </figcaption>
  </figure>
</div>

> **Note: 좌표축 설정**
> 
> <small>


### 월드 좌표계
기준이 되는 임의의 3차원 절대 공간 좌표계. 여러 객체나 카메라의 위치를 통합 관리할 때 사용.
단위 : mm, m ....
$\small P(X, Y, Z)$

### 카메라 좌표계
카메라를 기준으로 한 좌표계. 렌즈 중심(초점)을 원점으로 삼는 3차원 좌표계. 
3D 공간점을 카메라 시점으로 변환한 위치.
단, 단위는 월드 좌표계와 같은 단위 사용.
$\small P_c(X_c, Y_c, Z_c)$

### 픽셀 좌표계
최종 디지털 이미지의 좌측 상단을 원점으로 하고, 센서의 픽셀 단위로 환산한 2차원 좌표계.
단위 : 픽셀
$\small P_img(x, y)$

### 정규(평면) 좌표계
카메라의 내부 파라미터(intrinsic parameter)의 영향을 제거한 이미지 좌표계 및 좌표계의 단위를 없앤 초점거리가 1인 가상의 이미지 평면.
완전히 같은 위치에서 똑같은 이미지를 촬영하더라도 사용한 카메라에 따라서 서로 다른 영상을 갖게됨.
<strong style="color: red;">
이러한 카메라 고유의 성질인 내부 파라미터를 통해 불필요한 요소를 제거하여 정규화된 이미지 평면에서 공통된 기하학적 특성을 분석 가능.
</strong>
정규 좌표계의 원점은 광학축과의 교점.
$\small P^'(u, v)$

<div style="padding: 50px 0; text-align: center;">
  <figure style="margin: 0;">
    <img src="/images/normalized_plane.png" alt="정규 좌표계" width="500">
    <figcaption style="margin-top: 12px; font-size: 0.85em; color: #666;">
      ▲ [그림] 정규 좌표계 과정
    </figcaption>
  </figure>
</div>