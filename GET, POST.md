가장 큰 차이점은 프론트엔드에서 백엔드로 데이터 전송시 데이터 암호화 여부이다.

데이터 전송시 데이터를 packet에 담아 전송을 하게 되는데,

GET방식의 경우 packet의 Header에 데이터를 담아 URL주소에 데이터 내용 까지 포함되지만,

POST방식의 경우 packet의 Body에 데이터가 암호화 되어 전송된다.

따라서 GET방식의 경우 암호화를 거치지 않아서 상대적으로 빠르다는 장점이 있고,

POST방식의 경우 암호화와 GET방식 대비 큰 데이터를 전송할 수 있다는 장점이 있다.