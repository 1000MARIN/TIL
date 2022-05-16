# 5. 파일 저장

## 이미지 저장

```python
import cv2
img = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE) # 흑백으로 이미지 불러오기
cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()

result = cv2.imwrite('img_save.jpg', img)
print(result)
```

### 저장 포맷 (jpg, png)

```python
import cv2
img = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE) # 흑백으로 이미지 불러오기
cv2.imwrite('img_save.png', img) # png 형태로 저장
```

```
True
```

## 동영상 저장

```python
import cv2
cap = cv2.VideoCapture('video.mp4')

# 코덱 정의
fourcc = cv2.VideoWriter_fourcc(*'DIVX')

width = round(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = round(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
fps = cap.get(cv2.CAP_PROP_FPS) * 2 # 영상 재생 속도가 2배

out = cv2.VideoWriter('output_fast.avi', fourcc, fps, (width, height))
# 저장 파일명, 코덱, FPS, 크기 (width, height)

while cap.isOpened():
    ret, frame = cap.read()
    
    if not ret:
        break

    out.write(frame) # 영상 데이터만 저장 (소리X)  
    
    cv2.imshow('video', frame)
    if cv2.waitKey(1) == ord('q'):
        break
        
out.release() # 자원 해제        
cap.release()
cv2.destroyAllWindows()
```

```python
codec = 'DIVX'
print(codec)
print(*codec)
print([codec])
print([*codec])
```

```
DIVX
D I V X
['DIVX']
['D', 'I', 'V', 'X']
```
