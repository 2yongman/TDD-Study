■ Junit5 기초
- 

■ Junit5 모듈 구성
- 

- Junit 플랫폼 : 테스팅 프레임워크를 구동하기 위한 런처와 테스트 엔진을 위한 API 제공
- Junit 주피터(Jupiter) : Junit 5를 위한 테스트 API와 실행 엔진 제공
- Junit 빈티지(Vintage) : Junit 3, 4로 작성된 테스트를 Junit 5 플랫폼에서 실행하기 위한 모듈 제공

■ Junit 코드 기본 구조
- 

    public class SumTest {
        @Test
        void sum(){
            int result = 2+3;
            assertEquals(5,result);
    }

테스트로 사용할 클래스를 만든 후 @Test 애노테이션을 메서드에 붙힌다. @Test 애노테이션을 붙힌 메서드는 private 이면 안된다.

■ Assertions 클래스가 제공하는 주요 단언 메서드
-

- assertEquals(expected, actual) : 실제 값(actual)이 기대하는 값(expected)과 같은지 검사
- assertNotEquals(unexpected, actual) : 실제값(actual)이 특정 값(unexpected)과 같지 않은지 검사
- assertSame(Object expected, Object actual) : 두 객체가 동일한 객체인지 검사
- assertNotSame(Object unexpected, Object actual) : 두 객체가 동일하지 않은 객체인지 검사
- assertTrue(boolean condition) : 값이 true 인지 검사
- assertFalse(boolean condition) : 값이 false 인지 검사
- assertNull(Object actual) : 값이 null 인지 검사
- assertNotNull(Object actual) : 값이 null 아닌지 검사
- fail() : 테스트를 실패 처리함

■ fail() 메서드와 익셉션 발생 유무가 검증 대상일 때
- 

fail() 메서드는 테스트테 실패했음을 알린다.

ID와 암호로 전달받은 팔미터 값이 null이면 IllegalArgument Exception이 발생하도록 인증 기능을 구현해본다 가정해보자.

테스트 코드는 ID와 암호를 null 전달했는데 익셉션이 발생하지 않으면 테스트 실패이다.

    try{
        AuthService authService = new AuthService();
        authSevice.authenticate(null, null);
        fail();
    } catch(IllegalArgumentException e) {
    }

익셉션 발생 유무가 검증 대상이라면 fail() 메서드를 사용하는 것보다 두 메서드를 사용하자.

- assertThrows(Class(T) expectedType, Executable executable) : executalbe을 실행한 결과로 지정한 타입의 익셉션이 발생하는지 검사
- assertDoesNotThrow(Executable executable) : executable을 실행한 결과로 익셉션이 발생하지 않는지 검사

assertThrows() 메서드는 발생한 익셉션 객체를 리턴하기도 한다.

■ 모든 검증을 실행하고 그 중 실패한 것이 있는지 확인하는 메서드 : assertAll()
-

    assertAll(
        () -> assertEquals(3,5/2),
        () -> assertEquals(4,2*2),
        () -> assertEquals(6,11/2)
    );

assertAll() 메서드는 Executable 목록을 가변 인자로 전달받아 각 Executable을 실행한다.
실패한 코드가 있으면 그 목록을 모아 에러 메시지로 보여줌.


■ @BeforeEach 애노테이션과 @AfterEach 애노테이션
-

Junit은 각 테스트 메서드마다 다음 순서대로 실행한다.
 
1) 테스트 메서드를 포함한 객체 생성
2) @BeforeEach 애노테이션이 붙은 메서드 실행
3) @Test 애노테이션이 붙은 메서드 실행
4) @AfterEach 애노테이션이 붙은 메서드 실행

@BeforeEach 애노테이션은 테스트를 실행하는데 필요한 준비 작업을 할 때 사용한다.
ex) 테스트에 사용할 임시 파일 생성, 테스트 메서드에서 사용할 객체 생성

@AfterEach 애노테이션은 테스를 실행한 후 정리할 것이 있을 때 사용한다.
ex) 테스트에 사용한 임시파일을 삭제할 때

■ @BeforeAll 애노테이션과 @AfterAll 애노테이션
- 
@BeforeAll : 클래스의 모든 테스트 메서드를 실행하기 전에 한 번 실행된다.
@AfterAll : 클래스의 모든 테스트 메서드를 실행한 뒤 실행된다.

■ 테스트 메서드 간 실행 순서 의존과 필드 공유하지 않기
-
각 테스트 메서드는 서로 독립적으로 동작해야한다.

서로 필드를 공유한다거나 실행 순서를 가정하고 테스트를 작성하면 안된다.


