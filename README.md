# 소개
 - 우아한테크코스에서 학습한 내용을 개인적인 공부 목적으로 정리한 저장소입니다.
 > 예시 코드는 src 디렉토리에서 확인할 수 있습니다.

------
# 온보딩
## main method vs JUnit
### main method 의 용도
 - 프로그램을 시작
 - 구현한 프로그램을 테스트
 > 이 과정은 main method 를 테스트 용도로 사용하는 경우에 대해 다루고 있다.

### main method 의 문제점
 - Production code 와 Test code 가 클래스 하나에 존재한다.
 > 클래스 크기가 커짐 -> 복잡도 증가
 - Test Code 가 실서비스에 같이 배포된다.
 - **main method 에서 여러 개의 기능을 테스트한다.**
 - method 이름을 통해 어떤 부분을 테스트하는지에 대한 의도를 들어내기 힘들다.
 - 테스트 결과를 사람이 수동으로 확인한다.
 
### JUnit
 - main method 를 활용해 테스트할 때 발생하는 문제점을 해결하기 위해 등장한 도구가 JUnit 이다.
 - 애노테이션(Annotation)을 활용해 테스트를 구현한다.
    - @Test
    - @BeforeEach, @Aftereach
    - @BeforeAll, @AfterAll
 > JUnit 5.x 기준    
 - Assert 클래스의 static assert method 를 활용해 테스트 결과를 검증한다.
 
### Assertion
 - assertj: 메소드 체이닝을 통해 좀 더 깔끔하고 읽기 쉬운 assert 코드를 구현할 수 있다.
 
## 학습테스트와 단위테스트
### 학습테스트란?
 - 기능구현을 위한 테스트라기 보다는 새로운 API, 라이브러리, 프레임워크가 어떻게 동작하는지를 검증하기 위한 테스트

### 학습테스트 장점
 - 다양한 조건에 따른 기능을 손쉽게 확인해 볼 수 있다.
 - 학습 테스트 코드를 개발 중에 참고할 수 있다.
 - 프레임워크나 제품을 업그레이드할 때 호환성 검증을 보여준다.
 - 테스트 코드 작성에 좋은 훈련이 된다.
 - 새로운 기술을 검증하는 과정이 즐거워진다.
 
### 단위 테스트
단위 테스트는 프로덕션 코드를 구현한 후 JUnit 과 같은 도구를 활용해 작은 단위를 테스트하는 것을 의미한다.
단위 테스트와 TDD 는 다르다.

------
내가 구현하는 메소드(함수) 중
Input 과 Output 이 명확한 클래스 메소드(보통 Util 성격의 메소드)
에 대한 단위 테스트 연습

------
알고리즘을 학습한다면 알고리즘 구현에 대한 검증을 단위 테스트로 한다.
알고리즘은 Input, Output 이 명확하기 때문에 연습하기 좋다.

## 자바 문자열
### 학습 목표
 - 문자(char, Character)와 문자열(String)
 - StringBuilder 와 StringBuffer
 
### 문자와 문자열
 - 문자열(String)은 자바 프로그램이 실행되는 동안 가장 많이 생성되는 객체이다.
 - 문자열은 객체이지만 각각의 문자의 나열로 구성된다.
 - char capitalA = 'A'; // 문자
 - String a = "abc"; // 문자열 == 문자의 배열
 - String b = new String("abc"); // **이따구로 구현하지 마라.**
 
### StringBuilder API
String + String vs StringBuilder
 - String 은 불변(Immutable)하기 때문에 String 과 String 을 더하면 String 객체를 생성한다. 따라서 String 과 String 을 더하는 시점에 메모리 할당과 메모리 해제가 계속해서 발생한다.
 - StringBuilder 는 String 과 다르게 기존 데이터에 새로운 데이터를 더하는 방식을 취하기 때문에 속도가 더 빠르다.
 - 따라서 긴 문자열을 더하는 상황이 발생할 경우 StringBuilder 를 활용해 구현한다.
 ------
 Immutable
  - Immutable(불변)이란 객체를 생성한 후 상태를 변경할 수 없는 것을 의미한다.
  - String 객체는 문자열의 상태 값을 변경할 수 없기 때문에 Immutable 객체라 한다.
  
## 자바 List, Generic
### List
#### java.util.List Interface
 - 자바는 배열과 같은 데이터를 효과적으로 처리하기 위해 배열 대신 List 를 제공한다.
 - List 는 ArrayList, LinkedList 두 가지 종류가 있다. 일반적으로 ArrayList 를 가장 많이 사용한다.
 - List 는 배열에서 지원하지 않는 많은 기능을 제공한다.
 - 지금까지 배열을 사용했다면 배열대신 List 를 사용한다.
 
#### ArrayList vs LinkedList
 - ArrayList 와 LinkedList 사용 방법은 같다.
 - 다른 점은 데이터를 저장하는 방식이 다르다는 것 뿐이다.
 - ArrayList 데이터 저장 방식
 ------
 Index: 0 1 2 3 4 
 Value: 1 4 6 7 9
 ------
 - LinkedList 데이터 저장 방식
 ------
 1|· -> 4|· -> 6|· -> 7|· -> 9

 ------


 ### Generic
 - List 와 같이 다양한 종류의 데이터를 관리하는 경우 데이터 타입을 특정 데이터 타입으로 고정할 수 있다.
 
 ### Generic 장점
 - 특정 타입으로 고정함으로써 타입 안정성을 제공한다.
 - 타입 체크와 형변환을 생략할 수 있으므로 코드가 간결해 진다.
 
### Generic 을 사용하지 않을 경우
 - 다양한 종류의 객체의 타입을 추가할 수 있다. (특정 Type => Object)
 - 추가한 객체 타입을 사용하려면 다시 형변환을 해야 한다. (Object => 특정 Type)
 
### Generic 을 사용하는 경우
 - ArrayList<String> 와 같이 <>을 이용해 ArrayList 가 관리하는 타입을 지정한다.
 - 이와 같이 타입을 지정하면 해당 타입만 추가할 수 있다. 다른 타입을 저장하면 컴파일 에러가 발생한다.
**특별히 예외적인 상황이 아니라면 Generic 을 사용한다.**

## JavaDoc 읽기
 - 자바에서 제공하는 API 를 사용할 때 JavaDoc 문서를 참고해 사용법을 익힌다.