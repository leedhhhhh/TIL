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

```c
  BeanFactory
    - 스프링 컨테이너의 최상위 인터페이스이다.
    - 스프링 빈을 관리하고 조회하는 역할을 담당한다.
    - getBean()을 제공한다.
    - 지금까지 우리가 사용했던 대부분의 기능은 BeanFactory가 제공하는 기능이다.
    
  ApplicationContext
    - BeanFactory 기능을 모두 상속받아서 제공한다.
    - 빈을 관리하고 검색하는 기능을 BeanFactory가 제공해주는데, 그 둘의 차이는?
    - 애플리케이션을 개발할 때는 빈은 관리하고 조회하는 기능은 물론이고, 수 많은 부가기능이 필요하다.

```

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

### 빈 출력
  
  - 모든 빈 출력하기
    - 실행하면 스프링에 등록된 모든 빈 정보를 출력할 수 있다.
    - getBeanDefinitionNames() : 스프링에 등록된 모든 빈 이름을 조회한다.
    - getBean() : 빈 이름으로 빈 객체(인스턴스)를 조회한다.
  
  - 애플리케이션 빈 출력하기
    - 스프링이 내부에서 사용하는 빈은 제외하고, 내가 등록한 빈만 출력해보자.
    - 스프링이 내부에서 사용하는 빈은 getRole()로 구분할 수 있다.
      - ROLE_APPLICATION : 일반적으로 사용자가 정의한 빈
      - ROLE_INFRASTRUCTURE : 스프링이 내부에서 사용하는 빈

  - 동일한 타입이 둘 이상인 스프링 빈 조회
    - 타입으로 조회시 같은 타입의 스프링 빈이 둘 이상이면 오류가 발생한다. 이럴때는 빈이름을 지정해준다.
    - getBeansOfType() 을 사용하면 해당 타입의 모든 빈을 조회할 수 있다.


### 스프링 빈 조회- 상속관계

  - 부모 타입으로 조회하면, 자식 타입도 함께 조회한다.
  - 그래서 모든 자바 객체의 최고 부모인 Object 타입으로 조회하면, 모든 스프링 빈을 조회한다.


> ## 싱글톤 컨테이너

```c
  - 우리가 만들었던 스프링 없는 순수한 DI컨테이너는 요청을 할 때마다 객체를 새로 생성한다.
  - 고객 트래픽이 초당 100이 나오면 초당 100개의 객체가 생성되고 소멸된다. 즉! 메모리 낭비가 굉장히 심하다.
  - 해결방안은 해당 객체가 딱 1개만 생성되고, 공유하도록 설계하면 된다.
  
  이것이 싱글톤 패턴이다!
```

### 싱글톤
  - 클래스의 인스턴스가 딱 1개만 생성되는 것을 보장하는 디자인 패턴
  - 객체 인스턴스를 2개 이상 생성하지 못하도록 막아야하는데 그러기 위해선 private 생성자를 사용해서 외부에서 임의로 new 키워드를 사용하지 못하도록 막아야함

### 싱글톤 패턴의 문제점
  - 싱글톤 패턴을 구현하는 코드 자체가 많이 들어간다.
  - 의존관계상 클라이언트가 구체 클래스에 의존한다. -> DIP를 위반한다.
  - 클라이언트가 구체 클래스에 의존해서 OCP 원칙을 위반할 가능성이 높다.
  - 테스트하기가 어렵다.
  - 내부 속성을 변경하거나 초기화 하기 어렵다.
  - private 생성자로 자식 클래스를 만들기 어렵다.
  - 결론적으로 유연성이 떨어진다.
  - 안티패턴으로 불리기도 하다.


