## Effective Java 3/E

#### Item 22. 인터페이스는 타입을 정의하는 용도로만 사용하라

- 클래스가 어떤 인터페이스를 구현한다는 것은 <u>자신의 인스턴스로 무엇을 할 수 있는지</u>를 클라이언트에 얘기해주는 것



##### 상수 인터페이스(안티패턴)

- 메서드 없이, static final 필드로만 이루어진 인터페이스
  → 인터페이스의 용도에 맞지 않음

- 내부적으로 사용하는 상수를 API로 외부 노출하게 됨
- 클라이언트 코드가 상수들에 종속될 수 있음(더 이상 사용하지 않더라도 구현하고 있어야함)

###### 대안

- 클래스나 인터페이스 자체에 상수를 추가
- Enum 타입으로 만들기
- 인스턴스화 할 수 없는 유틸리티 클래스로 만들기

------

##### 정적 임포트

```java
import static effectivejava.chapter4.item22.constantutilityclass.Constants.*;
```

- 빈번히 사용하는 상수는 정적 임포트하여 클래스 이름 생략 가능

