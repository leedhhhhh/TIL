## JavaScript 에서의 객체지향 프로그래밍?

내가 학원을 다니면서 배웠던 Java나 C언어처럼 Class 기반의 객체지향 프로그래밍이 있는 반면 JavaScript 는 ProtoType 형태의 객체지향 프로그래밍이다.
이론적으로 알고 있다고 생각했지만 최근에 자바스크립트의 객체지향에 대해 설명을 할 기회가 있었는데 이론적으로 알고 있다고 생각했던 나는 제대로 말로 표현을 하지 못했다.
내가 알고있는 지식을 남들에게 얼마나 잘 설명 할 수 있는지에 따라 내가 얼마나 잘 알고 있는지의 척도라고 생각하기 때문에 자바스크립트 객체지향에 관한 포스팅을 하려고 한다.

### 객체지향프로그래밍이란 뭔가?
객체지향 프로그래밍(Object Oriented Programming)은 문제를 여러 개의 객체 단위로 나눠 작업하는 방식을 말한다. Java, C# 등 많은 언어에서 대표적으로 사용되는 프로그래밍 방식이며
장점으로는 프로젝트 데이터를 독립적인 추상화된 객체로 분리해서 작업을 할 수 있기 때문에 개발자들간의 협업 또는 유지보수 측면에서 우월성을 보인다.

### JavaScript 에서의 객체지향 프로그래밍

```c
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
  this.sayHello = function() {
    alert(this.name + ' said "hello"');
  }
}

var zero = new Person('Zero', 'm'); // Person {name: 'Zero', gender: 'm'}
var hero = new Person('Hero', 'f'); // Person {name: 'Hero', gender: 'f'}
zero.sayHello(); // 'Zero said "hello"'
hero.sayHello(); // 'Hero said "hello"'
```

new Person() 처럼 new를 붙이는 함수를 객체를 생성하는 함수인 자바스크립트에서는 생성자(constructor) 함수라고 불린다.
다른 언어에서는 class가 있지만 자바스크립트에서는 없다(ES6에서 도입되긴함)

또한 함수를 만들 때처럼 function을 쓰긴 했는데 함수와는 달리 대문자로 시작하게 만든다.
이게 규칙이며 생성자를 바탕으로 실제 사람 객체를 만들 수 있다. new라는 키워드를 사용해서 호출하고 new 생성자(인자); 로 사용을 할 수 있다.
 
하나의 Person 생성자를 바탕으로 zero와 hero 두 사람 객체를 만들었고 이 객체들은 공통적으로 sayHello라는 메소드를 갖고 있다.
Person 옆에 (name, gender)는 처음 만들 때 매개변수를 받는 부분임을 알 수 있다. 그렇게 받은 매개변수들을 this.name, this.gender에 저장하고 this는 바로 생성자 함수 자신을 가리킨다.
이렇게 this에 저장된 것들은 new를 통해 객체를 만들 때 그 객체에 적용된다.

### 프로토타입

```c
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
}
Person.prototype.sayHello = function() {
  alert(this.name + ' said "hello"');
};
```

해당 코드는 다른 부분은 위의 코드와 같은데 this.sayHello 대신에 Person.prototype에 sayHello를 넣었다.
prototype 객체는 사전 그대로 원형을 뜻한다. 생성자 함수로 객체가 생성되면 모두 이 원형 객체를 공유하게 된다.
따라서 Person의 prototype 객체에 sayHello 라는 메소드를 넣게 된다면 Person 생성자로 만든 모든 객체는 이 메소드 사용이 가능해진다.

첫번째 코드처럼 this.sayHello 보다는 두번째 코드의 Person.prototype.sayHello 로 사용하는 것이 좀 더 효율적인데 그러한 이유는 prototype은 모든 객체가 공유를 하고 있고
한번만 만들어지지만 만약 this에 넣은 것은 객체 하나를 만들 때마다 메소드도 하나씩 만들어지기 때문에 메모리 낭비가 생기므로 비효율적이다.

### prototype과 _ _proto_ _

```c
new Person('Nero', 'm'); // Person {name: "Nero", gender: "m", __proto__: Object}

// 누르면 나오는
/**
*{
*  constructor: function Person(name, gender),
*  sayHello: function() {},
*  __proto__: Object
*}
*/
```
Nero라는 새로운 사람 객체를 만들었더니 그 안에 처음보는 __proto__ 라는 객체가 있다
constructor과 우리가 추가한 sayHello 그리고 또다시 __proto__가 있다.
__proto__가 바로 실제 객체를 만들 때 생성자의 prototype이 참조된 모습이다. 생성자의 prototype을 참조하기 때문에 __proto__와 prototype은 같다.




