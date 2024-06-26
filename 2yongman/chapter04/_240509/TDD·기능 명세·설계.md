■ 기능 명세
-
기능에 대한 명세는 다양한 형태로 존재한다.

어떤 형태가 되든 간에 사용자에게 제공할 기능을 구현하려면 기능을 크게 두 가지로 나누어 생각해 볼 수 있다.

예를 들어 로그인 기능을 생각해보면 아래와 같다.

입력 : 아이디와 암호

결과 : 아이디와 암호가 일치하면 성공, 일치하지 않으면 실패

설계는 기능 명세로부터 시작한다.
스토리보드를 포함한 다양한 형태의 요구사항 문서를 이용해서 기능 명세를 구체화한다. 
기능 명세를 구체화하는 동안 입력과 결과를 도출하고 이렇게 도출한 기능 명세를 코드에 반영한다. 
기능 명세의 입력과 결과를 코드에 반영하는 과정에서 기능의 이름, 파라미터, 리턴 타입 등이 결정된다.

※정리 : 설계를 위한 조건

스토리보드와 요구사항 문서 정리 => 이를 토대로 기능 명세 구체화 => 기능 명세를 통한 입력 출력 결과 도출
 => 코드 반영 => 기능의 이름, 파라미터, 리턴 타입 결정

■ 설계 과정을 지원하는 TDD
=

TDD는 테스트코드를 가장 먼저 작성해야하기 때문에 설계 과정을 지원한다. 왜 그럴까?

※ 테스트 코드를 만들기 위해 필요한 두가지
1) 테스트 할 기능을 실행
2) 실행 결과를 검증

=> 테스트를 하려면 <u>기능</u>이 필요하다. 

=> 기능을 테스트 하기 위해선 테스트에서 실행할 수 있는 <u>객체</u>와 <u>함수</u> 가 필요하다.

=> 객체가 필요하면 클래스와 메서드가 필요하다.

=> 클래스, 메서드의 이름을 결정해야 한다. 

=> 메서드의 파라미터 타입과 개수를 결정해야 한다.

=> 실행 결과, 리턴 타입을 결정한다.

★TDD는 설계 과정을 지원하는 이유는 다음과 같다.

클래스 이름, 메서드 이름, 메서드 파라미터, 실행 결과 이 네 가지를 결정하는 과정에서 고민하는 것이
기본적인 설계 행위이다.

<u>단 오해하지 말자. TDD 자체는 설계가 아니다. TDD는 일부 설계를 도와준다.</u>

■ 필요한 만큼 설계하기
-

TDD는 테스트 통과할 만큼만 코드를 작성해야지, 미리 예측해서 코드를 만들지 않는다.
설계에서도 동일하게 적용되는데 필요할 것을 예측해 미리 설계를 유연하게 만들지 않는다.
실제 테스트 사레를 추가하고 통과시키는 과정에서 피요한 만큼 설계를 변경한다.


■ 기능 명세 구체화
-

테스트 코드를 작성하기 위해 기능 명세 정리가 필요.
스토리보드, 요구사항 문서를 보고 입력 결과를 명확하게 도출해야하지만 애매하다면 실무 담당자에게 반드시 구체적으로 정리해야된다.

