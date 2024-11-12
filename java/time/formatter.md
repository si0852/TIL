## DateTimeFormatter
- 불변객체, 한 번 생성된 포멧터는 변하지 않는다. (스레드에서 안전하게 공유)
- 정적 메소드를 통한 편리한 사용
  - ofPattern()
  - ISO_*, RFC_* 형식을 사용
- 지역화 지원
  - withLocale()
  - 다양한 언어와 국가에 맞는 형식 설정 가능
- 유연한 파싱
  - parse() 
  - 메서드를 통해 문자열을 날짜와 시간 객체로 변환할떄 다양한 옵션 제공