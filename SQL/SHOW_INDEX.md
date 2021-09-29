# 인덱스 확인하기 / 삭제하기

# **인덱스 확인하기**

```
**SHOW INDEXES IN 테이블명**
```

```sql
ANALYZE TABLE customers;
-- 테이블을 분석
SHOW INDEXES IN customers;
-- 테이블의 인덱스들의 정보를 출력
```

![https://postfiles.pstatic.net/MjAxOTA5MjdfODUg/MDAxNTY5NTEwMjI5ODcw.F9U7qURtf9yI8X5NjENNdSi7D3AAlJ6br95ORV7ItvMg.qCLwLfWbXuYDgsO5GVsUuATLRJIpmtRWZN0RHPUOA1Ug.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjdfODUg/MDAxNTY5NTEwMjI5ODcw.F9U7qURtf9yI8X5NjENNdSi7D3AAlJ6br95ORV7ItvMg.qCLwLfWbXuYDgsO5GVsUuATLRJIpmtRWZN0RHPUOA1Ug.PNG.drv98/image.png?type=w773)

## **PK 키는 자동으로 인덱스 생성**

```sql
SHOW INDEXES IN orders;
```

![https://postfiles.pstatic.net/MjAxOTA5MjdfMjA1/MDAxNTY5NTEwMjk5NTcw.I1oYkRC5tEatKtlvsRStETD4ZYKQjorUO4uIzPyUKNUg.F54lLV3mTrnxODpopj0tzJnfYWhQ8mSyn8VGqKGl_wog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjdfMjA1/MDAxNTY5NTEwMjk5NTcw.I1oYkRC5tEatKtlvsRStETD4ZYKQjorUO4uIzPyUKNUg.F54lLV3mTrnxODpopj0tzJnfYWhQ8mSyn8VGqKGl_wog.PNG.drv98/image.png?type=w773)

## **FK 키는 자동으로 인덱스 생성**

<br>

## **왼쪽 네비게이션 바에서도 확인 가능**

![https://postfiles.pstatic.net/MjAxOTA5MjdfMjg5/MDAxNTY5NTEwNDYyOTk4.V645TQiwgcrFciJ5mN3OR86zdHllzCn81c3Zv9sFGFQg.vC1TaqUsaKCIqfg19dM3sTrr2bk9YCVvIOyxVEoy3lAg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjdfMjg5/MDAxNTY5NTEwNDYyOTk4.V645TQiwgcrFciJ5mN3OR86zdHllzCn81c3Zv9sFGFQg.vC1TaqUsaKCIqfg19dM3sTrr2bk9YCVvIOyxVEoy3lAg.PNG.drv98/image.png?type=w773)

---

<br>

# **인덱스 삭제하기**


```
**ALTER TABLE 테이블명 DROP INDEX 인덱스명;**
```

## **오라클에서는 (  DROP INDEX 인덱스명 )**

```sql
CREATE INDEX idx_firstname ON customers(first_name);  -- 인덱스 생성
CREATE INDEX idx_lastname ON customers(last_name);    -- 인덱스 생성

SHOW INDEXES IN customers;                            -- 인덱스 확인
ALTER TABLE customers DROP INDEX idx_firstname;       -- 인덱스 삭제

SHOW INDEXES IN customers;
```

