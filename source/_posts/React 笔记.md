---
title: React 笔记
date: 2019-10-24
updated: 2019-10-24
categories:
  - web前端
tags:
  - React
---

[TOC]

## [React](https://zh-hans.reactjs.org/docs/getting-started.html)

### React 开发环境搭建

### 创建项目

```bash
npm install -g create-react-app
create-react-app demo01
cd demo01
npm start
dir
```

目录 `serviceWorker.js`  
这个是用于写移动端开发的，PWA 必须用到这个文件，有了这个文件，就相当于有了离线浏览的功能

### 基本格式

#### index.js

```JavaScript
import React from "react" //有状态无状态组件都需要引入，不然无法使用jsx语法
import ReactDom from "react-dom"
import App from "./App"
ReactDom.render(<App />,document.getElementById("root"))
```

#### App.js

```JavaScript
import React,{Component} from "react"
export default class App extends Component {
    constructor(){
        super()
        this.state={}
    }
    render(){
        return <div>Hello World</div>
    }
}
```

禁止直接操作 this.state 中的数据

[使用 PropTypes 进行类型检查](https://zh-hans.reactjs.org/docs/typechecking-with-proptypes.html)

`ref={(input)=>this.input=input}`
this.setState()是异步的

```JavaScript
import PropTypes from 'prop-types';
class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string
};
```

性能优化

```JavaScript
shouldComponentUpdate(nextProps,nextState){
    return nextProps.content !== this.props.content
}
```

## 问题

- 打印 e 展开 target 为 null, 直接打印 e.target 为 DOM 元素

```JavaScript
import React,{Component,Fragment} from 'react'
export default class Service extends Component {
  constructor(props){
    super(props)
    this.state={
      inputValue:'js',
      serviceLists:[],
    }
  }
  render(){
    return (
      <Fragment>
        <div>
          <input type="text" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
          <button>+1</button>
        </div>
        <ul>
          <li>1</li>
          <li>2</li>
          <li>3</li>
        </ul>
      </Fragment>
    )
  }
  inputChange(e){
    console.log(e)
    console.log(e.target)
    this.setState({
      inputValue:e.target.value,
    })
  }
}
```

## [Redux](http://cn.redux.js.org/)

[Redux 免费视频教程（共 24 集） | 技术胖-胜洪宇关注 web 前端技术-前端免费视频第一博客](http://www.jspang.com/posts/2019/06/20/redux.html)

**[Redux 免费视频教程（共 24 集） | 技术胖-胜洪宇关注 web 前端技术-前端免费视频第一博客](http://www.jspang.com/posts/2019/06/20/redux.html)**

## [React Router](http://react-guide.github.io/react-router-cn/)

**[React Router 免费文字视频教程（共 9 集） | 技术胖-胜洪宇关注 web 前端技术-前端免费视频第一博客](http://www.jspang.com/posts/2019/07/31/react-router.html)**

```bash
npm install --save react-router-dom
```

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function Index() {
  return <h2>JSPang.com</h2>;
}

function List() {
  return <h2>List-Page</h2>;
}

function AppRouter() {
  return (
    <Router>
      <ul>
        <li>
          {' '}
          <Link to='/'>首页</Link>{' '}
        </li>
        <li>
          <Link to='/list/'>列表</Link>{' '}
        </li>
      </ul>
      <Route path='/' exact component={Index} />
      <Route path='/list/' component={List} />
    </Router>
  );
}
export default AppRouter;
```

## [HOOK](https://react-1251415695.cos-website.ap-chengdu.myqcloud.com/docs/hooks-overview.html)

React 16.8 的新增特性

### `useState`

返回一对值：当前 state 以及更新 state 的函数  
唯一参数：初始 state  
类似：`this.setState`,但是它不会把新的 state 和旧的 state 进行合并
Hook 是一些可以让你在函数组件里钩入 React state 及生命周期等特性的函数

### `useEffect`

数据获取、设置订阅、手动更改 React 组件中的 DOM 都属于副作用

> 可以把 `useEffect` Hook 看做`componentDidMount`,`componentDidUpdate`,`componentWillUnmount`这三个函数的组合

**useEffect 做了什么** 告诉 React 组件需要在渲染后执行某些操作

**为什么在组件内部调用 useEffect** 可以在 effect 只不过直接访问 state 变量。Hook 使用了 JavaScript 的闭包机制

传递给 `useEffect`的函数在每次渲染中都会有所不同，这正是我们可以在 effect 中获取最新的 state 的值的原因，每次重新渲染，都会生成新的 effect

> 与`componentDidMount`或`componentDidUpdate`不同，使用`useEffect`调度的 effect 不会阻塞浏览器更新屏幕

如果你的 effect 返回一个函数，React 将会在执行清除操作时调用它

**使用 Effect 的提示**

- **使用多个 Effect 实现关注点分离** ，React 将按照 effect 声明的顺序依次调用组件中的每一个 effect

- **为什么每次更新的时候都要运行 Effect** 次默认行为保证了一致性，避免了在 class 组建中因为灭有处理更新逻辑而导致常见的 bug

- **通过跳过 Effect 进行性能优化** 传递数组作为`useEffect`的第二个可选参数

  > **注意**
  >
  > 如果你要使用此优化方式，请确保数组中包含了**所有外部这座用于中会随时间变化并且在 effect 中使用的变量** ，否则你的代码会引用到先前渲染中的旧变量
  >
  > 如果想执行只运行一次的 effect （仅在组件挂载和写在时执行），可以传递一个空数组（`[]`）作为第二个参数。

### HOOK 规则

**Hook 使用规则**

> - 只能在**函数最外层**调用 Hook。不要在循环、条件判断或者子函数中调用。
>
> - 只能在**React 的函数组件**中调用 Hook。不要在其他 JavaScript 函数中调用。（还可以在自定义的 Hook 中调用）

**ESLint 插件** `eslint-plugin-react-hooks`

如果我们想要有条件地执行一个 effect，可以将判断放到 Hook 的内部

### 自定义 Hook

自定义 Hook 是一个函数，其名称以“use”开头，函数内部可以调用其他的 Hook

自定义 Hook 是一种自然遵循 Hook 设计的约定，并不是 React 的特性

自定义 Hook 是一种重用状态逻辑的机制（例如设置为订阅并存储当前值），所以每次使用自定义 Hook 时，其中所有的 state 和副作用都是完全隔离的

编写一个`useReducer`的 Hook ,使用 reducer 的方式来管理组件的内部 state

```jsx
function useReducer(reducer, initialState) {
  const [state, setState] = useState(initialState);

  function dispatch(action) {
    const nextState = reducer(state, action);
    setState(nextState);
  }

  return [state, dispatch];
}
```

在组件中使用它

```jsx
function Todos() {
  const [todos, dispatch] = useReducer(todosReducer, []);

  function handleAddClick(text) {
    dispatch({ type: 'add', text });
  }

  // ...
}
```

### Hook API 索引

#### 基础 Hook

##### useState

```jsx
const [state, setState] = useState(initialState);
```

返回一个 state，以及更新 state 的函数

在初始渲染器件，返回的状态（`state`）与传入的第一个参数（`initialState`）值相同

`setState`函数用于更新 state。它接受一个新的 state 值并将组件的一次重新渲染加入队列

```jsx
setState(newState);
```

在后续的重新渲染中，`useState`返回的第一个值将始终是更新后最新的 state

> **注意**
>
> React 会确保`setState`函数的标识是稳定的，并且不会在组件重新渲染时发生变化。这就是为什么可以安全地从`useEffect`或`useCallback`的依赖队列表中省略`setState`

函数式更新

如果新的 state 需要通过使用先前的 state 计算得出，那么可以将函数传递给`setState`。该函数将接收先前的 state，并返回一个更新后的值

```jsx
function Counter({ initialCount }) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount((prevCount) => prevCount + 1)}>+</button>
      <button onClick={() => setCount((prevCount) => prevCount - 1)}>-</button>
    </>
  );
}
```

> **注意**
>
> 与 class 组件中的`setState`方法不同，`useState`不会自动合并更新对象，你可以使用函数式的`setState`结合展开开运算符来达到合并更新对象的效果
>
> ```jsx
> setState((prevState) => {
>   // 也可以使用 Object.assign
>   return { ...prevState, ...updatedValues };
> });
> ```

惰性初始 state

`initialState`参数只会在组件的初始渲染中起作用，后续渲染时会被忽略

```jsx
const [state, setState] = useState(() => {
  const initialState = someExpensiveComputation(props);
  return initialState;
});
```

跳过 state 更新

调用 State Hook 的更新函数并传入当前的 state 时，React 将跳过子组件的渲染及 effect 的执行。（React 使用 [Object.is](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/is) 比较算法来比较 state）

##### useEffect

```jsx
useEffect(didUpdate);
```

该 Hook 接收一个包含命令式，且可能有副作用代码的函数

在函数组件主体内（这里指在 React 渲染阶段）改变 DOM、添加订阅、设置定时器、记录日志以及执行其他包含副作用的操作都是不被允许的，因为这可能会产生莫名其妙的 bug 并破坏 UI 的一致性

使用`useEffect`完成副作用操作。赋值给`useEffect`的函数会在组件渲染到屏幕之后执行，你可以把 effect 看做从 React 的纯函数式操作通往命令式世界的逃生通道

清除 effect

为防止内存泄露，清除函数会在组件卸载钱执行。另外，如果组件多次渲染（通常如此），则**执行下一个 effect 之前，上一个 effect 就已被清除**

effect 的执行时机

虽然`useEffect`会在浏览器绘制后延迟执行，单会保证在任何新的渲染钱执行。React 将在组件更新前刷新上一轮渲染的 effect

effect 的条件执行

给`useEffect`传递第二个参数

##### useContext

```jsx
const value = useContext(MyContext);
```

接受一个 context 对象（`React.createContext`的返回值）并返回该 context 的当前值。当前的 context 值由上层组件中距离当前组件最近的 `<MyContext.Provider>`的`value`prop 决定

当组件上层最近的 `<MyContext.Provider>`更新时，该 Hook 会触发重新渲染，并使用最新传递给`MyContext`provider 的 context `value`值

调用了`useContext`的组件总会在 context 值变化时重新渲染

> **提示**
>
> 如果你在接触 Hook 前已经对 context API 比较熟悉，那应该可以理解，`useContext(MyContext)`相当于 class 组件中的`static contextType=MyContext`或者`<MyContext.consumer>`
>
> `useContext(MyContext)`只是让你能够读取 context 的值以及订阅 context 的变化。你仍然需要在上层组件树中使用`<MyContext.Provider>`来为下层组件提供 context

#### 额外的 Hook

##### useReducer

```jsx
const [state, dispatch] = useReduer(reducer, initialArg, init);
```

`useState`的替代方案。它接受一个形如`(state,action)=>newState`的 reducer，并返回当前的 state 以及与其配套的`diapatch`

## 文档资料

- [技术胖的 2019 新版 React 全家桶免费视频（84 集） - 掘金](https://juejin.im/post/5d817a15f265da039929a761)
- [掘金最污的 React16.x 图文视频教程(2 万 5 千字长文-慎入) - 掘金](https://juejin.im/post/5d085be0f265da1bac401937)

## 课后拓展

serviceWorker  
PWA

如何将项目发布到服务器
