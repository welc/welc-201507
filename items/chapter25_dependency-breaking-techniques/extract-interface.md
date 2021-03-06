## 인터페이스 추출 (Extract Interface)

여러 프로그래밍 언어에서 가장 안전한 의존성 제거 기법 중 하나.

세 가지 방식으로 추출할 수 있다.

1. 자동화된 리팩토링 도구 사용
2. 이 섹션에서 소개하는 절차에 따라 한 메써드씩 점진적으로 추출
3. 기존 클래스의 선언에서 여러 메써드의 선언을 복사하여 인터페이스 선언에 붙여넣고 편집
    * 약간 위험하지만, 시간이 촉박할 때 효과적

점진적으로 추출하기 절차

1. 새로운 빈 인터페이스 생성
2. 기존 클래스가 새 인터페이스를 구현하도록 선언
    * 여기까지 아무 문제 없이 컴파일 되는 것을 확인
3. 기존 클래스 대신 인터페이스로 객체를 참조했으면 부분들을 찾아서 수정
    * 지금 테스트 하려는 부분부터 우선적으로
4. 컴파일에 성공할 때까지 필요한 메써드 선언을 인터페이스에 추가

기존 클래스에 없는 메써드를 인터페이스에 선언해야 하는 경우도 있다.

* 클래스(static) 메써드를 인터페이스로 추출하고 싶은 경우
* [C++] 서브클래스가 있는 클래스의 인터페이스를 추출해야 하는데, 필요한 메써드가 `virtual`로 선언되어 있지 않은 경우
    * 기존 메써드를 인터페이스로 추출하고 `virtual`로 선언하면 시스템의 기존 동작이 바뀌는 부작용이 발생함
