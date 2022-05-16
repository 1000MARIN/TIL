# 마우스 이벤트 등록

```python
import cv2

def mouse_handler(event, x, y, flags, param):
    if event == cv2.EVENT_LBUTTONDOWN: # 마우스 왼쪽 버튼 Down
        print('왼쪽 버튼 Down')
        print(x, y)
    elif event == cv2.EVENT_LBUTTONUP: # 마우스 왼쪽 버튼 Up
        print('왼쪽 버튼 Up')
        print(x,y)
    elif event == cv2.EVENT_LBUTTONDBLCLK: # 마우스 왼쪽 버튼 더블 클릭
        print('왼쪽 버튼 Double Click')
#     elif event == cv2.EVENT_MOUSEMOVE: # 마우스 이동
#         print('마우스 이동')
    elif event == cv2.EVENT_RBUTTONDOWN: # 마우스 오른쪽 버튼 Down
        print('오른쪽 버튼 Down')

img = cv2.imread('poker.jpg')
cv2.namedWindow('img') # img 란 이름의 윈도우를 먼저 만들어두는 것. 여기에 마우스 이벤트를 처리하기 위한 핸들러 적용
cv2.setMouseCallback('img', mouse_handler)
cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

```
왼쪽 버튼 Down
718 221
왼쪽 버튼 Up
718 221
왼쪽 버튼 Down
332 685
왼쪽 버튼 Up
332 684
왼쪽 버튼 Double Click
왼쪽 버튼 Up
332 683
오른쪽 버튼 Down
오른쪽 버튼 Down
```
