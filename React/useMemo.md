<h1>useMemo?</h1>
useMemo는 리액트의 컴포넌트 성능을 최적화 하는데 사용하는 훅 


여기서 memo는 memoization를 의미, memoization의 자체의 의미는 기억,암기 인데 뜻을 생각해서 기능을 유추하면 


동일한 계산을 반복해야할 때, 이전에 계산한 값을 메모리에 저장함으로써, 동일한 계산의 반복수행을 제거하여 프로그램의 실행속도를 빠르게 하는것으로 생각 할 수 있다.


`useMemo(calculateValue, dependencies)`


<h5>calculateValue</h5>  캐시하려는 값을 계산하는 함수(callback 함수) 

해당 함수는 순수해야하며, 인수를 취하지 않아야 합니다 또한 모든 유형의 값을 반환 해야합니다.


<h5>dependencies</h5>  calculateValue 코드 내부에서 참조되는 모든 반응 값의 목록(의존성 배열), 

반응형 값에는 props, state 및 구성 요소 본체 내부에 직접 선언된 모든 변수와 함수가 포함됩니다. 



<h4>사용하기 좋을때</h4>
비용이 많이 드는 재계산을 건너뛸때 (다시 작업하는데 걸리는 시간이 큰 작업을 건너뛸때)

```
import { useState } from "react";

function TodoList({ todos, tab, theme }) {
  const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
  // ...
}
```

기본적으로 React는 다시 렌더링될 때마다 구성 요소의 전체 본문을 다시 실행합니다. 

`
function TodoList({ todos, tab, theme }) {
  const visibleTodos = filterTodos(todos, tab);
  // ...
}
`

예를 들어, 이것이 TodoList상태를 업데이트하거나 상위로부터 새로운 props를 받으면 함수는 filterTodos 다시 실행됩니다:

일반적으로 대부분의 계산이 매우 빠르기 때문에 이는 문제가 없습니다. 

그러나 대규모 배열을 필터링 또는 변환하거나 비용이 많이 드는 계산을 수행하는 경우, 

데이터가 변경되지 않은 경우 해당 작업을 건너뛰고 싶을 수도 있습니다!

이럴때, useMemo를 사용하여 이미 계산한 값을 사용할 수 있습니다. (값이 변경될때만 작동함)
