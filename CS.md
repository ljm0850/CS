# CS

### http 와 https의 차이

- 서버와 클라이언트 사이에 전송되는 데이터를 암호화 여부
- https는 서버와 클라이언트 사이 모든 데이터를 암호화 하여 전송
  - 암호화 하는 시간이 추가되서 상대적으로 느림



### frame work

- 복잡한 문제를 해결하거나 서술하는 데 사용되는 기본 개념 구조
- 일반적으로 소프트웨어의 전체적인 구조를 재사용과 관리가 유용하도록 미리 설계해둔 것.



### GET POST

- 가장 큰 차이점은 프론트엔드에서 백엔드로 데이터 전송시 데이터 암호화 여부

- 데이터 전송시 데이터를 packet에 담아 전송을 하게 되는데, GET방식의 경우 packet의 Header에 데이터를 담아 URL주소에 데이터 내용 까지 포함, POST방식의 경우 packet의 Body에 데이터가 암호화 되어 전송

- GET방식의 경우 암호화를 거치지 않아서 상대적으로 빠르다
- POST방식의 경우 암호화와 GET방식 대비 큰 데이터를 전송할 수 있다



### JAVA Garbage Collection

- 쓸모가 없어진 객체를 자동으로 제거하여 메모리를 관리하는 시스템

```java
Test gc = new Test();
gc.name("Garbage Collection");
//gc = null; // 필요가 없어져서 null 선언

gc = new Test(); // 기존에 할당되있던 객체의 참조가 사라져서 garbage 발생
gc.name("new Garbage Collection")
```

- 위와 같이 발생한 garbage를 놔두면 메모리를 차지하기 때문에 이를 지워 메모리를 관리하는 시스템



### ORM

- Object Relational Mapping
- DB제어시 기존에는 SQL문을 사용하여 제어했었으나, 객체를 DB와 직접 맵핑하여 제어하는 것



### Rest

- Representational State Transfer의 약자
- 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 것
- HTTP URI를 통해 자원을 명시하고 HTTP Method를 통해 해당 자원에 대한 상태를 주고 받는 방식
  - URI = URL + URN



### SPA

- 기존의 MPA(Multiple Page Application)의 경우 웹페이지에서 새로운 정보를 보여줘야 할 경우 해당 url로 요청을 보내어 페이지 전체를 다시 구성(새로운 View파일 제공)하는 방식

- SPA(Single Page Application)는 하나의 뷰(View)파일에 컴포넌트를 배치하여 페이지를 구성하는 방법



### Framework & Library

- Framework(Vue,django,spring...)
  - 소프트웨어의 구조를 설계해 둔것
  - 개발자가 프레임 워크 구조에 맞게 프로그래밍 하여 작동
- Library(React...)
  - 소프트웨어의 기능을 구현
  - 개발자가 라이브러리를 활용하여 개발
