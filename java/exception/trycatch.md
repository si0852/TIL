## 예외 처리
`형태`
~~~java
try{
        ... 내용 ....
}catch(exception e) {
        .. 에러 내용 ...
}
~~~

`변수 지정`
- try 블록 내에서 선언한 변수를 catch에서 사용할 수 없다.
- catch에서 사용되는 변수는 try 블록 앞에 선언해야 한다.
~~~java
 public void checkVariable2() {
    int[] intArray = null;
    try {
         intArray = new int[5];
        System.out.println(intArray[5]);
    } catch (Exception e) {
        System.out.println(intArray.length);
    }
    System.out.println("This code must run");
}
~~~

`multi catch`
- catch 블록의 순서가 중요하다.
- 미리 선언한 Catch 블록의 예외 클래스는 다음에 선언한 Catch 블록의 예외 클래스보다 범위가 작아야 한다.
    ~~~ java
    public void multiCatchThreeWithNull() {
        int[] intArray = null;
        try {
            intArray = null;
            System.out.println(intArray[5]);
        } catch (NullPointerException e) {
            System.out.println("NullPointerException occurrred");
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("ArrayIndexOutOfBoundsException occurrred");
        }catch (Exception e) {
            System.out.println("Exception occurrred");
        }
    }
    ~~~
  
`예외 종류`
- 자바에서는 세 정류의 예외가 존재
  - checked exception
  - error
  - runtime exception or unchecked exception

`error`
- 자바 밖에서 발생한 예외
- Exception과 큰 차이
  - 프로그램 안 or 밖에서 발생했는지 여부
  - 더 큰 차이는 프로그램이 멈추어 버리냐 계속 실행하느냐의 차이다.
  - Error는 프로세스에 영향을 주고
  - Exception은 쓰레드에 영향을 준다.
- uncheceked Exception

`runtimeException`
- 런타임 예외는 예외가 발생할 것을 미리 감지하지 못했을때 발생
- 컴파일시에 체크를 하지 않기 때문에 unchecked exception이라 부른다.

`Exception`
- checked Exception

`Throwable`
- Exception과 Error 클래스는 Throwable 클래스를 상속받아 처리
  - 생성자
    - Throwable()
    - Throwable(String message)
    - Throwable(String message, Throwable cause)
    - Throwable(Throwable cause)
  - Exception 클래스에서 overriding한 메서드
    - getMessage()
    - toString()
    - printStackTrace()

`예외 발생`
- 예외를 발생시키는 방법
  - 블록에서 예외 처리
    ~~~ java
        throw new Exception("~~~~");
    ~~~
  - 메서드에서 예외 처리
    ~~~java
        public static void maim(String args[]) throws Exception {}
    ~~~
    
`Custom Exception`
- Error가 아닌 Exception을 처리하는 예외 클래스는 개발자가 커스텀하여 사용가능
- Throwable의 직계 자손 클래스들을 상속받아 만들어야 한다.(Exception)
~~~java
public class MyException extends Exception{
    public MyException() {
        super();
    }

    public MyException(String message) {
        super(message);
    }
}
~~~
~~~java
public void throwMyException(int number) throws MyException{
        try {
            if(number > 12) {
                throw new MyException("Number is over than 12");
            }
        } catch (MyException e) {
            e.printStackTrace();
        }
    }
~~~