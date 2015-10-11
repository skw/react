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
首先你想要做的是在模型里的每一个组建周围绘制边框并给他们命名。如果你和设计师一起工作，他们应该已经完成这步了，所以去和他们谈谈！他们的photoshop图层名也许最终会成为你的React组件名。
***REMOVED***
但是你如何知道什么东西应该是独立的组件？只需使用你决定是否创建一个函数或者对象的相同技术。这样一种技术是[single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)，即是，一个组件在理想情况下只做一件事情。如果它最终变大，它就应该被分解为更小的组件。
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
  1. **`FilterableProductTable` (orange):** 包含示例的整体
  2. **`SearchBar` (blue):**  接受所有 *用户输入*
  3. **`ProductTable` (green):** 基于 *用户输入* 显示和过滤 *数据集合(data collection)*
***REMOVED***
***REMOVED***
***REMOVED***
如果你看着 `ProductTable`,你会看到表的头(包含了 "Name" 和 "Price" 标签) 不是独立的组件.这是一个个人喜好问题,并且无论哪种方式都有争论.对于这个例子,我把它留做 `ProductTable` 的一部分,因为它是 *data collection*渲染的一部分,而 *data collection*渲染是 `ProductTable` 的职责.然而,当列表头增长到复杂的时候(例如 如果我们添加排序的功能性),那么无疑的使它成为独立的 `ProductTableHeader` 组件是有意义的.
***REMOVED***
既然现在我们已经识别出了我们模型中的组件,让我们把他们安排到一个层级中.这很容易. 在模型中出现在其他组件中的组件 同样应该在层级中表现为一个子级:
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
要构建一个渲染你的数据模型的 app 的静态版本,你会想构建一个重用其他组件并利用 *props* 传递数据的组件. *props* 是一种从父级传递数据到子级的方式.如果你对 *state* 的观念很熟悉, **绝不要用state** 来构建这个静态版本.State 仅仅是为互动预留的,即,随时间变化的数据. 因为这是一个静态版本的app,你不需要它.
***REMOVED***
***REMOVED***
***REMOVED***
在这一步的最后,你会有一个渲染你数据模型的可重用的组件库. 这些组件将只含有 `render()` 方法因为这是一个你的app的静态版本. 在层级顶端的组件 (`FilterableProductTable`) 将会接受你的数据模型作为一个prop.如果你对你的底层数据模型做了变化并且再次调用 `React.render()` ,UI将会更新.很容易看到你的UI是如何更新以及哪里来作出变动,因为这里没有任何复杂的事情发生. React的  **单向数据流** (也被称为 *单向绑定* )保持了每个东西模块化和快速.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
在React里有两种数据 "模型":props和state.明白这二者之间的区别是很重要的;如果你不是很确定不同是什么,请概览[React官方文档](/react/docs/interactivity-and-dynamic-uis-zh-CN.html)
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
要正确的构建你的app,你首先需要思考你的app需要的可变state的最小组. 这里的关键是 DRY: *Don't Repeat Yourself(不要重复自己)*.想出哪些是你的应用需要的绝对最小 state 表达,并按需计算其他任何数据.例如,如果你要构建一个 TODO list,只要保持一个 TODO 项的数组;不要为了计数保持一个单独的 state 变量.作为替代,当你想渲染 TODO 数量时,简单的采用TODO项目数组的长度.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
  * 用户输入的搜索文本
***REMOVED***
***REMOVED***
***REMOVED***
让我们遍历每一个并指出哪一个是state.简单的问三个关于每个数据块的问题:
***REMOVED***
***REMOVED***
***REMOVED***
  3. 你能基于其他任何组件里的 state 或者 props 计算出它吗?如果是,它可能不是state.
***REMOVED***
原始的产品列表被以 props 传入,所以它不是 state. 搜索文本和 checkbox 看起来是state 因为他们随时间变化并且不能从任何东西计算出.最后,产品滤过的列表不是state因为它可以联合原始列表与搜索文本及 checkbox 的值计算出.
***REMOVED***
***REMOVED***
***REMOVED***
  * 用户输入的搜索文本
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
好,我们已经确定了app state 的最小组是什么.接下来,我们需要确定哪个组件变动,或者 *拥有*,这 个state.
***REMOVED***
记住:React都是关于单向数据流下组件层级的.可能不能立刻明白哪些组件应该拥有哪些 state. **这常常对于新手在理解上是最具挑战的一部分,** 所以跟着这几步来弄明白它:
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
  * 找到一个共同拥有者的组件(在层级中所有组件之上需要这个state的单个组件)
  * 要么是共同拥有者,要么是其他在层级里更高级的组件应该拥有这个state
  * 如果你不能找到一个组件,它拥有这个state有意义,创建一个新的组件简单的为了持有此state,并把它在层级里添加比共同拥有者组件更高的层级上.
***REMOVED***
***REMOVED***
***REMOVED***
***REMOVED***
  * 共同拥有者组件是`FilterableProductTable` .
***REMOVED***
***REMOVED***
酷,我们已经决定了我们的state存在于 `FilterableProductTable` .首先,添加一个 `getInitialState()` 方法到  `FilterableProductTable` ,返回 `{filterText: '', inStockOnly: false}` 来反映你的应用的初始状态. 然后,传递`filterText` 和 `inStockOnly` 给 `ProductTable` 和`SearchBar` 作为prop.最后,使用这些prop来过滤 `ProductTable` 中的行和设置`SearchBar`的表单项的值.
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
如果你尝试在当前版本的示例中输入或者选中复选框，你会发现 React 忽略了你的输入。这是有意的，因为已经设置了 `input` 的 `value` prop 总是与 `FilterableProductTable` 传递过来的 `state` 一致。
***REMOVED***
让我们思考下我们希望发生什么。我们想确保每当用户改变了表单，我们就更新 state 来反映用户的输入。由于组件应该只更新自己拥有的 state ， `FilterableProductTable` 将会传递一个回调函数给 `SearchBar` ，此函数每当 state 应被改变时就会击发。我们可以使用 input 的 `onChange` 事件来接受它的通知。 `FilterableProductTable` 传递的回调函数将会调用 `setState()` ，然后应用将会被更新。
***REMOVED***
虽然这听起来复杂，但是实际上只是数行代码。并且数据在应用中从始至终如何流动是非常明确的。
***REMOVED***
***REMOVED***
***REMOVED***
希望,这给了你一个怎样思考用React构建组件和应用的概念。虽然可能比你通常要输入更多的代码，记住，读代码的时间远比写代码的时间多，并且阅读这种模块化的,显式的代码是极端容易的。当你开始构建大型组件库时，你会非常感激这种清晰性和模块化，并且随着代码的重用，你的代码行数将会开始缩减. :)。
