***REMOVED***
***REMOVED***
title:  컴포넌트 명세와 생명주기
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
## 컴포넌트 명세
***REMOVED***
`React.createClass()`를 호출하여 컴포넌트 클래스를 생성할 때, `render` 메소드를 포함한 명세 객체를 제공해야 합니다. 또한 필요한 경우 여기에서 설명하는 다른 생명주기 메소드를 명세 객체에 추가로 제공할 수 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
`render()` 메소드는 필수 항목입니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
`render()` 함수는 순수 함수여야 합니다. 즉, 컴포넌트의 상태를 변경하지 않고, 여러번 호출해도 같은 결과를 리턴하며, DOM을 읽고 쓰거나 브라우저와 상호작용(예를 들어 `setTimeout`를 사용)하지 않아야 합니다. 브라우저와 상호작용해야 한다면 `componentDidMount()`나 다른 생명주기 메소드에서 수행해야 합니다. `render()` 함수를 순수 함수로 유지하면 서버 렌더링이 훨씬 쓸만해지고 컴포넌트에 대해 생각하기 쉬워집니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
## 생명주기 메소드
***REMOVED***
컴포넌트의 생명주기에서 특정 시점마다 실행되는 메소드들입니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
최초 렌더링이 일어나기 직전에 클라이언트 및 서버에서 한번 호출됩니다. 이 메소드 안에서 `setState`를 호출하면, `render()`에서 업데이트된 state를 확인할 수 있고 state가 변함에도 불구하고 `render()`가 한번만 실행됩니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
다른 JavaScript 프레임워크를 연동하거나, `setTimeout`/`setInterval`로 타이머를 설정하고 AJAX 요청을 보내는 등의 작업을 이 메소드에서 합니다.
***REMOVED***
***REMOVED***
### 업데이트 시: componentWillReceiveProps
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
`render()`가 호출되기 전에 prop의 변화를 감지하여 `this.setState()`를 호출해서 state를 업데이트할 수 있습니다. 이전 props는 `this.props`로 접근할 수 있습니다. 이 함수 안에서 `this.setState()`를 호출해도 추가 렌더링이 발생하지 않습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
> `componentWillReceiveState`에 해당하는 메소드는 없습니다. prop이 변할 때 state가 바뀔 수는 있지만, 그 역은 불가능합니다. state의 변화에 따라 작업을 실행해야 하면 `componentWillUpdate`를 사용하세요.
***REMOVED***
***REMOVED***
***REMOVED***
### 업데이트 시: shouldComponentUpdate
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
새로운 props와 state가 컴포넌트 업데이트를 필요로 하지 않는 것이 확실하다면
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
기본적으로 `shouldComponentUpdate`는 항상 `true`를 리턴합니다. `state`가 제자리에서(in place) 바뀐 경우에 발생하는 파악하기 힘든 버그를 막기 위함입니다. 하지만 `state`가 항상 변경 불가능하도록 주의하고 `render()`에서 `props`와 `state`를 읽기만 하면 이전 props 및 state와 바뀌는 값을 비교하는 `shouldComponentUpdate`를 직접 구현할 수 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
### 업데이트 시: componentWillUpdate
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
업데이트가 일어나기 전에 준비하기 위해 사용할 수 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
> 이 메소드에서는 `this.setState()`를 호출할 수 없습니다. prop 변화에 반응하여 state를 업데이트해야 할 경우, `componentWillReceiveProps`를 대신 사용하세요.
***REMOVED***
***REMOVED***
### 업데이트 시: componentDidUpdate
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
컴포넌트의 업데이트가 DOM에 반영된 직후에 호출됩니다. 최초 렌더링 시에는 호출되지 않습니다.
***REMOVED***
컴포넌트가 업데이트된 뒤 DOM을 조작해야 하는 경우 사용할 수 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
이 메소드에서 타이머를 무효화하거나 `componentDidMount`에서 만들어진 DOM 엘리먼트를 정리하는 등 필요한 정리 작업을 수행할 수 있습니다.
