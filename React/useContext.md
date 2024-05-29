<h1>useContext?</h1>
useContext는 컴포넌트에서 context를 읽고 구독할 수 있는 React Hook 입니다.

`
const value = useContext(SomeContext)
`

<h3>SomeContext</h3>
createContext로 생성한 context, context 자체는 정보를 담고 있지 않으며, 
컴포넌트에서 제공하거나 읽을 수 있는 정보의 종류를 나타냅니다

```
import { useContext } from 'react';

function MyComponent() {
  const theme = useContext(ThemeContext);
  // ...
```

<h3>return Value</h3>
호출되는 컨포넌트에 대한 context값을 반환합니다.<br>
이값은 트리에서 호출하는 컴포넌트 위의 가장 가까운 SomeContext.Provider에 전달된 Value로 결정됩니다.<br>
Provider가 없으면 반환된 값은 해당 컨텍스트에 대해 createContext에 전달한 defaultValue가 됩니다.<br>
반환된 값은 항상 최신상태 입니다.<br>
컨텍스트가 변경되면, React는 자동으로 해당 context를 읽는 컴포넌트를 다시 렌더링 합니다.<br>

<h3>주의사항</h3>
- 컴포넌트 내의 useContext() 호출은 동일한 컴포넌트에서 반환된 provider에 영향을 받지 않습니다.<br>
해당하는 "Context.Provider" 는 useContext() 호출을 하는 컴포넌트 위에 배치되어야 합니다.<br>
- React는 다른 value을 받는 provider로부터 시작해서 특정 context를 사용하는 모든 자식들을 자동으로 리렌더링합니다. <br>
  이전 값과 다음 값은 Object.is 비교를 통해 비교됩니다. memo로 리렌더링을 건너뛰어도 자식들이 새로운 context 값을 받는 것을 막지는 못합니다.<br>
- 빌드 시스템이 결과물에 중복 모듈을 생성하는 경우(심볼릭 링크에서 발생할 수 있음) context가 손상될 수 있습니다. <br>
  context를 통해 무언가를 전달하는 것은 === 비교에 의해 결정되는 것처럼 컨텍스트를 제공하는 데 <br>
  사용하는 SomeContext와 context를 읽는 데 사용하는 SomeContext가 정확하게 동일한 객체인 경우에만 작동합니다.<br>
