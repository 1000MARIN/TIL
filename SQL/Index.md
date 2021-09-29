# 인덱스 소개

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjgx/MDAxNTY5NTA4MzYyMzky.x4ivg58Yrkt_GLou4uD2a7eRGdM-8aKr0rmGseXQ8dYg.GKToZppoWZdywltTFnt2yzbUevjG2HWcYQvS28TVMd8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjgx/MDAxNTY5NTA4MzYyMzky.x4ivg58Yrkt_GLou4uD2a7eRGdM-8aKr0rmGseXQ8dYg.GKToZppoWZdywltTFnt2yzbUevjG2HWcYQvS28TVMd8g.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTA5MjZfMTMz/MDAxNTY5NTA4NDI2MjY2.rKJTkgcj5n5mtvk0b-B1JwSQQZhdP8u6koOLj_TTn4Mg.avfJUhGc5dJ3rMZD_0PdHNw7L_4aC5kc2KlAbWaa_uYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMTMz/MDAxNTY5NTA4NDI2MjY2.rKJTkgcj5n5mtvk0b-B1JwSQQZhdP8u6koOLj_TTn4Mg.avfJUhGc5dJ3rMZD_0PdHNw7L_4aC5kc2KlAbWaa_uYg.PNG.drv98/image.png?type=w773)

<br>

# **INDEX의 의미**

RDBMS에서 검색속도를 높이기 사용하는 하나의 기술입니다.

INDEX는 색인입니다. 해당 TABLE의 컬럼을 색인화(따로 파일로 저장)하여 검색시 해당 TABLE의 레코드를 full scan 하는게 아니라 색인화 되어있는 INDEX 파일을 검색하여 검색속도를 빠르게 합니다.

이런 INDEX는 TREE구조로 색인화합니다.

<br>

# **INDEX의 장점**

- 키 값을 기초로 하여 테이블에서 검색과 정렬 속도를 향상시킵니다.
- 질의나 보고서에서 그룹화 작업의 속도를 향상시킵니다.
- 테이블의 기본 키/외래키는 자동으로 인덱스 됩니다.

<br>

# **INDEX의 단점**

- 인덱스 된 필드에서 데이터를 (DML 작업시) 업데이트하거나, 레코드를 추가 또는 삭제할 때 성능이 떨어집니다.
- 인덱스가 데이터베이스 공간을 차지해 추가적인 공간이 필요해진다. (DB의 10퍼센트 내외의 공간이 추가로 필요)
- 인덱스를 생성하는데 시간이 많이 소요될 수 있다.
- 데이터 변경 작업이 자주 일어날 경우에 인덱스를 재작성해야 할 필요가 있기에 성능에 영향을 끼칠 수 있다.

<br>

따라서 어느 필드를 인덱스 해야 하는지 미리 시험해 보고 결정하는 것이 좋습니다. 인덱스를 추가하면 쿼리 속도가  빨라지지만, 데이터 행을 추가하는 속도는  느려지게 됩니다.

<br>

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjYg/MDAxNTY5NTA4NDcyMzQ5.LCC3giSlw_ceGTaJ7GmlKhYZ99zwANRXNli-biQVd3Ag.CdwS2ManvPEM6uTa2dzenGCYFZjN8Do8IpJJJyovSyQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjYg/MDAxNTY5NTA4NDcyMzQ5.LCC3giSlw_ceGTaJ7GmlKhYZ99zwANRXNli-biQVd3Ag.CdwS2ManvPEM6uTa2dzenGCYFZjN8Do8IpJJJyovSyQg.PNG.drv98/image.png?type=w773)
