# 3. 도형 그리기

## 빈 스케치북 만들기

```python
import cv2
import numpy as np

# 세로 480 X 가로 640, 3 Channel (RGB) 에 해당하는 스케치북 만들기
img = np.zeros((480, 640, 3), dtype=np.uint8)
# img[:] = (255, 255, 255) # 전체 공간을 흰 색으로 채우기
# print(img)
cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 일부 영역 색칠
```python
import cv2
import numpy as np

img = np.zeros((480, 640, 3), dtype=np.uint8)

# [세로 영역, 가로 영역]
img[100:200, 200:300] = (255, 255, 255)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 직선
직선의 종류 (line type)

1. cv2.LINE_4 : 상하좌우 4 방향으로 연결된 선
1. cv2.LINE_8 : 대각선을 포함한 8 방향으로 연결된 선 (기본값)
1. cv2.LINE_AA : 부드러운 선 (anti-aliasing)

```python
import cv2
import numpy as np
img = np.zeros((480, 640, 3), dtype=np.uint8)

COLOR = (0, 255, 255) # BGR : Yellow
THICKNESS = 3 # 두께

cv2.line(img, (50, 100), (400, 50), COLOR, THICKNESS, cv2.LINE_8)
cv2.line(img, (50, 200), (400, 150), COLOR, THICKNESS, cv2.LINE_4)
cv2.line(img, (50, 300), (400, 250), COLOR, THICKNESS, cv2.LINE_AA)
# 그릴 위치, 시작 점, 끝 점, 색깔, 두께, 선 종류

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 원

```python
import cv2
import numpy as np
img = np.zeros((480, 640, 3), dtype=np.uint8)

COLOR = (255, 255, 0) # BGR : 옥색
RADIUS = 50 # 반지름
THICKNESS = 10 # 두께

cv2.circle(img, (200, 100), RADIUS, COLOR, THICKNESS, cv2.LINE_AA) # 속이 빈 원
cv2.circle(img, (400, 100), RADIUS, COLOR, cv2.FILLED, cv2.LINE_AA) # 속이 꽉찬 원
# 그릴 위치, 원의 중심점, 반지름, 색깔 두께, 선 종류

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 사각형

```python
import cv2
import numpy as np
img = np.zeros((480, 640, 3), dtype=np.uint8)

COLOR = (0, 255, 0) # BGR : 초록색
THICKNESS = 10 # 두께

cv2.rectangle(img, (100, 100), (200, 200), COLOR, THICKNESS) # 속이 빈 사각형
cv2.rectangle(img, (400, 100), (500, 200), COLOR, cv2.FILLED) # 속이 빈 사각형
# 그릴 위치, 왼쪽 위 좌표, 오른쪽 아래 좌표, 색깔, 두께

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
