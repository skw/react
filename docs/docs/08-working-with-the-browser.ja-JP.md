***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
Reactはほとんどのケースで、DOMを直接触ることからあなたを解放するパワフルな抽象性を提供します。しかし、単純に根本的なAPIにアクセスする必要がある場合もあります。サードパーティのライブラリや現存するコードと動かす必要があるかもしれません。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
加えて、Reactはブラウザ依存があるにも関わらず、W3Cの使用に則っていると保証されているイベントオブジェクトのような、完全に合成されたイベントシステムを実行します。HTML5のイベントをIE8で使うこともできます！
***REMOVED***
パフォーマンスが優れており、簡単であると思われるので、ほとんどの場合、Reactの「偽のブラウザ」を使うべきです。しかし、jQueryプラグインのようなサードパーティのライブラリと動かすかもしれません。基本的なAPIに単純にアクセスする必要がある時もあります。Reactは基本的なDOMのAPIを直接使うための脱出口を提供しています。
***REMOVED***
## 参照とfindDOMNode()
***REMOVED***
ブラウザと相互に影響するために、DOMノードへの参照が必要になるでしょう。ReactはコンポーネントのDOMノードへの参照を得ることができる `ReactDOM.findDOMNode(component)` 関数を持っています。
***REMOVED***
***REMOVED***
> `findDOMNode()` はマウントされたコンポーネントの上でのみ動きます（これは、DOMに配置されたコンポーネントという意味です）。まだマウントされていない（まだ作成されていないコンポーネントの上で `render()` の `findDOMNode()` を呼ぶようなものです）コンポーネントの上でこれを呼ぼうとした場合、例外がスローされます。
***REMOVED***
Reactのコンポーネントへの参照を得るためには、現在のReactコンポーネントを得るために `this` を使ったり、あなたがオーナーのコンポーネントを表す参照を使ったりできます。それらは、以下のように動きます。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
    // 生のDOMのAPIを使ってテキスト入力に明確にフォーカスします。
***REMOVED***
***REMOVED***
***REMOVED***
    // この参照属性はコンポーネントがマウントされた時に、
    // this.refs のコンポーネントへの参照を追加します。
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
## 参照に関しての詳細
***REMOVED***
参照に関して、詳細に学ぶためと、効率的にそれらを使う方法については、[参照に関しての詳細](/react/docs/more-about-refs.html)ドキュメントを読んでください。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
* **アップデーティング:** DOMがアップデートする必要があるとき、コンポーネントを決定するために再度レンダリングされます。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
* `getInitialState(): object` はコンポーネントがマウントされる前に実行されます。ステートフルなコンポーネントはこのメソッドをインプリメントする必要があり、最初のstateのデータをリターンする必要があります。
***REMOVED***
* `componentDidMount()` はマウンティングが起きた直後に実行されます。DOMノードを必要とする初期化はここで行われるべきです。
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
* `findDOMNode(): DOMElement` はレンダリングされたDOMノードへの参照を得るために、どのマウントされたコンポーネントの上でも実行されます。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
Facebookでは、IE8を含む古いブラウザをサポートしています。私たちは将来に向けたJSを書くことができるように、長い間ポリフィルを使ってきました。これは、私たちのコードベースにたくさんの処理が散らばり、「ただ動くだけの」コードであることを予想することしかできないことを意味します。例えば、 `+new Date()` を見る代わりに、  `Date.now()` と記述しています。オープンソースであるReactを私たちは内部で使っているので、将来に向けたJSを使うという哲学を持ち越しています。
***REMOVED***
この哲学に加えて、私たちはJSのライブラリの作者として、ライブラリの一部としてポリフィルを含めるべきではないというスタンスをとっています。全てのライブラリがこのようなことを行ったなら、死んだコードの大きな塊になりうる同じポリフィルを何度も記述しなくてもよくなるでしょう。あなたのプロダクトが古いブラウザをサポートする必要があるなら、[es5-shim](https://github.com/es-shims/es5-shim)のようなものを使うことにチャンスがあるでしょう。
***REMOVED***
### ポリフィルは古いブラウザをサポートする必要があります
***REMOVED***
[kriskowal's es5-shim](https://github.com/es-shims/es5-shim) の `es5-shim.js` はReactが必要とする以下のようなものを提供します。
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
[kriskowal's es5-shim](https://github.com/es-shims/es5-shim)の `es5-sham.js` もまたReactが必要とする以下のようなものを提供します。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
小さくされていないReactのビルドは[paulmillr's console-polyfill](https://github.com/paulmillr/console-polyfill)にある以下のようなものを必要とします。
***REMOVED***
***REMOVED***
***REMOVED***
`<section>` 、 `<article>` 、 `<nav>` 、 `<header>` 、 `<footer>` を含むHTML5の要素をIE8で使うときには、[html5shiv](https://github.com/aFarkas/html5shiv)か、似たようなスクリプトをインクルードする必要があります。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
詳細な情報については、GitHubのイシューである[onScrollがIE8で動かない](https://github.com/facebook/react/issues/631)を参照してください。
***REMOVED***
