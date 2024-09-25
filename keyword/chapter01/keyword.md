#외래키
Foreign Key
두 개의 테이블을 연결해주는 연결다리 역할을 함.
예를 들어서 이번 주 미션 내용에서 설계한 데이터베이스를 보자.
설계 조건에는 유저의 필수 정보를 담아야하는 users 테이블과, 미션을 담을 수 있는 missions 테이블이 필요하다.
그러나 실제 어플 화면에서는 '내 미션'과 '완료한 미션'을 담을 수 있어야 한다. 그러면 users에 missions 내용을 넣어서 만들어도 될까?
이런식으로 테이블을 만들게 되면 하나의 테이블에 정보가 너무 많아지고, 중복되는 데이터가 많아서 참조하기 어려울 거다. 그래서 user_missions라는 별도의 테이블을 만들어 관리하는데
user_missions 테이블의 컬럼을 보면 user_id와 mission_id의 정보를 담을 수 있다. 여기서 user_id로 users의 정보를, mission_id로 missions의 정보를 긁어올 수 있을 거다.
최종적으로 users의 my_mission에서 user_missions의 정보를 불러오고, user_missions의 mission_id로 missions의 정보를 불러올 수 있는거다.
여기서 사용된 모든 요소들이 외래키의 역할을 수행한다고 보면 되겠다.(연결다리의 역할)

참고 출처: https://brunch.co.kr/@dan-kim/26

#기본키
Primary Key
테이블 내의 모든 레코드에서 갖는 고유한 값.
기본적으로 모든 레코드가 서로 다른 값을 가져야 함. 그래야 레코드들을 구분할 수 있음.
NULL값이 존재하면 안됨.
기본적으로 테이블당 하나의 기본키를 갖지만, 경우에 따라 1개 이상의 기본키를 정의할 수 있음(다수 열 기본키, 복합 기본 키)
PRIMARY KEY라는 속성을 붙여줘서 정의할 수 있고 AUTO_INCREMENT 같은걸 붙여줘서 레코드가 추가될 때 마다 증가시켜서 기본키를 만드는게 보편적임.
MongoDB에서 기본적으로 부여되는 ObjectId와 같은 경우도 기본키라고 볼 수 있겠다.

참고 출처: https://velog.io/@hiy7030/DB-Primary-key%EC%99%80-foreign-key

#ER 다이어그램
ERD(Entity-Relation Diagram)
우리말로는 개체 관계도
데이터베이스 상의 데이터와 테이블 간의 관계를 사람이 직관적으로 이해할 수 있게 하는 모델
이런게 왜 필요하냐면 백엔드에서 데이터베이스의 관계는 말로는 설명할 수 있을 정도로 복잡하게 얽혀있음. SQL에서 명령어로 계속 테이블 띄우면서 볼 수 있을 정도로 간단하지 않음.
그리고 개발하다 보면 특정 요소가 추가되거나 수정되거나 삭제되는 일이 빈번하게 일어남. 이거를 테이블 관계를 미리 생각 안해놓고 무지성으로 만들다가는 굉장히 피곤해진다.(1학기 인프 프로젝트 중 본인 얘기)
그래서 개발하기 전에 관계도를 그려서 어떤 데이터베이스를 구축할지 미리 고민해보고 이해하는 거임.
이걸 빠르고 쉽게 구축할 수 있게 하는 도구들도 널리 퍼져있다.  (저는 인터넷에서 바로 코드로 구현할 수 있는 DBdiagram이란 곳에서 했습니다.)

참고 출처: https://m.blog.naver.com/gongtong/150135598792
https://velog.io/@mong9_s/DBRDBMS-5.-ER%EB%8B%A4%EC%9D%B4%EC%96%B4%EA%B7%B8%EB%9E%A8ERD

#복합 키
Composite Key
두개 이상의 컬럼을 묶어서 하나의 기본키로 지정하는 것
??이게 뭔소리임
말 그대로이긴 한데 예를 들어서 id와 age라는 컬럼이 있다고 가정하자. 그리고 이 둘을 묶어서 primary key로 지정했다.

id = 1, age = 10인 레코드       id = 1, age = 20인 레코드

이렇게 두개의 레코드는 에러가 나지 않는다. id라는 값이 같아도 age 값이 다르기 때문에 primary key의 조건 중 하나인 고유성을 만족하고 있기 때문이다.
근데 여기에 id = 1, age = 10이란 레코드를 또 insert 한다고 가정하자. 이 때는 에러가 발생한다.
어떤 구체적인 경우에서 이걸 써야 할지 아직 잘 모르겠다. 아무래도 id값이 겹치지만 다른 컬럼값을 다르게 하는 테이블에서 사용할 수 있을 것 같다.

참고 출처: https://velog.io/@kon6443/DB-%EA%B8%B0%EB%B3%B8%ED%82%A4-%EC%99%B8%EB%9E%98%ED%82%A4-%ED%9B%84%EB%B3%B4%ED%82%A4-%EB%B3%B5%ED%95%A9%ED%82%A4-%EA%B0%9C%EB%85%90-4x1bgz5w
https://gaemi606.tistory.com/entry/Composite-Key-%EB%B3%B5%ED%95%A9-%ED%82%A4

