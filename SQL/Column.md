# 컬럼 속성 알아보기

![https://postfiles.pstatic.net/MjAxOTA5MThfMjkw/MDAxNTY4NzYyMTM3MDM0.21Eu4DgrG0mMlOOQ0_dTzSNS6j81ai9Y06eo7uSo_dcg.4o9724d8ohEVi479rLb6y6_c53ysY6Joi7jwaLvymS0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjkw/MDAxNTY4NzYyMTM3MDM0.21Eu4DgrG0mMlOOQ0_dTzSNS6j81ai9Y06eo7uSo_dcg.4o9724d8ohEVi479rLb6y6_c53ysY6Joi7jwaLvymS0g.PNG.drv98/image.png?type=w773)

customers 테이블의 디자인 모드를 클릭하여 아래와 같이 컬럼 속성의 정보를 얻는다.

![https://postfiles.pstatic.net/MjAxOTA5MTRfNjMg/MDAxNTY4NDQ5NzAxMDg1.N6nslRSbKbeVaXRtXBO4MpSOEVL1wiDqWAY32BQbDFMg.5ft2xJvTEL-b_46xBNbkA3QZVaH97-WDUueat2TGIfwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTRfNjMg/MDAxNTY4NDQ5NzAxMDg1.N6nslRSbKbeVaXRtXBO4MpSOEVL1wiDqWAY32BQbDFMg.5ft2xJvTEL-b_46xBNbkA3QZVaH97-WDUueat2TGIfwg.PNG.drv98/image.png?type=w773)

<br>

### INT(11)

int는 정수형으로 괄호안의 숫자와 관계없이 최대 10자리까지 정수를 표현

()안의 숫자는 ZF 옵션일때 숫자만큼 0을 채워준다.

<br>


### VARCHAR(50)

MAX 최대 50 바이트  (자동으로 넣은 문자열만큼 저장)

<br>


### DATE

년 - 월 - 일 (  0000-00-00 ~ 9999-12-31 )

<br>


### PK (기본키)

노란색 표시

<br>


### NN ( Not Null )

널값을 입력할수 없음, 즉 꼭 입력을 해야 함.

<br>


### AI ( Auto Increment )

자동으로 +1 증가하는 열, 입력하지 않아도 자동으로 1씩 증가

<br>


### Default/Expression

입력하지 않을시에 기본값 설정
