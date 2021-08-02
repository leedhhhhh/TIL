# Today I Learned


> 꾸준히 런런!


## Spring Framework

> 인프런 우아한형제들 김영한 팀장님의 스프링 핵심 원리- 기본편 강의를 들으며 정리한 내용입니다. (강의 순서 상관x)

### 스프링이란?  
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

```c 
  스프링 부트
  - 스프링을 편리하게 사용할 수 있도록 지원, 최근에는 기본으로 사용
  - 단독으로 실행할 수 있는 스프링 애플리케이션을 쉽게 생성
  - Tomcat 같은 웹 서버를 내장해서 별도의 웹 서버를 설치하지 않아도 됨
  - 손쉬운 빌드 구성을 위한 starter 종속성 제공
  - 스프링과 3rd parth(외부) 라이브러리 자동 구성
  - 메트릭, 상태 확인, 외부 구성 같은 프로덕션 준비 기능 제공
  - 관례에 의한 간결한 설정
```

```c
  스프링 단어?
  - 스프링이라는 단어는 문맥에 따라 다르게 사용된다.
    - 스프링 DI 컨테이너 기술
    - 스프링 프레임워크
    - 스프링 부트, 스프링 프레임워크 등을 모두 포함한 스프링 생태계
```

### 스프링은 왜 만들었을까?

```c
 스프링의 핵심 개념, 컨셉?
 - 웹 애플리케이션을 만들고, DB 접근을 편리하게 해주는 기술일까?
 - 전자정부 프레임워크?
 - 웹 서버도 자동으로 띄워주는?
 - 클라우드, 마이크로서비스..?
```

```c
  스프링의 진짜 핵심
  - 스프링은 자바 언어 기반의 프레임워크!
  - 자바 언어의 가장 큰 특징- 객체 지향 언어!
  - 스프링은 객체 지향 언어가 가진 강력한 특징을 살려내는 프레임워크
  - 스프링은 은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크
```

>## 객체 지향 설계 5원칙 - SOLID -> 참고자료: https://dev-momo.tistory.com/entry/SOLID-%EC%9B%90%EC%B9%99

```c
  객체 지향 설계 5원칙 - SOLID
  - SRP (Single Responsibillity Principle) : 단일 책임 원칙
  - OCP (Open Closed Principle) : 개방 폐쇄 원칙
  - LSP (Liskov Substitution Principle) : 리스코프 치환 원칙
  - ISP (Interface Segregation Principle) : 인터페이스 분리 원칙
  - DIP (Dependency Inversion Principle) : 의존 역전 원칙
```

#### SRP 단일 책임 원칙 - 한 클래스는 하나의 책임만 가져야 한다!!! 또한 클래스는 그 책임을 완전히 캡슐화해야 함을 일컫는다.

  - 클라이언트 객체는 직접 구현한 객체를 생성하고, 연결하고, 실행하는 다양한 책임을 가지고 있음
  - SRP 단일 책임 원칙을 따르면서 관심사를 분리함
  - 클라이언트 객체는 실행하는 책임만 담당
  - 구현 객체를 생성하고 연결하는 책임은 다른 클래스가 담당
  - 서로의 역할을 다르게! 한 클래스는 하나의 책임만 가지게 한다

#### OCP 개방 폐쇄 원칙 - 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다. 기존 코드를 변경하지 않고 기능을 수정하거나 추가할 수 있도록 설계해야한다.

  - 다형성 사용하고 클라이언트가 DIP를 지킴
  - 애플리케이션을 사용 영역과 구성 영역으로 나눔
  - 소프트웨어 요소를 새롭게 확장해도 사용 영역의 변경은 닫혀 있다.
  - 요구사항이 변경되었을 때 코드에서 변경되어야 하는 부분과 변경되지 않아야하는 부분을 명확하게 구분하여,
  변경되어야 하는 부분을 유연하게 작성하는 것을 의미하며 또한 확장에는 유연하게 반응하며 '변경은 최소화하는 것'을 의미한다.
  
