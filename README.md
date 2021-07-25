# Today I Learned


> 꾸준히 런런


## Spring Framework

> 인프런 우아한형제들 김영한 팀장님의 스프링 핵심 원리- 기본편 강의를 들으며 정리한 내용입니다.


```c
  스프링 프레임워크
  - 핵심기술 : 스프링 DI 컨테이너, AOP, 이벤트, 기타
  - 웹기술: 스프링MVC, 스프링 WebFlux
  - 데이터 접근 기술: 트랜잭션, JDBC, ORM 지원, XML 지원
  - 기술 통합: 캐시, 이메일, 원격접근, 스케줄링
  - 테스트: 스프링 기반 테스트 지원
  - 언어: 코틀린, 그루비
  - 최근에는 스프링 부트를 통해서 스프링 프레임워크의 기술들을 편리하게 사용
```


## Java 객체지향프로그래밍

> 자바란 무엇인지 심도있게 공부해보고 싶어 인프런의 JavaTPC 강의를 들으며 정리한 내용입니다. 

```c
  프로그래밍의 3대 요소?
  1. 변수(Variable)
   - 데이터를 저장할 메모리 공간의 이름(symbol)
  2. 자료형(Data Type)
   - 변수의 크기와 변수에 저장될 데이터의 종류를 결정하는 것
  3. 할당(Assign)
   - 변수에 값을 저장(대입,할당)하는 것
```
```c
자료형(DataType)
-> 기본자료형(PDT) : 컴파일러에서 기본적으로 제공해주는 자료형
-> 사용자정의자료형(UDDT) : 객체 자료형(Object DataType)
    - 필요에 의해서 새롭게 만들어 사용하는 자료형
    - 만드는 도구, 설계하는 도구, 모델링하는 도구가 필요하다. : class!
```
기본자료형
종류|자료형|크기(byte)|예시
---|---|---|---|
정수|short,int,long|2,4,8|10,20|
실수|float, double|4,8|23,4f,34.567...|
문자|char|2|'A','a'|
불리언|boolean|1|false or true|

사용자정의자료형
종류|자료형|예시
---|---|---|
책|BookDTO|자바의 정석(제목,가격,출판사)|
회원|MemberVO|김길동(이름,주소,전화번호)|
문자열|String|"apple"|

-> 우리가 만드는 객체는 프로젝트에 따라 다양하므로 class로 언제든지 만들어 사용하면 된다.



