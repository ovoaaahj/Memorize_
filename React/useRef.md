<h1>useRef?</h1>

<h3>useRef</h3>
useRef는 렌더링에 필요하지 않은 값을 참조할 수 있는 Hook!

`const ref= useRef(initialValue)
`

<h4>initialValue</h4>
ref 객체의 current 프로퍼티 초기 설정값, 여기엔 어떤 유형의 값이든 지정 가능

이 인자는 초기 렌더링 이후부터는 무시 됩니다.

<h4>Return Value :: current</h4>

`
return :: {current: 초기값}
`

처음에 전달한 initialValue로 설정, 나중에 다른값으로 변경 가능

ref객체를 JSX노드의 ref 어트리뷰트로 React에 전달하면, React는 current 프로퍼티를 설정합니다.



<h3>주의사항</h3>


ref.current 프로퍼티는 state와 달리 변이 할 수 있습니다.

ref.current 프로퍼티를 변경해도 React는 컴포넌트를 다시 렌더링 하지 않습니다.


ref객체는 일반 javaScript객체이기 때문에 React는 사용자가 언제 변경했는지 알지 못합니다


<h3>장점</h3>
자주 변경되는 값을 state에 담으면, 변경될때 마다 재 렌더링이 일어나서 성능에 안좋은 영향을 미치지만,
useRef를 이용하면 값이 변경될때마다 렌더링이 일어나지 않아서 좋습니다!


<h3>일반 변수와의 차이점?</h3>


```
import {useRef} from "react";

const App = () => {

const countVar = 0;

//const countVar2= useRef(0);

const increaseVar = () => {
countVar = countVar +1;
//countVar2.current = countVar2.current + 1;
}

return (
  <div>
  <p>Var: {countVar} </p>
  <button onClick={increaseVar}> plus </button>
  </div>
)

//이러한 구조에서, plus 버튼을 누르면 var의 값은 0 이된다.
//하지만 useRef를 사용한다면(countVar2) 1이 되는거다.
```


<h3>예시</h3>
input요소에 focus을 주고싶을때 많이 사용된다.

```
import React, { useState, useRef } from "react";

const InputSample = () => {
const [inputs, setInputs] = useState({
    이름: "",
    nickname: "",
  });

const nameFocus = useRef();

const { 이름, nickname } = inputs;

  const onChange = (e) => {
    const { value, name } = e.target;
    setInputs({
      ...inputs,
      [name]: value,
    });
  };

  const onReset = () => {
    setInputs({
      이름: "",
      nickname: "",
    });
    nameFocus.current.focus();
  };
  return (
    <div>
      <input
        name="이름"
        placeholder="이름쓰세요"
        onChange={onChange}
        value={이름}
        ref={nameFocus}
      />
      <input
        name="nickname"
        placeholder="닉네임쓰세요"
        onChange={onChange}
        value={nickname}
      />
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값:</b>
        {이름}({nickname})
      </div>
    </div>
  );
};

export default InputSample;
```

위의 예시에서
`nameFocus.current.focus();` 이부분으로 focus를 준다.

<br><br><br><br><br><br><br>
참조 :: https://hihiha2.tistory.com/19     https://ko.react.dev/reference/react/useRef#useref
