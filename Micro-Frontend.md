# Micro-Frontend

- https://www.youtube.com/watch?v=-4aYqPV9PM8&t=1403s

## 왜 사용하는가 ?

- 플랫폼 프론트에서 고려 (여러개의 위젯으로 구성된 경우)
  - 외부에서 신규 위젯 개발 요청
    - 외부팀의 증가에 맞춰 인원 늘리는데는 한계가 있음
    - 각자의 일정 / 요구사항에 따라 배포, 머지 등에 문제가 발생
    - 트러블 슈팅, QA에 대응이 힘듬



## 원리

- 외부에서 각각의 백엔드와 프론트엔드를 만들어 배포
- 배포된 데이터를 bundle로 가져와 합치는 형태



## 기본구조

![image-20230510203946257](C:\Users\dlwoa\AppData\Roaming\Typora\typora-user-images\image-20230510203946257.png)

- 컨테이너 중심으로 각 파트를 통합

- 인터페이스를 기반으로 느슨한 결합 (직접 참조 x)
- 각 마이크로 프론트엔드의 번들을 독립적으로 배포

- **핵심은 코드를 통합하는 방법 - 런타임 / 원격 / 동적**

### 런타임 원격 코드 동적 로딩

- import로 위젯별 컴포넌트의 원격 번들 파일 로딩
- 각 번들을 위젯 이름 키로 해서 저장
- 페이지 정보에 나열된 위젯 컴포넌트를 각각 렌더링



#### 문제

- ESM (ECMAScript Modules) 이 사용 가능한가?
  - JavaScript 모듈 시스템을 위한 표준 규격 (import, export)
  - CommonJS 나 AMD의 서버나 브라우저 환경에서 실행시 한계를 극복하기 위해 만들어짐
  - 코드를 여러 개의 파일로 나누어 작성하고, 각각을 모듈로 가져와서 사용 가능

- Vue template / JSX 컴파일 -> 번들러 사용
- 번들러에서 `remote / dynamic import`가 가능한가?
- 리모트 번들 파일 버전이 변경될 텐데, 어떻게 처리할 건가?



#### 문제 해결

- 다양한 레이어에서 작동하는 라이브러리가 존재
- 대체적으로 정적인 remote entry
- entry에 참조된 remote URL의 mainfest 파일에서 최신 번들 파일의 URL 다시 참조
- **SSR에 적용이 가능한가?**



## SSR과 Micro-Frontend

![image-20230510205148931](C:\Users\dlwoa\AppData\Roaming\Typora\typora-user-images\image-20230510205148931.png)

- Next.js에서 Federated SSR을 지원
- 각각의 SSR에서 HTML 생성
- 컨테이너에서 HTML을 통합

![image-20230510205612065](C:\Users\dlwoa\AppData\Roaming\Typora\typora-user-images\image-20230510205612065.png)

- HTML이 아닌 컴포넌트 번들을 SSR할때 런타임에 불러오고 싶음



## 캐시전략

![image-20230510210801866](C:\Users\dlwoa\AppData\Roaming\Typora\typora-user-images\image-20230510210801866.png)

- 캐시가 없을 경우 module, container 등 버전이 바뀔 경우 전체를 바꿔야함 => CPU 등 리소스 낭비가 커짐
- 버전이 바뀐 것만 확인하여 바꿈

### 동시성 문제

- 특정 페이지 생성하면 캐시를 먼저 만들고 캐시로부터 서빙 시작
- 캐시가 만료되어 리프레시하는 와중에 대량의 트래픽이 몰린다면 문제가 발생 할 수 있음
- 발표자의 해결 방법
  - ![image-20230510211657498](C:\Users\dlwoa\AppData\Roaming\Typora\typora-user-images\image-20230510211657498.png)