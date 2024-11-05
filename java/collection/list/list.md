## ArrayList
`1. 상속 관계`
- java.lang.object
  - java.util.AbstractCollection< E >
    - java.util.AbstractList< E >
- 최상위 부모는 Object 이후 AbstractCollection, AbstractList 순으로 확장
  - Abstract의 메서드는 자식에서 재정의가 가능하다.
  - AbstractCollection: Collection 인터페이스 중 일부 공통적인 메소드 구현
  - AbstractList: List 인터페이스 중 일부 공통적인 메소드 구현
    
`ArrayList가 구현한 모든 인터페이스`
~~~
Serializable, Cloneable, iterable<E>, Collection<E>, List<E>, RandomAccess 
~~~

`2. ArrayList 생성자`

| 생성자                                  | 설명                                         |
|--------------------------------------|--------------------------------------------|
| ArrayList()                          | 객체를 저장할 공간이 10인 list를 만든다.                 |
| ArrayList(Collection<? extends E> c) | 매개 변수로 넘어온 컬렉션 객체가 저장되어 있는 ArrayList를 만든다. |
| ArrayList(int initialCapacity)       | initialCapacity 만큼 저장공간을 만든다.              |

`3. ArrayList 추가`

| 리턴타입    | 메소드 이름 및 매개 변수                              | 설명                 |
|:--------|:--------------------------------------------|:-------------------|
| boolean | add(E e)                                    | 데이터를 가장 끝에 저장      |
| void    | add(int index, E e)                         | 데이터를 지정된 index에 추가 |
| boolean | addAll(Collection<? extends E> c            | 컬렌션 데이터를 끝에 저장     |
| boolean | addAll(int index, Collection<? extends E> c | 컬렌션 데이터를 index에 저장 |


`3-1. Shallow Copy vs Deep Copy`
- Shallow Copy
  - 다른 객체에 원본 객체의 주소값만 할당 (주소 복사)
  ~~~ java
  ArrayList<String> list = new ArrayList<>();
  list.add("A");

  ArrayList<String> list2 = list;
  // 또는 clone 사용
  // ArrayList<String> list2 = (ArrayList<String>)list.clone();
  list.add("Ooops");
  ~~~
  => 결과
  ~~~
  List: A
  List: Ooops 
  ~~~
  
- Deep Copy
  - 객체의 모든 값을 복사하여 복제된 객체에 있는 값을 변경해도 원본에 영향이 없도록 할때 사용
  ~~~ java
  // 1. 생성자를 통한 Deep Copy
  ArrayList<String> list = new ArrayList<>();
  list.add("A");
  
  ArrayList<String> list2 = new ArrayList<>(list); // deep copy
  
  // 2. addAll 사용
  ArrayList<String> list3 = new ArrayList<>();
  list3.addAll(list3);  // deep copy
  ~~~

`4. 데이터 꺼내기`
- 메서드
    
    | 리턴타입    | 메소드 이름 및 매개 변수       | 설명                     |
    |:--------|:---------------------|:-----------------------|
    | int | size()               | 들어가 있는 데이터 개수          |
    | E    | get(int index)       | index 위치의 데이터 값        |
    | int | indexOf(object o)    | 객체와 동일한 데이터 위치 리턴      |
    | int | lastIndexOf(object o | 객체와 동일한 데이터의 마지막 위치 리턴 |
- ArrayList 객체에 있는 데이터들을 배열로 뽑아낼 때 => toArray() 사용

  | 리턴타입     | 메소드 이름 및 매개 변수 | 설명                                            |
  |:---------|:---------------|:----------------------------------------------|
  | object[] | toArray()      | ArrayList 객체에 있는 값들을 object[] 타입의 배열로 만든다.    |
  | <T> T[]  | toArray(T[] a) | ArrayList 객체에 있는 값들을 매개 변수로 넘어온 T 타입의 배열로 만든다 |

`5. 데이터 삭제`
- 메서드

  | 리턴타입    | 메소드 이름 및 매개 변수             | 설명                    |
  |:--------|:---------------------------|:----------------------|
  | void    | clear()                    | 모든 데이터 삭제             |
  | E       | remove(int index)          | index 위치의 데이터 삭제      |
  | boolean | remove(object o)           | 객체 값과 같은 첫번째 데이터 삭재   |
  | boolean     | removeAll(Collection<?> o) | 객체 값과 같은 동일한 데이터모두 삭제 |