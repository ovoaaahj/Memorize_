# useCallback?
`useCallback` 은 리렌더링 간의 함수를 정의해주는 React Hook

`const cachedFn = useCallback(fn,dependencies)`

### fn
캐싱할 함수값, 이함수는 어떤 인자나 반환값도 가질수 있습니다.<br>
React는 첫 렌더링에서 이 함수를 반환 합니다.<br>
반대로 dependencies 값이 변경되었다면, 이번렌더링에서 전달한 함수를 반환하고 나중에 재사용할 수 있도록 이를 저장합니다.<br>
React는 함수를 호출하지 않습니다. 이함수의 호출여부는 개발자가 결정할 수 있습니다.<br>

### dependencies
fn내에서 참조되는 반응형의 값의 목록입니다.<br>
반응형 값으로 props와 state 그리고 컴포넌트안에서 선언된 모든 변수와 함수를 포함합니다.<br>


예시

```
const calculate = useCallback((num) => {
    return num + 1;
}, [item])
```



<br><br>
<br>
<br>
<br>
<br>

참조 :: https://ko.react.dev/reference/react/useCallback   https://velog.io/@hjthgus777/React-%EB%8B%A4%EC%8B%9C-%ED%95%9C%EB%B2%88-useCallback%EC%9D%84-%ED%8C%8C%ED%97%A4%EC%B3%90%EB%B3%B4%EC%9E%90