#### LSP 리스코프치환 원칙 - 자식 클래스는 부모 클래스에서 가능한 행위를 수행할 수 있어야 한다.
  
  - 부모 클래스와 자식 클래스 사이의 행위에는 '일관성'이 있어야한다.
  - 객체 지향 프로그래밍에서 부모 클래스의 인스턴스 대신에 자식 클래스의 인스턴스를 사용해도 문제가 없어야 한다
  - 자식 클래스가 부모 클래스를 오버라이딩하거나 추가적인 기능을 통해 부모의 상태를 변경시키는 것은 LSP원칙을 위반하는 것이다.
  - 자식 클래스가 부모 클래스의 책임을 무시하거나 재정의 하지 않고 확장만을 수행한다는 것을 의미한다.

#### DIP 의존관계 역전 원칙 - 프로그래머는 "추상화에 의존해야하며, 구체화에 의존해서는 안된다." 의존성 주입은 이 원칙을 따르는 방법 중 하나이다.
  
  - DIP를 만족한다는 것은 의존관계를 맺을 때, 구체적인 클래스보다 인터페이스나 추상 클래스와 관계를 맺는다는 것을 의미한다.
  - 의존 관계를 맺을 때, 변화하기 쉬운 것보단 변화하기 어려운 것에 의존해야 한다는 원칙이다.

#### ISP 인터페이스 분리 원칙 - 한 클래스는 자신이 사용하지 않은 인터페이스를 구현하지 말아야한다. 하나의 일반적인 인터페이스 보다는, 여러개의 구체적인 인터페이스가 낫다.

  - 자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지 말아야 한다.
  - 인터페이스를 클라이언트에 특화되도록 분리시키는 설계원칙이다.
  - 다양한 기능을 인터페이스화 함으로써 클라이언트에서 인터페이스를 사용할 때 타 인터페이스의 영향을 받지 않고 본인이 구현하고자 하는 기능만을 선택할 수 있게 한다. 


> ## 스프링 컨테이너와 스프링 빈

#### 스프링 컨테이너 생성
```c
  - ApplicationContext를 스프링 컨테이너라 한다.
  - ApplicationContext는 '인터페이스' 이다.
  - 스프링 컨테이너는 xml을 기반으로 만들 수 있고, 에노테이션 기반의 자바 설정 클래스로 만들 수 있다.
  - 자바 설정 클래스를 기반으로 스프링 컨테이너를 만드는 코드는 new AnnotationConfigApplicationContext(???.class); 이다.
    - 이 클래스는 ApplicationContext 인터페이스의 구현체이다.
```

※ 참고: 더 정확히는 스프링 컨체이너를 부를때 BeanFactory, ApplicationContext로 구분해서 이야기한다. BeanFactory를 직접 사용하는 경우는 거의 없고 일반적으로 ApplicationContext를 사용한다.

### 스프링 컨테이너 생성 과정
```c
  1. 스프링 컨테이너 생성
    - new AnnotationConfigApplicationContext(???.class);
    - 스프링 컨테이너를 생성할 때는 구성 정보를 지정해주어야 한다.
  2. 스프링 빈 등록
    - 스프링 컨테이너는 파라미터로 넘어온 설정 클래스 정보를 사용해서 스프링 빈을 등록한다.
    - 빈이름은 메소드 이름을 사용한다.
    - 빈 이름을 직접 부여할 수도 있다. -> @Bean(name="직접 지정하는 빈 이름")
    - 빈 이름은 항상 다른 이름을 부여해야 한다. 같은 이름을 부여하면 다른 빈이 무시되거나 기존 빈을 덮어버리거나 설정에 따라 오류가 발생한다.
  3. 스프링 빈 의존관계 설정 - 준비
  4. 스프링 빈 의존관계 설정 - 완료
   - 스프링 컨테이너는 설정 정보를 참고해서 의존관계를 주입(DI)한다.
   - 단순히 자바 코드를 호출하는 것 같지만, 차이가 있다. 이 차이는 싱글톤 컨테이너 부분에서 자세히 설명
```











### 싱글톤
  - 클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴
  - 객체 인스턴스를 2개 이상 생성하지 못하도록 막아야하는데 그러기 위해선 private 생성자를 사용해서 외부에서 임의로 new 키워드를 사용하지 못하도록 막아야함





----------------------------
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



