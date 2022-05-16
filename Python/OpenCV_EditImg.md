# 이미지 수정

# 이미지 자르기

영역을 잘라서 새로운 윈도우(창)에 표시

```python
import cv2
img = cv2.imread('img.jpg')
# img.shape # (390, 640, 3)

crop = img[100:200, 200:400] # 세로 기준 100 : 200까지, 가로 기준 300 : 400 까지 자름

cv2.imshow('img', img) # 원본 이미지
cv2.imshow('crop', crop) # 잘린 이미지
cv2.waitKey(0)
cv2.destroyAllWindows()
```

영역을 잘라서 기존 윈도우에 표시

```python
import cv2
img = cv2.imread('img.jpg')
# img.shape # (390, 640, 3)

crop = img[100:200, 200:400] # 세로 기준 100 : 200까지, 가로 기준 300 : 400 까지 자름
img[100:200, 400:600] = crop

cv2.imshow('img', img) # 원본 이미지
cv2.waitKey(0)
cv2.destroyAllWindows()
```

# 이미지 대칭

## 좌우 대칭

```python
import cv2
img = cv2.imread('img.jpg')
flip_horizontal = cv2.flip(img, 1) # flipCode > 0 : 좌우 대칭 Horizontal

cv2.imshow('img', img)
cv2.imshow('flip_horizontal', flip_horizontal)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 상하 대칭

```python
import cv2
img = cv2.imread('img.jpg')
flip_vertical = cv2.flip(img, 0) # flipCode == 0 : 상하 대칭 Vertical

cv2.imshow('img', img)
cv2.imshow('flip_vertical', flip_vertical)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 상하좌우 대칭

```python
import cv2
img = cv2.imread('img.jpg')
flip_both = cv2.flip(img, -1) # flipCode < 0 : 상하좌우 대칭 

cv2.imshow('img', img)
cv2.imshow('flip_both', flip_both)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

# 9. 이미지 회전

## 시계 방향 90도 회전

```python
import cv2
img = cv2.imread('img.jpg')

rotate_90 = cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE) # 시계 방향으로 90도 회전

cv2.imshow('img', img)
cv2.imshow('rotate_90', rotate_90)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 180도 회전

```python
import cv2
img = cv2.imread('img.jpg')

rotate_180 = cv2.rotate(img, cv2.ROTATE_180) # 시계 방향으로 90도 회전

cv2.imshow('img', img)
cv2.imshow('rotate_180', rotate_180)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 시계 반대 방향 90도 회전

```python
import cv2
img = cv2.imread('img.jpg')

rotate_270 = cv2.rotate(img, cv2.ROTATE_90_COUNTERCLOCKWISE) # 시계 반대 방향으로 90도 회전

cv2.imshow('img', img)
cv2.imshow('rotate_270', rotate_270)
cv2.waitKey(0)
cv2.destroyAllWindows()
```








