## ApplicationContext (스프링 컨테이너)
- AppConfig 생성하여 DI 하는것 대신에 ApplicationContext를 활용해 보자

`Annotation`
- Configuration Annotation
  - AppCofig 클래스를 설정 정보로 사용
  - @Bean으로 붙혀진 메서드를 스프링 컨테이너에 등록한다.
~~~java
@Configuration
public class AppConfig {
    ...
}
~~~
- Bean Annotation
  - 스프링 빈이라 불린다.(스프링 컨테이너에 등록된 객체)
- AppConfig 하위 메서드에 모두 붙힌다.
~~~java
@Configuration
public class AppConfig {
    @Bean
    public MemberService memberService() { ... }
    
    @Bean
    public OrderService orderService() { ... }
    ...
}
~~~

`등록된 스프링 빈 객체 찾기`
- applicationContext.getBean() 메서드 활용
~~~java

        ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
        MemberService memberService = applicationContext.getBean("memberService", MemberService.class);
~~~
