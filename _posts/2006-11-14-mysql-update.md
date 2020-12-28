---
toc: true
layout: post
description:
categories: [journal]
---
# Cafe24 신서버로 MySQL DB Migration

아, 나름대로 힘든 하루 였음.
아래는 세 줄 요약.

제로보드 5 베타판 설치를 위해 호스팅 업체인 Cafe24에 서버 이전을 요구함.
이전 된 신서버(MySQL 5.0)와 구서버(MySQL 3.23) 간의 DB 버전 차이로 백업한 DB가 복구가 안 됨.
반 나절의 닭질 끝에 해결했음 -_-v
언제나 너무나도 바쁠 때면, 괜시리 다른 일들이 눈에 밟힌다.
이번 제로보드 5 베타판 역시 마찬가지.

뒤늦게(8월에 발표된 것), 혹은 너무 일찍(버전 0.05-_-; ) 필이 꽂혀서 알아본 결과,
지금 호스팅 서버에서는 제로보드 5 베타를 설치가 불가능하고, 굳이 하려면 호스팅 업체에게 제로보드가 설치 가능한 서버로 이전해 달라고 요청하면 된단다.

그래서 바로 서버 이전을 요청하고, 모든 자료와 DB 백업을 해 두었다.
그리고 마침내 새 서버로 이전한 후, 홈페이지를 다시 복구 하려는 찰나!
다음과 같은 에러가 나며, DB복구에 실패하였다. -_-;

[ethiel@uw64-005 www]$ mysql -u ethiel -p ethiel < ethiel-2006-11-14.dump
Enter password:
ERROR 1064 (42000) at line 11: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ‘desc text,
date datetime default NULL,
place varchar(255) default NULL,
sh’ at line 5
[ethiel@uw64-005 www]$

확인해 본 결과, 예전 서버의 MySQL 버전은 3.23, 지금 서버는 5.0.
그 사이에 무-_-수히 많은 업그레이드가 진행되면서 SQL 구문이 호환되지 않는 부분이 발생한 것이다.

급한 마음에 vi 로 dump파일을 열어 보았지만,
흰 것은 종이요 검은 것은 글씨라.. 가 아니라 흰 것은 글씨요, 검은 것은 바탕화면…
머 아는 것이 있어야지.. -_-; OTL

순돌아빠 버금가는 박학다식, 진철 옹에게 헬프를 요청했으나,
진철 옹은 회사 일 러쉬로 인해 본진 수비에 급급, 헬프할 형편이 아니었다.

Anyway,
결국은 Cafe24 고객 서비스 센터와 구글링과 봉사 문고리 잡기 식 에디팅으로 간신히 복구 성공.
내용은 아래와 같다.

ERROR 1064: desc, show는 Table column의 type으로 사용시 `desc`, `show`와 같이 변경해 주어야 함. -> 예약어이기 때문
ERROR 1071 ‘Specified key was too long’: Table 내에서 사용된 byte가 1000이 넘지 않도록 수정해야 함. -> MySQL 4.1부터 적용되는 utf-8환경에서 var(255)는 255 bytes가 아닌 255*43 bytes로 인식함.
euc-kr로 인코딩 엔트리의 경우, utf-8로 변경해 주어야 함. -> 제로보드 4.x의 경우 euc-kr을 사용하기 때문에 따로 작업이 필요하다. 다음 링크 참조 [제로보드를 UTF-8로]
별거 아니지만, 문외한인 나로서는 꽤 삽질 했던 내용이다.
혹시나 나와 같이 해매고 있을 사람들을 위해 포스팅 한다.

p.s. 제로는 제로보드 5.0의 차후 버전이 지금 버전(beta 0.05)과 구조적으로 완전히 달라질 것이며, 서로 호환되지 않을 것이라고 발표함. -_-; 정식 버전 나올 때 까지 일단 손 때기로 결정;

p.s.2 11월19일 새로 내용 추가. 이탤릭 체 부분 참고.