#연관 관계
데이터베이스는 관계를 맺을 수 있다.
논리적으로 연관이 있는 두 테이블 사이의 연결을 설정한다.
테이블 구조를 정제하고 중복 데이터를 최소화 하는 것을 도와준다.

크게 세가지 관계로 정리할 수 있다.
1. 1:1 관계
하나의 테이블이 상대 테이블과 하나의 관계를 가지는 것
2. 1:N 관계
한 쪽 테이블의 레코드가 관계를 맺은 테이블의 여러 레코드와 연결된다는 것
예시) area 테이블과 shops 테이블의 관계
3. N:M 관계
양쪽 엔티티에서 1:N 관계를 가지는 것
두 테이블의 대표키를 컬럼으로 갖는 중간 다리 연결 테이블을 생성해서 관리한다.
예시) users 테이블과 missions 테이블의 관계

참고 출처: https://benlee73.tistory.com/95

#정규화
Normalization
테이블 간에 중복된 데이터를 허용하지 않는다는 목표로 테이블을 분해하는 것.
중복 데이터가 없기 때문에 무결성을 유지할 수 있고 DB 저장용량도 줄일 수 있다.
정규화 단계는 다음과 같다.

1. 제1정규화
테이블의 컬럼이 하나의 값을 갖도록 테이블을 분해하는 것. 하나의 레코드에서 컬럼 하나에 여러 값을 갖지 않도록 분해하는 것이다.

2. 제2정규화
제 1정규화가 되어있는 테이블에 대해 완전 함수 종속을 만족하도록 테이블을 분해하는 것이다.
??완전 함수 종속이 뭐임
기본키의 부분집합이 결정자가 되어선 안된다는 것을 의미한다.
??아직도 모르겠음
예를 들어 (학번, 강의명)이라는 복합키를 기본키로 가지고 있는 테이블이 있다고 가정해보자.
여기에 컬럼에 추가적으로 강의실, 학점을 추가해보자.
학점은 기본키(학번, 강의명)에 따라 하나씩 결정될 것이다.
그런데 강의실의 경우는 강의명에 따라서 결정된다. 
!!(강의명)이라는 기본키의 부분집합에 의해 컬럼값이 정해지고 있다.
이런 경우를 방지하는 것이 제2정규화이다. 이 경우는 강의명과 강의실 정보를 담고 있는 별도의 테이블을 만들어서 해결할 수 있겠다.

3. 제3정규화
제 2정규화를 진행한 테이블에 대해 이행적 종속을 없애도록 테이블을 분해하는 것이다.
??아까부터 모르겠는 소리만 나온다.
A->B, B->C에 의해 A->C가 되는 것을 막는 것이다.
예를 들어 학번, 강의명, 수강료라는 컬럼이 있는 테이블을 가정해보자.
학번에 의해 강의명이 결정된다고 할 때, 강의명은 수강료를 결정하게 된다. 이렇게 되면 해당 학생을 OO수강료를 배정받게 된다.
근데 여기서 학생이 강의를 다른 것으로 바꾼다고 생각해보자. 이 경우 테이블의 강의명 컬럼뿐만 아니라 수강료 컬럼까지 바꿔줘야 한다.
데이터가 한두가지면 모르겠는데 수백, 수천가지가 되면 이런식으로 바꾸는 건 굉장히 비효율적이다. 따라서 강의명과 수강료가 함께 정의되어 있는 테이블로 분해하는 것이다.

4. BCNF 정규화
제 3정규화까지 된 테이블에 대해 모든 결정자가 후보키가 되도록 테이블을 분해하는 것이다.
??이제 제발 그만
이번에도 학번, 강의명, 교수라는 컬럼을 가진 테이블이 있다고 가정해보자.
(학번, 강의명)복합키를 기본키로 하면 교수라는 값을 결정하고, 교수라는 값은 강의명을 결정하게 된다.
여기서 이상한게 교수가 강의명을 결정하지만 후보키가 아니라는 점이다. 그래서 테이블을 (학번, 교수), (강의명, 교수) 테이블 2개로 찢어야 한다.

참고 출처: https://mangkyu.tistory.com/110

#반 정규화
DeNormalization
정규화하면 무결성성, 유연성 등의 장점이 있지만, 단점도 있음.
무수한 테이블 조인으로 인해 성능이 저하됨...
따라서 반정규화로 어느 정도 타협을 보면서 데이터를 중복시키는 것이다. 데이터를 조회하는 속도는 빨라지지만 유연성은 낮아진다.

절차는 다음과 같다.
1. 반정규화 대상조사
범위처리빈도수, 테이블 조인 개수 등의 데이터베이스가 작동될 때의 성능을 분석한다.
2. 다른 방법 검토
뷰 테이블, 클러스터링, 인덱스 조정등의 방법으로 해결될 수 있는지 확인해본다.
3. 반정규화 적용

반정규화를 하게 되었을 때 기법 세가지
1. 테이블 병합
1:1, 1:N, 슈퍼/서브 테이블 병합등으로 테이블을 하나로 통합한다.
2. 테이블 분할
수직분할: 한 테이블의 속성을 분할해서 두 개 이상으로 분할한다.
수평분할: 한 테이블의 값을 기분으로 테이블을 분할한다.
3. 테이블 추가
중복, 통계 테이블 등을 추가하여 성능을 향상한다.

참고 출처: https://velog.io/@dddooo9/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B0%98%EC%A0%95%EA%B7%9C%ED%99%94