### 싱글톤 컨테이너
  - 스프링 컨테이너는 싱글톤 패턴을 적용하지 않아도, 객체 인스턴스를 싱글톤으로 관리한다.( 잘 생각해보자. 컨테이너는 객체를 '하나'만 생성해서 관리한다. 그럼 굳이 싱글톤패턴을..?)
  - 스프링 컨테이너는 싱글톤 컨테이너 역할을 한다. 싱글톤 객체를 생성하고 관리하는 기능을 싱글톤 레지스트리라 한다.
  - 스프링 컨테이너의 이런 기능 덕분에 싱글턴 패턴의 모든 단점을 해결하면서 객체를 싱글톤으로 유지할 수 있다.
  - 싱글톤 패턴을 위한 지저분한 코드가 들어가지 않아도 된다.
  - DIP, OCP, 테스트, private 생성자로부터 자유롭게 싱글톤을 사용할 수 있다.
  - 스프링 컨테이너를 사용하는 테스트 코드를 짜서 실험하면 참조값이 같은 것을 확인 할 수 있다. 즉 스프링 컨테이너는 고객의 요청이 올 때 마다 객체를 생성하는 것이 아니라, 이미 만들어진 객체를 공유해서 효율적으로 재사용할 수 있다는 것이다.

### 싱글톤 방식의 주의점 (영한님이 정말 강조하신 부분 중요!!!)
  - 싱글톤 패턴이던 스프링 같은 싱글톤 컨테이너를 사용하던, 객체 인스턴스를 하나만 생성해서 공유하는 싱글톤 방식은 여러 클라이언트가 하나의 같은 객체 인스턴스를 공유하기 때문에 싱글톤 객체는 상태를 유지(stateful)하게 설계하면 안된다.
  - 반드시 무상태로 설계해야한다!
    - 특정 클라이언트에 의존적인 필드가 있으면 안된다.
    - 특정 클라이언트가 값을 변경할 수 있는 필드가 있으면 안된다.
    - 가급적 읽기만 가능해야한다.
    - 필드 대신에 자바에서 공유되지 않는 지역변수, 파라미터, ThreadLocal 등을 사용해야 한다.
  - 스프링 빈의 필드에 공유 값을 설정하면 정말 큰 장애가 발생할 수 있다.

#### 예시코드
```java
  
  public class StatefulService {
  
    private int price; // 상태를 유지하는 필드
    
    public void order(String name, int price){
      System.out.println("name = " + name + " price = " + price);
      this.price = price; // 여기가 문제!
    }
    
    public int getPrice(){
      return price;
    }
  }

```
```java
  public class StatefulServiceTest {
  
    @Test
    void statefulServiceSingleton() {
      ApplicationContext ac = new AnnotationConfigApplicationContext(TestConfig.class);
      StatefulService statefulService1 = ac.getBean("statefulService", StatefulService.class);
      StatefulService statefulService2 = ac.getBean("statefulService", StatefulService.class);
      
      //ThreadA: A사용자 10000원 주문
      statefulService1.order("userA", 10000);
      
      //ThreadB: B사용자 20000원 주문
      statefulService2.order("userB", 20000);
      
      //ThreadA: 사용자A 주문 금액 조회
      int price = statefulService1.getPrice();
      
      //ThreadA: 사용자A는 10000원을 기대했지만, 기대와 다르게 20000원 출력
      System.out.println("price = " + price);
      
      Assertions.assertThat(statefulService1.getPrice()).isEqualTo(20000);
      }
      
      static class TestConfig {
      
      @Bean
      public StatefulService statefulService() {
        return new StatefulService();
      }
     }
  }
```
```
싱글톤 컨테이너는 이미 만들어진 객체를 공유해서 효율적으로 재사용한다.  
TestConfig 클래스를 스프링 컨테이너로 만들었고 그로 인해 계속 새로운 객체를 생성하는 것이 아닌 이미 만들어진 객체를 공유해서 사용한다는 것을 알 수 있다. 
그로 인해 userA의 1만원이 들어갔지만 새로운 객체를 생성하는게 아니라 객체를 공유하기 때문에 다시 userB의 2만원이order(String name, int price)에 담기게 되고 
그로 인해 getPrice 메소드의 price 반환값이 2만원이 되어 2만원이 출력이 된 것이다. 
```


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



