## Effective Java 3/E

#### Item 74. 메서드가 던지는 모든 예외를 문서화하라

- 메서드가 던지는 예외는 메서드를 올바로 사용하는 데 아주 중요한 정보이기 때문에 각 메서드가 던지는 예외 하나하나를 문서화하는 데 충분한 시간을 써야 함

- 검사 예외는 항상 따로따로 선언

  - 공통 상위 클래스 하나로 뭉뚱그려서 선언할 경우 메서드 사용자에게 각 예외에 대처할 수 있는 힌트를 주지 못함
  - 같은 맥락에서 발생할 여지가 있는 다른 예외들가지 삼켜버릴 수 있음

- 각 예외가 발생하는 상황을 JavaDocs의 @throws를 사용해 문서화 할 것 

  → main은 JVM만이 호출하므로 Exception을 던지도록 선언해도 괜찮음

---

###### 비검사예외

- 자바 언어가 요구하는 것은 아니지만 문서화해두면 좋음

- 일반적으로 비검사 예외는 프로그래밍 오류를 뜻하는데, 프로그래머가 이런 오류가 발생하지 않도록 코딩할 수 있는 힌트를 줄 수 있음

- 잘 정비된 비검사 예외 문서는 그 메서드를 성공적으로 수행하기 위한 전제조건이 됨

- **발생 가능한 비검사 예외를 문서로 남기는 것은 인터페이스 메서드에서 특히 중요**

  → 이 조건이 인터페이스의 일반 규약에 속하게 되어 모든 구현체가 일관되게 동작하도록 해줌

----

###### 예외 문서화

- 메서드가 던질 수 있는 예외를 각각 @throws 태그로 문서화
- 비검사 예외는 메서드 선언의 throws 목록에 넣지 않음

> 검사냐 비검사냐에 따라 사용자가 해야 할 일이 달라지므로 둘을 구분해야 함
>
> 
> 자바독 유틸리티는 
>
> 1. 메서드 선언의 throws절-주석에 @throws에 명시한 예외
> 2. @throws 태그에만 명시한 예외
>
> 두 예외를 시각적으로 구분해 사용자가 어느 것이 비검사 예외인지 알 수 있음

- 현실적으로 모든 비검사 예외를 문서화하는 것이 불가능할 때도 있음
  - 새로운 비검사 예외를 던져도 소스-바이너리 호환성이 유지되기 때문에 메서드가 수정될 경우 문서에 언급되지 않은 비검사 예외를 전파할 수 있음
- 한 클래스에 정의된 많은 메서드가 같은 이유로 같은 예외를 던지면 그 예외를 메서드가 아닌 클래스 설명에 추가할 수 있음

