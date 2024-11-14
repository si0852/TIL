### Generic
- 형 변환 처리시 다양한 예외가 발생할 수가 있다.
- 이러한 예외를 최소화하기 위해선 타입 점검이 필요하다.
- 타입 점검을 보완하기 위해 Generic 가용

`What is Generic`
- 타입 형 변환에서 발생할 수 있는 문제점을 사전에 없애기 위함
~~~ java
CastingGenericDTO<String> dto1 = new CastingGenericDTO<>();
        dto1.setObject(new String());

        CastingGenericDTO<StringBuffer> dto2 = new CastingGenericDTO<>();
        dto2.setObject(new StringBuffer());

        CastingGenericDTO<StringBuilder> dto3 = new CastingGenericDTO<>();
        dto3.setObject(new StringBuilder());
        
        // 타입치환
        String temp1 = dto1.getObject();
        StringBuffer temp2 = dto2.getObject();
        StringBuilder temp3 = dto3.getObject();
~~~
- 타입치환에서 잘못된 타입으로 하게되면 컴파일 에러가 발생이된다.
- 하지만 Generic을 사용하면 형 변환을 할 필요가 없어진다.
- 위와 같이 명시적으로 타입을 지정할 때 사용하는 것이 제네릭이다.

`Type`
- E: 요소(자바 컬렉션에서 주로 사용)
- K: 키
- N: 숫자
- T: 타입
- V: 값
- S,U,V: 두번쨰, 세번째, 네번째에 선언된 타입

`메서드의 매개변수로 넘어가는 제네릭`
- wildcardGeneric<?> c
  - ?를 적어주면 어떤 타입이 되더라도 상관없다.
  - But 어떤 타입인지 모르기 때문에 Object로 처리해야된다.
    - Object value c= c.getWildcard();
~~~ java
WildcardGeneric<?> wildcard = new WildcardGeneric<>();
wildcard.setWildcard("A");
~~~
- Error 발생
- 어떤 객체를 wildcard로 선언하고, 그 객체의 값은 가져올 수 있다.
- 하지만 와일드카드로 객체를 선언했을 때 위 예제 처럼 특정 타입으로 값을 지정 X

`타입 범위`
- < ? extends Car>
  - Car 클래스와 관련되어 있는 상속한 클래스가 넘어오면 된다.
  - Bounded Wildcards라고 불린다.
  - 매개 변수로 넘어오는 제네릭 타입의 경계를 지정하는데 사용