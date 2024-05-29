<h2>useEffect?</h2>
useEffect는 외부시스템과 컴포넌트를 동기화하는 React Hook

`useEffect(setup, dependencies?) `
컴포넌트의 최상위 레벨에서 useEffect를 호출하여 Effect를 선언할 수 있습니다.

<h3>setup(설정)</h3>
Effect의 로직이 포함된 함수, 설정함수는 선택적으로 clean up(정리) 함수를 반환 할 수 있습니다.<br>
React는 컴포넌트가 DOM에 추가된 이후 설정함수를 실행합니다.<br>
의존성에 변화에 따라 컴포넌트가 리렌더링이 되었을경우, <br>
React는 이전 렌더링에 사용된 값으로 정리 함수를 실행한 후 새로운 값으로 설정 함수를 실행합니다.<br>
컴포넌트가 DOM에서 제거된 경우에도 정리함수를 실행합니다.<br>


<h3>dependencies(선택사항)</h3>
설정함수 코드 내부에서 참조되는 모든 반응형 값들이 포함된 배열로 구성,<br>
반응형 값에는 props 와 state, 모든 변수 및 컴포넌트 body에 직접적으로 선언된 함수들이 포함됩니다.<br>
인수를 생략할 경우, Effect는 컴포넌트 리렌더링 될때마다 실행됩니다.<br>
빈배열을 추가했을경우는 처음 렌더링 시에만,<br>
인수가 존재할경우는 인수의 값이 업데이트 될때마다 실행됩니다.<br>


<h3>반환값</h3>

`undefined`


<h3>주의사항</h3>
- useEffect는 Hook이므로 컨포넌트의 최상위 또는 커스텀 Hook에서만 호출할 수 있습니다.<br>
- 외부 시스템과 컴포넌트를 동기화 할 필요가 없는 경우, Effect를 선언할 필요가 없을 수 있습니다.<br>
- Effect가 상호작용(클릭과 같은)에 의해 일어나지 않는다면,<br> 
React는 브라우저가 업데이트된 화면을 그리도록 허용한 후 Effect를 실행합니다. <br>
만약 Effect로 수행하는 작업이 시각적인 효과가 있고 지연이 눈에 띄게 발생한다면(예를 들어, 툴팁을 위치시키는 경우와 같이 화면에 어떤 변화를 주는 경우), <br>
useEffect 대신 <h4>useLayoutEffect</h4>를 사용하십시오.<br>
- Effect는 client 환경에서만 동작합니다. 서버 렌더링에서는 동작하지 않습니다.<br>


<h3>예시</h3>

```
import { useEffect, useRef } from 'react';

export default function ModalDialog({ isOpen, children }) {
  const ref = useRef();

  useEffect(() => {
    if (!isOpen) {
      return;
    }
    const dialog = ref.current;
    dialog.showModal();
    return () => {
      dialog.close();
    };
  }, [isOpen]);

  return <dialog ref={ref}>{children}</dialog>;
}
```
모달 값이 변할때 마다, 동작하는 

```
import { useRef, useEffect } from 'react';

export default function Box() {
  const ref = useRef(null);

  useEffect(() => {
    const div = ref.current;
    const observer = new IntersectionObserver(entries => {
      const entry = entries[0];
      if (entry.isIntersecting) {
        document.body.style.backgroundColor = 'black';
        document.body.style.color = 'white';
      } else {
        document.body.style.backgroundColor = 'white';
        document.body.style.color = 'black';
      }
    }, {
       threshold: 1.0
    });
    observer.observe(div);
    return () => {
      observer.disconnect();
    }
  }, []);

  return (
    <div ref={ref} style={{
      margin: 20,
      height: 100,
      width: 100,
      border: '2px solid black',
      backgroundColor: 'blue'
    }} />
  );
}
```
 IntersectionObserver를 관리하는 Effect,<br>
 Box 컴포넌트 전체가 뷰포트 내에서 완전히 보일 때 배경 색상이 검은색으로 변경되는 것을 확인해 볼 수 있다.



<br><br><br><br>
참고 :: https://ko.react.dev/reference/react/useEffect#useeffect 
