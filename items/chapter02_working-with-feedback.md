# 2장. 피드백 받으며 작업하기

시스템을 변경하는 두 가지 방식

* 흔히 하는 **고치고 기도하기(Edit and Pray)**
* **둘러싸고 수정하기(Cover and Modify)**
    * 코드의 나머지 부분에 안 좋은 영향을 주지 않도록 작업 영역을 잘 짜여진 테스트로 둘러싼다.
    * 변경 감지. 문제가 있는지 없는지 빠른 피드백.
    * 한 번에 한 행위씩, 의도한 부분만 안전하게 변경

단위 테스트는 개발 과정에서 빠른 피드백을 주고, 리팩토링을 안전하게 할 수 있게 해준다.

## 단위 테스트란 무엇인가?

단위 테스트: 소프트웨어의 각 컴포넌트에 대한 격리된 테스트

* 컴포넌트: 시스템 행위의 가장 기본적인 단위. 절차형 언어에서 함수, 객체지향 언어에서 클래스.
* 단위 테스트는 빠르게 실행(100 ms 이내)되고 문제의 원인을 찾아내는데 도움이 되어야 한다.

다음과 같은 테스트는 단위 테스트가 아니다. 단위 테스트와는 분리하여 사용•관리해야 한다.

* 데이터베이트에 연결한다.
* 네트워크 통신을 한다.
* 파일 시스템을 변경한다.
* 실행하기 위해 설정 파일과 같은 환경을 조작해야 한다.

## 고수준 테스트

고수준 테스트는 여러 클래스가 관련된 행위를 *pin down* 하는 용도로 쓰일 수 있다. 이는 개별 클래스에 대한 테스트 작성을 쉽게 해준다.

## *Test Coverings*

레거시 코드의 딜레마: 코드를 수정하려면 테스트가 있어야 하는데, 테스트를 작성하려면 코드 수정이 불가피하다.

컴포넌트 간의 의존성을 끊으면 테스트를 작성하는 것이 조금 쉬워진다. 의존성을 끊기 위한 초기 리팩토링은 테스트 없이 보수적으로 수행한다. 이후에는 본격적인 변경을 보다 안전하게 할 수 있다.

오류를 만들어냈을 때의 위험에 따라, 손댄 부분의 코드가 다소 보기 이상하게 되더라도(나중에 개선하면 된다) 초기 리팩토링을 보수적으로 진행할지 말지를 결정한다.

## 레거시 코드 변경 알고리즘

1. 변경 지점을 확인한다. (Identify change points)
2. 테스트 지점을 찾는다. (Find test points)
3. 의존성을 끊는다. (Break dependencies)
4. 테스트를 작성한다. (Write tests)
5. 코드를 변경하고 리팩토링 한다. (Make changes and refactor)

매일매일의 레거시 코드 작업 목표: 의미가 있는 기능적인 변경을 가하면서 동시에 시스템의 더 많은 부분을 테스트 가능하게 만든다.

* 테스트가 가능한 영역의 코드 변경은 점점 쉬워진다.

### 변경 지점 확인

변경 지점은 설계의 영향을 많이 받는다. 어디부터 손을 대야 할지 잘 모르겠다면:

- 16장, *I Don't Understand the Code Well Enough to Change It*
- 17장, *My Application Has No Structure*

### 테스트 지점 찾기

변경 유형별 적용 방법:

- 11장, *I Need to Make a Change. What Methods Should I Test?*
- 12장, *I Need to Make Many Changes in One Area. Do I Have to Break Dependencies for All the Classes Involved?*

### 의존성 끊기

끊어야 할 의존성이 있다는 증거:

* 테스트 도구 내에서 객체를 생성하기 어렵다.
* 테스트 도구 내에서 메써드를 실행하기 어렵다.

상황별 의존성 제거 방법:

- 초기 리팩토링
    - 23장, *How Do I Know That I'm Not Breaking Anything?*
- 흔한 의존성 문제의 해결 절차
    - 9장, *I Can't Get this Class into a Test Harness*
    - 10장, *I Can't Run This Method in a Test Harness*
    - ...
- 거대한 메써드에 얽힌 의존성 때문에 테스트를 작성할 수 없다면
    - 22장, *I Need to Change a Monster Method and I Can't Write Tests for It*
- 의존성은 끊었지만 테스트를 만드는 데 너무 많은 시간이 걸린다면
    - 7장, *It  Takes Forever to Make a Change*

### 테스트 작성

레거시 코드를 변경할 때와 TDD로 개발할 때 작성하는 테스트는 다르다.

레거시 코드 작업에서 테스트의 역할: 13장, *I Need to Make a Change but I Don't Know What Tests to Write*

### 코드 변경 및 리팩토링

새로운 기능을 추가할 때는 TDD를 사용하라: 8장, *How Do I Add a Feature?*

레거시 코드 변경 후 더 생각해볼 부분:

- 20장, *This Class Is Too Big and I Don't Want It to Get Any Bigger*
- 22장, *I Need to Change a Monster Method and I Can't Write Tests for It*
- 21장, *I'm Changing the Same Code All Over the Place*
