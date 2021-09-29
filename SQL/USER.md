# 새 유저(User) 생성 / 조회 / 삭제

> ![https://postfiles.pstatic.net/MjAxOTEwMDNfNTMg/MDAxNTcwMDY4OTMzNDQw.-CsRYGBPIq5dXQ58bSbq7YGuMzwlSITpijnFY7_M9Rwg.LiQkhj5zHFYphQgsQNbTC-uJARMrmhuXTe61UoBDTQkg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfNTMg/MDAxNTcwMDY4OTMzNDQw.-CsRYGBPIq5dXQ58bSbq7YGuMzwlSITpijnFY7_M9Rwg.LiQkhj5zHFYphQgsQNbTC-uJARMrmhuXTe61UoBDTQkg.PNG.drv98/image.png?type=w773)

<br>

## **새 유저 생성**

**CREATE USER  유저이름@IP주소  IDENTIFIED BY  '비밀번호';** 

```sql
-- CREATE USER john@127.0.0.1
-- CREATE USER john@localhost
-- 유저이름 뒤에 @를 입력하지 않으면 어디서든 허용 (%)
CREATE USER john IDENTIFIED BY '1234'; -- 유저 존 생성과 비밀번호 1234 설정
```

---

<br>

## **유저 조회**

```sql
SELECT * FROM mysql.user;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjMy/MDAxNTcwMDg2MzQ5MzIz.uZYBD5s7kCbe4kjddVIl8qxb8C1ZsVOpJftoEi8Yf4wg.BDDHp0LbCmsd-4K3LVC6jBbPyvtlY-DRuzNfrBiEAeUg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjMy/MDAxNTcwMDg2MzQ5MzIz.uZYBD5s7kCbe4kjddVIl8qxb8C1ZsVOpJftoEi8Yf4wg.BDDHp0LbCmsd-4K3LVC6jBbPyvtlY-DRuzNfrBiEAeUg.PNG.drv98/image.png?type=w773)

**왼쪽 네비게이터에서 확인방법**

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTA4/MDAxNTcwMDg2NTU2Nzg1.C7upPsSPWd3vODntA9cfX9CaMieJrsJqQnJUAF4H99Qg.KOce6UFbXf14yvVHM2yaamJ0MPBkOKPsvjUJZeMqAk8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTA4/MDAxNTcwMDg2NTU2Nzg1.C7upPsSPWd3vODntA9cfX9CaMieJrsJqQnJUAF4H99Qg.KOce6UFbXf14yvVHM2yaamJ0MPBkOKPsvjUJZeMqAk8g.PNG.drv98/image.png?type=w773)

---

<br>

## **유저 삭제**

```sql
DROP USER 유저이름@IP주소;
```
