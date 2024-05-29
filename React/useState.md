<h1>useState?</h1>
useState는 컴포넌트에 state 변수를 추가할 수 있는 React Hook 입니다.

`
const [state,setState] = useState(initialState)
`

<h3>initalState</h3>
state의 초기 설정값, 어떤 유형의 값이든 지정할 수 있지만,<br>
함수에 대해서는 특별한 동작이 존재, 해당 인수는 초기 렌더링 이후 무시됩니다.<br>

- 함수로 initialState로 전달하면, 이를 초기화 함수로 취급합니다.<br>
이함수는 순수해야하고 인수를 받지 않아야 하며, 반환값은 반드시 존재 해야 합니다.<br>

<h3>return Value</h3>
useState는 정확히 두 개의 값을 가진 배열을 반환 합니다.<br>
1. 현재의 state<br>
2. state를 다른값으로 업데이트 하고 리렌더링을 촉발할 수 있는 set 함수<br><br><br>


```
import { useState } from 'react';

function MyComponent() {
  const [age, setAge] = useState(42);
  const [name, setName] = useState('Taylor');
  // ...
```

<br>

```
function handleClick() {
  setName('Robin');
}
```

<br>
<br>
<br>
<br>
<br>


참고 :: https://ko.react.dev/reference/react/useState
