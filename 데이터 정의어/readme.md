# 데이터 정의어(DDL)
  - 데이터를 저장하기위해 데이터를 저장할 테이블의 구조를 설정해준다.
  - DDL(Data Definition Language) 가 이구조를 설정하는 명령어를 통칭한다.
    - CREATE : 테이블 구조 생성
    - ALTER : 구조 변경
    - DROP : 테이블 구조 삭제
 
# CREATE 
  ~~~html
  
    CREATE TABLE 테이블 이름(
      변수(속성)이름 데이터타입 제약 조건  
      [PRIMARY KEY 변수(속성)이름's]
      [FOREIGN KEY 변수(속성) REFERENCES 테이블이름(속성이름)]
      [ON DELETE {CASCADE | SET NULL}]
    
    )
  
  ~~~
    
  ~~~

    CREATE TABLE NewBook (
      bookid INTEGER PRIMARY KEY,
      bookname VARCHAR(20),
      publisher VARCHAR(20),
      price INTEGER,
      
      //PRIMARY KEY(bookid) 
      //mysql,mariadb 에서 는 작동하지만 다른 db에서는 안될수도?
    );
 ~~~
# ex
  ~~~
  CREATE TABLE NewBook(
    bookname VARCHAR(20) NOT NULL,
    publisher VARCHAR(20) UNIQUE,
    price INTEGER DEFAULT 1000 CHECK(price >1000)
  
  
  );
  
  ~~~

  ~~~
  CREATE TABLE NewCustomer(
    custid INTEGER PRIMARY KEY,
    name VARCHAR(40),
    address VARCHAR(40),
    phone VARCHAR(30)
  
  )
  
  ~~~

  ~~~
    CREATE TABLE NewOrders (
      orderid INTEGER PRIMARY KEY,
      custid INTEGER NOT NULL
      FOREIGN(custid) REFERENCES NewCustomer(custid)
      ON DELETE CASCADE,
      
      // custid 외래키 설정 : ON DELETE CASCADE 옵션을 통해 NewCustomer 옵션을 통해 NewCustomer 의 
      // 데이터 (custid=3)이 삭제될 경우 NewOrders 의 custid =3 이 연쇄 삭제(ON DELETE CASCADE) 된다.
      
      bookid INTEGER NOT NULL,
      saleprice INTEGER,
      orderdate DATE
    
    
    );
  ~~~

     
 # 제약조건 
  - NOT NULL : NULL 값을 허용하지 않음
  - UNIQUE : 중복 허용 X (유일한 값에 대한 제약)
  - DEFAULT : 기본값 부여
  - PRIMARY KEY : 기본키 지정 (NOT NULL , UNIQUE)
  - FOREIGN KEY : 외래키 지정
    - ON DELETE : 투플의 삭제 시 외래키 속성에 대한 동작지정
    - 옵션 : CASCADE, SET NULL, RESTRICT(NO ACTION : 기본값)
      - ON DELETE CASCADE : 참조하는 테이블의 값 삭제시 외래키 또한 연쇄 삭제 됨 
      - ON DELETE SET NULL : 참조하는 테이블의 값 삭제시 왜래키 NULL 값을 바뀔듯 
      - ON RESTRICT : 기본값
      
 # 외래키 제약조건 명시 시 주의사항
  - 외래키 제약조건 명시 시 참조되는 테이블(부모 릴레이션) 이 존재 해야 된다
  - 참조하는 값(변수, 속성)은 테이블의 기본키 이여야 한다.
      
    
  
    
