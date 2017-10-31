<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 32px;font-family: inherit;">React 常用面试题目与分析</span>

![王下邀月熊](https://pic2.zhimg.com/v2-a627d79d2ed03fe6f83a11743a18d909_xs.jpg)

<span style="color: rgb(128,128,128);background-color: rgb(255,255,255);font-size: 14px;">9 个月前</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">本文有一定概率为水文，怕湿身者勿看。</span>

[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">React 常用面试题目与分析</span>](https://zhuanlan.zhihu.com/p/24856035)<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">翻译自</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">React Interview Questions</span>](http://link.zhihu.com/?target=https%3A//medium.com/%40tylermcginnis/react-interview-questions-c8a319ed02bd)<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">，从属于笔者的</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">Web 前端入门与工程实践</span>](http://link.zhihu.com/?target=https%3A//github.com/wxyyxc1992/Web-Frontend-Introduction-And-Engineering-Practices)<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">，更多前端思考借鉴</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">2016-我的前端之路:工具化与工程化</span>](https://zhuanlan.zhihu.com/p/24575395)  

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">调用 setState 之后发生了什么？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">在代码中调用setState函数之后，React 会将传入的参数对象与组件当前的状态合并，然后触发所谓的调和过程（Reconciliation）。经过调和过程，React 会以相对高效的方式根据新的状态构建 React 元素树并且着手重新渲染整个UI界面。在 React 得到元素树之后，React 会自动计算出新的树与老树的节点差异，然后根据差异对界面进行最小化重渲染。在差异计算算法中，React 能够相对精确地知道哪些位置发生了改变以及应该如何改变，这就保证了按需更新，而不是全部重新渲染。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">React 中 Element 与 Component 的区别是？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">简单而言，React Element 是描述屏幕上所见内容的数据结构，是对于 UI 的对象表述。典型的 React Element 就是利用 JSX 构建的声明式代码片然后被转化为createElement的调用组合。而 React Component 则是可以接收参数输入并且返回某个 React Element 的函数或者类。更多介绍可以参考</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">React Elements vs React Components</span>](http://link.zhihu.com/?target=https%3A//tylermcginnis.com/react-elements-vs-react-components/)<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">在什么情况下你会优先选择使用 Class Component 而不是 Functional Component？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">在组件需要包含内部状态或者使用到生命周期函数的时候使用 Class Component ，否则使用函数式组件。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">React 中 refs 的作用是什么？</span>

> <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">注意，根据</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">React最新文档</span>](http://link.zhihu.com/?target=https%3A//facebook.github.io/react/docs/refs-and-the-dom.html)<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">，下面这种用法已经被弃用了，统一改为回调函数模式</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`this.refs.textInput`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">Refs 是 React 提供给我们的安全访问 DOM 元素或者某个组件实例的句柄。我们可以为元素添加ref属性然后在回调函数中接受该元素在 DOM 树中的句柄，该值会作为回调函数的第一个参数返回：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`class CustomForm extends Component {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`handleSubmit = () => {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`console.log("Input Value: ", this.input.value)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`render () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return (`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<form onSubmit={this.handleSubmit}>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<input`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`type='text'`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`ref={(input) => this.input = input} />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<button type='submit'>Submit</button>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</form>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">上述代码中的input域包含了一个ref属性，该属性声明的回调函数会接收input对应的 DOM 元素，我们将其绑定到this指针以便在其他的类函数中使用。另外值得一提的是，refs 并不是类组件的专属，函数式组件同样能够利用闭包暂存其值：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`function CustomForm ({handleSubmit}) {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`let inputElement`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return (`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<form onSubmit={() => handleSubmit(inputElement.value)}>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<input`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`type='text'`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`ref={(input) => inputElement = input} />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<button type='submit'>Submit</button>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</form>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">React 中 keys 的作用是什么？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">Keys 是 React 用于追踪哪些列表中元素被修改、被添加或者被移除的辅助标识。</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`render () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return (`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<ul>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`{this.state.todoItems.map(({task, uid}) => {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return <li key={uid}>{task}</li>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`})}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</ul>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">在开发过程中，我们需要保证某个元素的 key 在其同级元素中具有唯一性。在 React Diff 算法中 React 会借助元素的 Key 值来判断该元素是新近创建的还是被移动而来的元素，从而减少不必要的元素重渲染。此外，React 还需要借助 Key 值来判断元素与本地状态的关联关系，因此我们绝不可忽视转换函数中 Key 的重要性。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">如果你创建了类似于下面的Twitter元素，那么它相关的类定义是啥样子的？</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<Twitter username='tylermcginnis33'>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`{(user) => user === null`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`? <Loading />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`: <Badge info={user} />}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</Twitter>`</span>  
</pre>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`import React, { Component, PropTypes } from 'react'`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`import fetchUser from 'twitter'`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`// fetchUser take in a username returns a promise`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`// which will resolve with that username's data.`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`class Twitter extends Component {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`// finish this`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">如果你还不熟悉回调渲染模式（Render Callback Pattern），这个代码可能看起来有点怪。这种模式中，组件会接收某个函数作为其子组件，然后在渲染函数中以props.children进行调用：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`import React, { Component, PropTypes } from 'react'`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`import fetchUser from 'twitter'`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`class Twitter extends Component {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`state = {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`user: null,`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`static propTypes = {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`username: PropTypes.string.isRequired,`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`componentDidMount () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`fetchUser(this.props.username)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`.then((user) => this.setState({user}))`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`render () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return this.props.children(this.state.user)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">这种模式的优势在于将父组件与子组件解耦和，父组件可以直接访问子组件的内部状态而不需要再通过Props传递，这样父组件能够更为方便地控制子组件展示的UI界面。譬如产品经理让我们将原本展示的Badge替换为Profile，我们可以轻易地修改下回调函数即可：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<Twitter username='tylermcginnis33'>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`{(user) => user === null`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`? <Loading />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`: <Profile info={user} />}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</Twitter>`</span>  
</pre>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">Controlled Component 与 Uncontrolled Component 之间的区别是什么？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">React 的核心组成之一就是能够维持内部状态的自治组件，不过当我们引入原生的HTML表单元素时（input,select,textarea 等），我们是否应该将所有的数据托管到 React 组件中还是将其仍然保留在 DOM 元素中呢？这个问题的答案就是受控组件与非受控组件的定义分割。受控组件（Controlled Component）代指那些交由 React 控制并且所有的表单数据统一存放的组件。譬如下面这段代码中username变量值并没有存放到DOM元素中，而是存放在组件状态数据中。任何时候我们需要改变username变量值时，我们应当调用setState函数进行修改。</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`class ControlledForm extends Component {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`state = {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`username: ''`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`updateUsername = (e) => {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`this.setState({`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`username: e.target.value,`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`})`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`handleSubmit = () => {}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`render () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return (`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<form onSubmit={this.handleSubmit}>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<input`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`type='text'`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`value={this.state.username}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`onChange={this.updateUsername} />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<button type='submit'>Submit</button>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</form>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">而非受控组件（Uncontrolled Component）则是由DOM存放表单数据，并非存放在 React 组件中。我们可以使用 refs 来操控DOM元素：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`class UnControlledForm extends Component {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`handleSubmit = () => {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`console.log("Input Value: ", this.input.value)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`render () {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return (`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<form onSubmit={this.handleSubmit}>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<input`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`type='text'`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`ref={(input) => this.input = input} />`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<button type='submit'>Submit</button>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</form>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">竟然非受控组件看上去更好实现，我们可以直接从 DOM 中抓取数据，而不需要添加额外的代码。不过实际开发中我们并不提倡使用非受控组件，因为实际情况下我们需要更多的考虑表单验证、选择性的开启或者关闭按钮点击、强制输入格式等功能支持，而此时我们将数据托管到 React 中有助于我们更好地以声明式的方式完成这些功能。引入 React 或者其他 MVVM 框架最初的原因就是为了将我们从繁重的直接操作 DOM 中解放出来。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">在生命周期中的哪一步你应该发起 AJAX 请求？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">我们应当将AJAX 请求放到 componentDidMount 函数中执行，主要原因有下：</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">React 下一代调和算法 Fiber 会通过开始或停止渲染的方式优化应用性能，其会影响到 componentWillMount 的触发次数。对于 componentWillMount 这个生命周期函数的调用次数会变得不确定，React 可能会多次频繁调用 componentWillMount。如果我们将 AJAX 请求放到 componentWillMount 函数中，那么显而易见其会被触发多次，自然也就不是好的选择。</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">如果我们将 AJAX 请求放置在生命周期的其他函数中，我们并不能保证请求仅在组件挂载完毕后才会要求响应。如果我们的数据请求在组件挂载之前就完成，并且调用了setState函数将数据添加到组件状态中，对于未挂载的组件则会报错。而在 componentDidMount 函数中进行 AJAX 请求则能有效避免这个问题。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">shouldComponentUpdate 的作用是啥以及为何它这么重要？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">shouldComponentUpdate 允许我们手动地判断是否要进行组件更新，根据组件的应用场景设置函数的合理返回值能够帮我们避免不必要的更新。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">如何告诉 React 它应该编译生产环境版本？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">通常情况下我们会使用 Webpack 的 DefinePlugin 方法来将 NODE_ENV 变量值设置为 production。编译版本中 React 会忽略 propType 验证以及其他的告警信息，同时还会降低代码库的大小，React 使用了 Uglify 插件来移除生产环境下不必要的注释等信息。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">为什么我们需要使用 React 提供的 Children API 而不是 JavaScript 的 map？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">props.children并不一定是数组类型，譬如下面这个元素：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<Parent>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<h1>Welcome.</h1>`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</Parent>`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">如果我们使用props.children.map函数来遍历时会受到异常提示，因为在这种情况下props.children是对象（object）而不是数组（array）。React 当且仅当超过一个子元素的情况下会将props.children设置为数组，就像下面这个代码片：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<Parent>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<h1>Welcome.</h1>`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`<h2>props.children will now be an array</h2>`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`</Parent>`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">这也就是我们优先选择使用React.Children.map函数的原因，其已经将props.children不同类型的情况考虑在内了。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">概述下 React 中的事件处理逻辑</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">为了解决跨浏览器兼容性问题，React 会将浏览器原生事件（Browser Native Event）封装为合成事件（SyntheticEvent）传入设置的事件处理器中。这里的合成事件提供了与原生事件相同的接口，不过它们屏蔽了底层浏览器的细节差异，保证了行为的一致性。另外有意思的是，React 并没有直接将事件附着到子元素上，而是以单一事件监听器的方式将所有的事件发送到顶层进行处理。这样 React 在更新 DOM 的时候就不需要考虑如何去处理附着在 DOM 上的事件监听器，最终达到优化性能的目的。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">createElement 与 cloneElement 的区别是什么？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">createElement 函数是 JSX 编译之后使用的创建 React Element 的函数，而 cloneElement 则是用于复制某个元素并传入新的 Props。</span>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">传入 setState 函数的第二个参数的作用是什么？</span>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">该函数会在setState函数调用完成并且组件开始重渲染的时候被调用，我们可以用该函数来监听渲染是否完成：</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`this.setState(`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`{ username: 'tylermcginnis33' },`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`() => console.log('setState has finished and the component has re-rendered.')`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`)`</span>  
</pre>

# <span style="color: rgb(51,51,51);background-color: rgb(255,255,255);font-size: 24px;font-family: inherit;">下述代码有错吗？</span>

<pre><span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`this.setState((prevState, props) => {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`return {`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`streak: prevState.streak + props.count`</span>  
 <span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`}`</span>  
<span style="color: rgb(51,51,51);background-color: rgb(235,238,245);font-size: 14px;">`})`</span>  
</pre>

<span style="color: rgb(51,51,51);background-color: rgb(255,255,255);">这段代码没啥问题，不过只是不太常用罢了，详细可以参考</span>[<span style="color: rgb(34,85,153);background-color: rgb(255,255,255);">React中setState同步更新策略</span>](https://zhuanlan.zhihu.com/p/24781259?refer=wxyyxc1992)