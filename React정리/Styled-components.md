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
