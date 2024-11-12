## Local****
`LocalDate`
- 날짜만을 나타내는 클래스(연도, 월, 일만 표현)
- 시간대 정보 포함X
- 생성 방법
  ```java
  LocalDate date = LocalDate.now(); // 현재 날짜
  LocalDate specificDate = LocalDate.of(2024, 11, 6); // 특정 날짜 지정
  LocalDate parsedDate = LocalDate.parse("2024-11-06"); // 문자열에서 파싱
  ```
- 주요 메서드
  - getYear(): 연도
  - getMonth(): 월 
  - getDayOfMonth(): 일
  - getDayOfWeek(): 요일
  - plusDays(10): 10일 후
  - isLeapYear(): 윤년 여부

`LocalTime`
- 시간만을 나타내는 클래스 (시간, 분, 초, 나노초)
- 시간대가 없고, 시각 정보만 나타낸다.
  - 시간대: 특정 지역에서 사용하는 시간의 기준(ex 한국 표진시: UTF+9)
  - 시각: 하루의 특정 시각을 표현
  - 하루 중 특정 시각을 나타낸다.
- 생성 방법
~~~ java
LocalTime time = LocalTime.now(); // 현재 시간
LocalTime specificTime = LocalTime.of(14, 30, 15); // 특정 시각 지정 
LocalTime parsedTime = LocalTime.parse("14:30:15); // 문자열 파싱
~~~
- 주요 메서드
  - getHour()
  - getMinute()
  - getSecond()
  - plusHours(2) : 2시간 후의 시간
  - minusMinutes(30) : 30분 전 시간
  - isBefore(otherTime): 특정 시간보다 이른지 비교

`LocalDateTime`
- 날짜와 시간을 모두 포함
- 시간대 정보는 없다.
- 생성방법
  ~~~ java
  LocalDateTime dateTime = LocalDateTime.now();
  LocalDateTime specificDateTime = LocalDateTime.of(2024, 11, 6, 14, 30); // 특정 날짜와 시간
  LocalDateTime parsedDateTime = LocalDateTime.parse("2024-11-06T14:30:00"); // 문자열에서 파싱
  ~~~
- 주요 메서드
  - getYear()
  - getMonth()
  - getDayOfMonth(): 일
  - getHour()
  - getMinute()
  - getSecond()
  - plusDays(1): 하루 더하기
  - minusHour(5)
  - toLocalDate(): LocalDate로 변환
  - toLocalTime: LocalTime으로 변환

`Epoch`
- 컴퓨터 시스템에서 시간의 기준점을 의미
- **"1970년 1월 1일 00:00:00 UTC"**로 정의