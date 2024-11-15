### Overloading
- 메서드의 이름이 같고, 매개 변수만 다르게 하는 것
~~~java
public class ReferenceOverloading {
    public static void main(String[] args) {
        ReferenceOverloading reference = new ReferenceOverloading();
    }

    public void print(int data){}
    public void print(String data){}
    public void print(int intData, String stringData){}
    public void print(String stringData, int intData){}
}

~~~

### Overriding
- 자식 클래스에서 부모 클래스에 있는 메소드와 동일하게 선언
- 접근제어자, 리턴 타입, 메소드 명, 매개 변수 타입 및 개수가 모두 동일해야 한다.
~~~ java
public class ParentOverriding {
    public ParentOverriding() {
        System.out.println("ParentOverriding Constructor");
    }

    public void printName() {
        System.out.println("printName() - ParentOverriding");
    }
}
~~~
~~~ java
public class ChildOverriding extends ParentOverriding{
    
    public ChildOverriding() {
        System.out.println("ChildOverriding Constructor");
    }

    @Override
    public void printName() {
        System.out.println("printName() - ChildOverriding");
    }
}
~~~
- overriding 된 메서드의 접근 제어자는 부모 클래스에 있는 메소드와 달라도 되지만 접근 권한이 확장되는 경우에만 허용
  - 잘못된 예시
    ~~~java
    public class ChildOverriding extends ParentOverriding{
    
        public ChildOverriding() {
            System.out.println("ChildOverriding Constructor");
        }

        @Override
        private void printName() {
            System.out.println("printName() - ChildOverriding");
        }
    }
    ~~~
    - 부모는 public 이고 자식은 private 로 선언이 되면, 에러가 발생이 된다.
    - 접근 제어자가 확장되는 것은 문제가 안되지만, 축소가 되면 문제가 생긴다.
    - 부모가 private 이면, 자식은 어떠한 메서드도 사용가능하다.