# Today I Learned 
<br />

## JavaScript

> let, const는 Hoisting을 하지만..... 다만?

### Hoisiting?
- [ ] 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것

### TDZ?
- [ ] 생명주기를 알아보기전에 let과 const에 설명되는 개념인 TDZ란 무엇일까?
- [ ] TDZ란 변수가 선언되고 초기화되기의 범위를 TDZ(Temporal Dead Zone)에 있다고 한다.

### var, let, const 생명주기
- [ ] var는 선언과 초기화가 동시에 일어난다. 고로 변수를 선언전에 접근해도 error 가 뜨는게 아닌 undefined가 뜬다.
- [ ] let과 const는 선언과 초기화가 따로 일어나고, TDZ는 그 사이 시간, 즉 스코프의 시작 지점에서 초기화 시작 지점까지의 구간을 말한다. 초기화는 변수 선언문에 도달해야 이루어진다.

1) var
```c
console.log(myName); // undefined
var myName = "taenami";
```
- var는 선언하기 전에 사용할 수 있다.
- myName 이라는 변수는 error 대신 undefined가 나오는데 var로 선언된 변수는 '호이스팅'이 되기 때문이다.

2) let, const
```c
console.log(myName); // ReferenceError
let myName = "taenami";
```
```c
console.log(myName); // ReferenceError
const myName = "taenami";
```
- let과 const로 선언된 변수는 선언하기 전에는 사용 할 수 없다.
- 위와 같은 에러가 발생한다고 해서 호이스팅 되지 않는 것은 아니다!
- TDZ에 영향을 받기 때문인데, TDZ에 있는 변수들은 사용할 수가 없다.

### let과 const도 hoisting 한다!
var와 다르게 let과 const는 선언하면 초기화되지 않은 상태로 남는다. 그리고 초기화 되기 전에 접근하려고 하면 오류를 나타낼뿐이다.
```c
let foo = 1; // 전역 변수

{
  console.log(foo); // ReferenceError: foo is not defined
  let foo = 2; // 지역 변수
}
```
위 코드에서 만약 호이스팅이 되지 않는다면 Scope chain에 의해 전역 변수인 foo에 할당된 1이 출력이 되야 하지만 let으로 선언된 블럭 스코프 안에서 hoisting이 되고
변수 선언문을 만나기 전까지는 TDZ에 빠져서 오류가 나는 것이다.


<br /><br /><br /><br />
## React
   
> React , Redux, Hook 등 공부하면서 정리

### styled-components  

> styled-components 적용X
```c
import styled from "styled-components";

function App() {
  return (
    <div stlye={{display:flex}}>
      <div style={{backgroundColor: "teal" , width: 100, height: 100}}></div>
      <div style={{backgroundColor: "teal" , width: 100, height: 100, border-radius:50}}></div>
    </div>
  );
}

export default App;
```


> styled-components 적용
```c
import styled from "styled-components";

const Father = styled.div`
  display: flex;
`;

const Box = styled.div`
  background-color: ${(props) => props.bgColor};
  width: 100px;
  height: 100px;
`;

const Circle = styled(Box)`
  border-radius: 50px;
`;

function App() {
  return (
    <Father>
      <Box bgColor="teal" />
      <Circle bgColor="tomato" />
    </Father>
  );
}

export default App;

```

리액트는 컴포넌트가 가장 큰 장점 적용 시킨 코드와 적용시키지 않은 코드 중에 뭐가 컴포넌트 관리가 더 용이한지 생각해보기


> const interface = styled.span<{인터페이스명}>` 

ex1) 
```c
const Tab = styled.span<{ isActive: boolean }>`
```
ex2)
```c
interface isActive {
   isActive: boolean;
}

const Tab = styled.span<isActive>`
```
