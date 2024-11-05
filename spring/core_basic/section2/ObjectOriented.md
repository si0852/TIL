## 객체지향 그리고 IoC, DI
- AppConfig를 추가하며 역할에 대한 관심사를 분리하였다.
- AppConfig는 객체 생성과 연결
- Client(Service)는 실행에 초점
- 그렇다면 어떤 객체지향 원칙이 적용되었는지 알아보

`SRP 단일 책임 원칙`
- 처음 개발된 Service에는 객체 생성, 연결, 기능 실행 등 많은 책임을 가지고 있었다.
- SRP 원칙을 따르며 관심사를 분리
  - AppConfig: 객체 생성과 연결
  - Service: 실행 

`DIP 의존관계 역전 원칙`
- 구체화가 아닌 추상화에 의존해야 한다.
- 할인 정책에 따라 OrderService 코드를 수정해야 했다.
  ~~~java
  // 고정 할인
  DiscountPolicy discountPolicy = new FixDiscountPolicy();
  // 정액 할인
  DiscountPolicy discountPolicy = new RateDiscountPolicy();
  ~~~
  Service에서 어떤 정책을 쓰느냐에 따라 코드가 변경이 된다. (구체화에 의존하기 때문)
- 추상화 인터페이스에만 의존하도록 코드 변경
  ~~~java
  private DiscountPolicy discountPolicy;
  ~~~
- 인터페이스로만은 아무것도 할 수 없어 AppConfig를 추가
  - AppConfig를 통해 할인 정책에 따라 객체를 대신 생성하여 의존관계 주입 하였다.

`OCP 개방 폐쇄 원칙`
- 확장에는 열려 있으나 변경에는 닫혀 있다.
- AppConfig에서 할인 정책에 따라 객체를 대신 생성하여 주입해주므로 Service에서는 코드를 수정할 필요가 없다.

`IOC 제어의 역전`
- AppConfig 등장 전에는 구현 객체(Service)에서 객체를 생성하고 연결하고 실행하였다. 이는 전체 프로그램 제어 흐름을 컨트롤 하였다.
- But AppConfig 등장 이후에는 객체를 생성하고 연결하는 역할을 AppConfig가 맡게 되면서 프로그램 제어 흐름을 가져갔다.
- OrderService 코드를 보면
  ~~~java
  public class OrderServiceImpl implements OrderService {

    private final MemberRepository memberRepository;
    private final DiscountPolicy discountPolicy;

    public OrderServiceImpl(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
    }

    @Override
    public Order createOrder(Long memberId, String itemName, int itemPrice) {

        Member member = memberRepository.findById(memberId);
        int discountPrice = discountPolicy.discount(member, itemPrice);

        return new Order(memberId, itemName, itemPrice, discountPrice);
        }
    }
  ~~~
  -> 서비스 코드를 보면 필요한 인터페이스를 호출하지만, 어떤 구현 객체들이 실행될지 모른다.
- 어떤 구현 객체를 실행할지는 AppConfig에서 정한다.
- AppConfig 처럼 외부에서 관리하는 것을 IoC(제어 역전)이라고 한다.

`DI 의존관계 주입`
- 정적인 클래스 의존관계
  - 위 OrderServiceImpl 코드를 보면 어떤 인터페이스에 의존하는지 한눈에 볼 수 있다.
  - 즉, import 코드만 봐도 전반적인 구조를 한눈에 볼 수 있다.
- 동적인 객체 인스턴스 의존 관계
  - 애플리케이션 실행 시점에 생성된 객체 인스턴스의 참조가 연결된 의존 관계다.
  - AppConfig에서 객체 생성 후 OrderApp 통해 Service에 전달하는 것이 의존관계가 연결되는 것이다.
    - 이것을 의존관계 주입이라 한다.
    - 인스턴스 생성 후, 참조값을 전달한다.
  - 외존관계를 사용하면, 클라이언트(정적 클래스)에서는 코드 수정 없이 실행할 수 있다.
 