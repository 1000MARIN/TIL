# 이미지 변형 (흑백)

이미지를 흑백으로 읽음

```python
import cv2
img = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE)
cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

불러온 이미지를 흑백으로 변경

```python
import cv2
img = cv2.imread('img.jpg')

dst = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

cv2.imshow('img', img)
cv2.imshow('gray', dst)

cv2.waitKey(0)
cv2.destroyAllWindows()
```

# 이미지 변형 (흐림)

 ## 가우시안 
 
 커널 사이즈 변화에 따른 흐림
 
 ```python
 import cv2
img = cv2.imread('img.jpg')

# (3, 3), (5, 5), (7, 7)
kernel_3 = cv2.GaussianBlur(img, (3, 3), 0)
kernel_5 = cv2.GaussianBlur(img, (5, 5), 0)
kernel_7 = cv2.GaussianBlur(img, (7, 7), 0)

cv2.imshow('img', img)
cv2.imshow('kernel_3', kernel_3)
cv2.imshow('kernel_5', kernel_5)
cv2.imshow('kernel_7', kernel_7)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

표준 편차 변화에 따른 흐림

```python
import cv2
img = cv2.imread('img.jpg')

sigma_1 = cv2.GaussianBlur(img, (0, 0), 1) # sigmaX - 가우시안 커널의 x 방향의 표준 편차
sigma_2 = cv2.GaussianBlur(img, (0, 0), 2)
sigma_3 = cv2.GaussianBlur(img, (0, 0), 3)

cv2.imshow('img', img)
cv2.imshow('sigma_1', sigma_1)
cv2.imshow('sigma_2', sigma_2)
cv2.imshow('sigma_3', sigma_3)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


 
 
 
