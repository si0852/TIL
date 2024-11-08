## ZonedDateTime
- 날짜(LocalDate), 시간(LocalTime), 시간대(ZoneId) 모두 포함하는 클래스
- 특정 시간대의 날짜와 시간 저장, 다른 시간대로 변환하거나 조작 가능
- 시계열 데이터(예: 전 세계 다양한 시간대의 날짜와 시간 정보) 다루는 데 유용
- 불변객체 클래스, 인스턴스를 변경할 수 없으며 메서드 호출하면 새로운 객체가 반환

`ZonedDateTime 생성`

- ZonedDateTime.now()
  - 현재 시스템 시간대에 맞는 ZonedDateTime 생성
      ~~~ java
        ZonedDateTime currentDateTime = ZonedDateTime.now();
      ~~~
  - 특정 시간대에 맞는 ZonedDateTime 생성
    ~~~ java
        ZonedDateTime tokyoDateTime = ZonedDateTime.now(ZoneId.of("Asia/Tokyo"));
    ~~~
- ZonedDateTime.of()
  - 특정 날짜와 시간, 시간대를 직접 지정하여 생성
    ~~~ java
        ZonedDateTime customDateTime = ZonedDateTime.of(2023, 12, 25, 12, 0, 0, 0, ZoneId.of("Europe/Paris"))
    ~~~
    
`주요 메서드`
- 시간대 간 변환, 날짜 및 시간 조작 등을 쉽게 수행
- 시간대 변환: withZoneSameInstance(ZoneId zone) - 현재 객체를 지정된 시간대로 변환 
  ~~~ java
    currentDateTime.withZoneSameInstance(ZoneId.of("UTF"));
  ~~~
- 날짜 및 시간 조작: 날짜와 시간을 더하거나 빼는 메서드
  - plusDays(long days), minusHours(long hours), plusMonths(long months), minusYears(long years)
- 시간대 가져오기
  - getZone() - 현재 객체의 시간대를 반환
- 오프셋(UTC와의 차이) 가져오기
  - getOffset() - 현재 시간대의 오프셋 반환

`ZonedDateTime과 관련된 클래스`
- ZoneId: 시간대를 나타내는 클래스
- ZoneOffset: UTC와의 차이를 나타내는 클래스
- OffsetDateTime: ZonedDateTime과 유사하지만, ZoneId 대신 ZoneOffset만 포함