### Super()
~~~ java
public class parentArg{
    public  parentArg(String name) {
        System.out.println("ParentArg("+name+") Constructor");
    }
    
    public void printName() { ... }
}
~~~ 

~~~ java
   public class ChildArg extends ParentArg {
        public ChildArg() {
            System.out.println("Child Constructor");
        }
    }
~~~
- ChildArg 클래스의 생성자가 실행이될떄 에러가 발생이된다.
  - 이유: ParentArg 클래스의 매개 변수가 있는 생성자가 존재 But ChildArg에는 매개 변수로 받는 생성자가 존재 X
  - 해결: 자식 클래스에서 부모 클래스의 생성자를 명시적으로 지정하는 super()를 사용 