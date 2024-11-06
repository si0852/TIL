## System 클래스
- java.lang 패키지에 포함
- 자바 프로그램 실행 환경과 상호작용할 수 있도록 지원하는 유틸리티 클래스
- 인스턴스를 생성할 수 없으며, 모든 메서드와 필드가 static으로 선언

### 1. System 클래스의 주요 정적 변수

`System.in`
- 표준 입력 스트림(InputStream 타입)
- 콘솔에서 입력 받는데 사용

`System.out`
- 표준 출력 스트림
- 콘솔에 데이터 출력하는데 사용
- System.out.println, System.out.print

`System.err`
- 표준 에러 스트림
- 오류 메시지나 경고 메시지 출력

### 2. 주요 메서드
`System.currentTimeMillis()`
- 시스템의 현재 시간을 밀리초 단위로 변환

`System.nanoTime()`
- 시스템의 현재 시간을 나노초 단위로 반환

`System.gc()`
- 가비지 컬렉터를 실행하도록 요청
- 메모리에서 더 이상 참조되지 않는 객체 정리
- 가비지 컬렉터가 바로 실행된다는 보장은 없다

`System.getProperty(String key)`
- 시스템 속성을 가져옴 
- key에는 속성의 이름 전달 (java.version, os.name, user.dir 등)

`System.setProperty(String key, String value)`
- 시스템 속성을 설정
    ~~~ java
    System.setProperty("myProperty", "myValue");
    ~~~

`System.getenv(String name)`
- 운영체제의 환경 변수를 가져오는 메서드
    ~~~ java
    String path = System.getenv("PATH");
    System.out.println("PATH: " + path);
    ~~~
  
`System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`
- 배열을 복사하는데 사용
  - src 배열에서 srcPos 위치부터 dest 배을의 destPos 위치에 length만큼 요소를 복사
  - 성능이 중요한 경우 for 루프를 이용한 복사보다 빠르게 동작
  ~~~ java
  int[] sourceArray = {1, 2, 3, 4, 5};
  int[] destinationArray = new int[5];
  System.arraycopy(sourceArray, 0, destinationArray, 0, sourceArray.length);
  ~~~