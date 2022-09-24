# 클로저란?

## MDN 에서의 클로저

```c
"A closure is the combination of a function bundled together (enclosed) with 
references to its surrounding state (the lexical environment). In other words, 
a closure gives you access to an outer function’s scope from an inner function. 
In JavaScript, closures are created every time a function is created, at function creation time."
```

간단하게 해석하자면 함수가 선언(실행이 아닌)될 때 외부의 렉시켤 환경을 참조하게 되는 현상

말만 들어서는 이게 뭐지? 싶을거다. 이럴땐 예시를 보면서 이해하는게 가장 좋다.

```c
function outer(){
  const name = 'kyle';
  console.log(name)
}
outer() //kyle
console.log(name) //error
```

위의 코드의 결과는 다 당연한 결과다 name은 전역변수가 아닌 함수 내부에 선언되어있기 때문에 console에 name을 찍어도
error가 나온다.

그렇다면 변수 name을 함수 밖에서 사용 할 수는 없을까?
변수 name은 outer이라는 함수의 실행컨텍스트가 종료 되면서 아무도 접근할 수 없게됐다.
name을 함수 밖에서도 사용하기 위해서는 클로져를 사용하면 된다.

```c
function outer(){
  const name = 'kyle';
  console.log(name)
  return function inner(){
    const greeting = 'hello!'
    console.log(greeting,name)
  }
}
const getKyle = outer() //kyle 
getKyle() //hello!kyle
```

outer 함수가 위와 같이 종료됐다.
우리의 예상대로라면 'outer함수가 종료 됐으니 name은 아무데서도 접근할 수 없다' 라고 생각 할 수 있다
하지만 inner함수에서 접근 가능하다. 이게 바로 클로저다.

## 클로저가 필요한 이유

### 1. 전역변수를 줄일 수 있다.
전역변수가 많으면 어디에서든 실수로라도 접근을 할 수 있기 때문에 최대한 전역변수를 줄여서 코딩을 하는게 좋다.
하지만 코딩을 하다보면 함수 하나에서만 사용하는데 전역변수가 필요한 경우가 있는데 이럴때 클로저가 유용하게 사용된다.

```c
const btn = document.querySelector('button')

btn.addEventListener('click',handleClick)

let count = 0
function handleCilck(){
  count++
  return count
}
```
위 코드는 버튼을 누를때마다 1씩 올라가는 count 함수이다.
btn이라는 전역변수를 주고 구현했다. 하지만 저 전역변수가 단지 handleClick 이라는 함수에서만 쓰인다면 전역변수를 줄이는게 더 좋다.

```c
const btn = document.querySelector('button')

btn.addEventListener('click',handleClick())

function handleCilck(){
  let count = 0
  return function (){
    count++
    return count
  }
}
```
위와 같이 작성해 준다면 외부함수의 lexical environment를 참조하는 함수를 btn의 콜백함수로 이용해 전역객체 없이 구현할 수 있다

### 2. 비슷한 형태의 코드의 재사용률을 높일 수 있다.
```c
const newTag = function(open, close) {
    return function(content) {
        return open + content + close
    }
}

const bold = newTag('<b>', '</b>')
const italic = newTag('<i>', '</i>')

console.log(bold(italic("This is my content!")))
//<b><i>This is my content!</i></b>
```
인자에 open,close,content를 한번에 다 받는다면,This is my content! 와 같은 값을 출력을 하고 싶을 때 가독성이 떨어질 수 있다.
하지만 클로져로 구현하면 코드의 가독성도 좋은 재사용하기 편한 코드를 구현할 수 있다.

## 요약

클로저란 내부함수에서 외부함수의 지역변수를 사용할 때 외부함수의 lexcial environment와 함께 bundled 되는 것?(mdn에서는 combination이라고 표현했다.) 이라고 생각하면 될 것이다.
