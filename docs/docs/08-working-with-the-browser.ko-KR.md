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
React는 DOM을 직접 다루지 않기 때문에 굉장히 빠릅니다. React는 메모리에(in-memory) DOM의 표상(representation)을 관리합니다. `render()` 메소드는 DOM의 *서술*를 반환하고, React는 이를 메모리에 있는 DOM의 표상과 비교(diff)해 가장 빠른 방식으로 계산해서 브라우저를 업데이트해 줍니다.
***REMOVED***
게다가 React는 브라우저의 괴악함(quirks)에도 불구하고 모든 이벤트 객체가 W3C 명세를 보장하도록 통합적인 이벤트 시스템을 구현했습니다. 모든 것이 일관된 방식으로 일어나고(bubbles) 효율적으로 크로스 브라우징을 수행합니다. 심지어 IE8에서도 HTML5 이벤트를 사용할 수 있습니다!
***REMOVED***
더 효율적이고 쉬우므로 대개의 경우 React의 "가짜 브라우저"를 이용해 작업을 하게 될 것입니다. 하지만 간혹 jQuery 플러그인 같은 서드파티 라이브러리를 다루다 보면 기저(underlying)의 API에 접근할 필요가 있을지도 모릅니다. React는 기저의 DOM API를 직접 다루는 회피방법을 제공합니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
브라우저와 상호 작용하려면 DOM 노드에 대한 참조가 필요합니다. React는 `ReactDOM.findDOMNode(component)` 함수를 갖고 있으며, 이를 통해서 컴포넌트의 DOM 노드의 참조를 얻을 수 있습니다.
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
    // raw DOM API를 사용해 명시적으로 텍스트 인풋을 포커스 합니다.
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
## 컴포넌트 생명주기
***REMOVED***
컴포넌트의 생명주기에는 세 가지 주요 부분이 있습니다:
***REMOVED***
* **Mounting:** 컴포넌트가 DOM에 삽입되고 있습니다.
* **Updating:** 컴포넌트가 DOM의 업데이트 여부를 결정하기 위해 다시 렌더링되고 있습니다.
***REMOVED***
***REMOVED***
React는 이 프로세스에 훅을 지정할 수 있는 생명주기 메소드를 제공합니다. 발생 직전 시점을 위한 **will** 메소드, 발생 직후 시점을 위한 **did** 메소드가 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
* `componentWillMount()`는 마운팅되기 직전에 호출됩니다.
* `componentDidMount()`는 마운팅 직후 호출됩니다. 초기화에 필요한 DOM 노드는 이곳에 있어야 합니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
* `shouldComponentUpdate(object nextProps, object nextState): boolean`는 컴포넌트가 어떤 변경이 DOM의 업데이트를 보증하는지 결정해야 할 때 호출됩니다. 최적화하려면, React가 업데이트를 무시해야할 때 `this.props`와 `nextProps`를, `this.state`와 `nextState`를 비교해 `false`를 리턴하면 됩니다.
* `componentWillUpdate(object nextProps, object nextState)`는 업데이트가 발생하기 직전에 호출됩니다. 이 시점에는 `this.setState()`를 호출할 수 없습니다.
* `componentDidUpdate(object prevProps, object prevState)`는 업데이트가 발생한 후 즉시 호출됩니다.
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
* `findDOMNode(): DOMElement`는 렌더링 된 DOM 노드에 대한 참조를 얻기 위해 모든 마운트된 컴포넌트에서 호출할 수 있습니다.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
그 철학에 더하여, 우리는 또한 JS 라이브러리의 저자로서 polyfill을 라이브러리에 포함해서 배포하지 않습니다. 만약 모든 라이브러리가 이런 짓을 하면, 같은 polyfill을 여러 번 내리게 되어 쓸모없이 크기만 차지하는 죽은 코드들을 만들 것 입니다. 당신의 제품이 구식 브라우저를 지원해야한다면, [es5-shim](https://github.com/es-shims/es5-shim) 같은 녀석을 사용할 기회가 있었을 겁니다.
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
