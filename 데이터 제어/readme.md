# 데이터 조작어(DML) -추가 수정 삭제 조회
  - SELECT
    ~~~html
      SELECT 속성명,속성명...
      FROM 찾을 테이블;
    
    ~~~
    ~~~html
      SELECT 속성명,속성명...
      FROM 찾을 테이블;
    
    ~~~
    
    ~~~html
      SELECT *
      FROM 찾을 테이블;
      //전체속성
    ~~~
    
    - 옵션 ALL , DISTINCT 
      - ALL
        - 기본값 전부 출력
    
      - DISTINCT
       - 중복을 제외한 유일한 값

# 데이터 검색
  - WHERE 조건
    - 비교 = ,<> , <=, >, >=
     ~~~html
     SELECT *
     FROM Book
     WHERE price < 20000;
     ~~~
    
    - 범위 BETWEEN
    ~~~html
    SELECT *
    FROM Book
    WHERE price BETWEEN 1000 AND 2000;
    ~~~
    아래와 같다.
    ~~~
    SELECT *
    FROM Book
    WHERE price >= 1000 AND price <=2000;
    ~~~
    
    - 집합 IN, NOT IN
    ~~~html
    SELECT *
    FROM Book
    WHERE publisher (NOT) IN('책1',"책2")
    ~~~ 
    
    - 패턴 LIKE
    ~~~html
    SELECT bookname, publisher
    From Book
    WHERE bookname LIKE '책이름'
    ~~~
    
    '%문자열' => 문자열로 끝나는
    '문자열%' => 문자열로 시작하는
    '%문자열%' => 문자열을 포함하는
    '_열%' => (한글자)열 로 시작하는
    '__열%' => (두글자)열 로 시작하는
    
    
    
    - IS NULL, IS NOT NULL
    - AND, OR, NOT
    
 # ORDER BY
  - 정렬 : ORDER BY
    - ASC : 오름차순 (기본값)
    - DESC : 내림차순
  ~~~html
    SELECT *
    FROM Book
    ORDER BY price DESC, bookname;
  ~~~
    가격 순으로 내림차순정렬후 이름 기준 오름차순정렬

  - INSERT
     ~~~html
      INSERT INTO 테이블 이름 (포멧)
        values(ex,ex,ex,ex)
     ~~~

