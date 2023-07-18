# v18.2.0

# 1. React 原始使用方法

```js
const span = React.createElement("span", { id: "test" }, "hello react");
const p = React.createElement("p", null, span);
ReactDOM.createRoot(document.getElementById("example_root")).render(p);
```

# 2. JSX 使用

- JSX 使得可以在 js 内写标签
- 浏览器无法解析 JSX，需要使用 babel 进行编译，babel 编译成 createElement 的原始语法
- 一段 JSX 必须要有一个父元素
- 在 JSX 要规范书写标签
- JSX 注释`{/**/}`

# 3. 插值表达式

- 可以在 JSX 中使用插值表达式，实现动态渲染

## 插值表达式的位置

1. 标签子节点
2. 标签属性位置

## 插值表达式注意点

- 插值表达式可以写任何 js 表达式
- 插值表达式不能直接渲染对象
- 插值表达式不应该直接渲染函数和 NaN
- 对于 boolean，null，undefined 这些特殊值无法渲染
- 对于数组，会遍历数组将每一个元素当作子节点进行渲染

```js
function fn() {
  console.log(111);
}
ReactDOM.createRoot(document.getElementById("root")).render(
  <div>
    <div>{123}</div>
    <div>{"123"}</div>
    <div>{true}</div>
    <div>{null}</div>
    <div>{undefined}</div>
    <div>{NaN}</div>
    {/*  <div>{{ a: 1 }}</div>*/}
    <div>{function (params) {}}</div>
    <div>{fn()}</div>
    <div>{[1, 2, 3]}</div>
  </div>
);
```

## 列表渲染

- 列表渲染通常使用渲染数组特性，并且在数组渲染出来的元素内部加上 key 属性

### key

- react 用 key 来识别哪些 dom 应该保留、更改
- key 的值应具有**稳定性**
  - 列表渲染时应使用 id 而不是下标，下标可能会导致渲染错误
- key 的值在该列表范围内必须**唯一**
- key 的值不可读，在 props 中无法获取 key 属性的值

````js
ReactDOM.createRoot(document.getElementById("root")).render(
        <div>
          {arr.map((item) => {
            return <div key={item.id}>The name is {item.name}</div>;
          })}
        </div>
      );
```js
````

# 4. JSX with Array

- 在数组中使用 JSX

# 5. 组件通讯-props

## props 传递数据

- 写在组件标签属性位置
  `<Test name="zs"></Test>`
- 写在组件标签子节点位置(只能通过 props.children 获取)

## props 接收数据

- 类组件
  - 通过组件实例`this.props`获取
  - 在类组件 constructor 中，不能直接通过`this.props`获取数据，需要将传递给 constructor 形参，并调用 super 时传递
  ```js
  constructor(props){
    super(props)
    console.log(this.props)
  }
  ```
- 函数组件
  - 通过函数形参接收

## props 特点

- props 只能自上而下逐级传递数据
- props 传递的数据只读
- props 可以传递任何类型的数据(包括组件、组件实例、虚拟 DOM)

# 6. props 校验

对传入组件的 props 数据进行校验

- 引入`import PropTypes from 'prop-types'`
- 函数组件

```js
Foo.propTypes = {
  [属性]: PropTypes.数据类型.isRequired,
};
```

- 类组件

```js
static propTypes = {
    [属性]: PropTypes.数据类型.isRequired,
};
```

## props 批量传递

- 将一个对象批量传递

```js
<Fun {...data}></Fun>
```

# 7. refs 技术

React 提供 refs 技术可以拿到真实 DOM

## 类组件中使用 refs

1.  创建 ref 对象
    `const ref = React.createRef()`
2.  绑定 ref

- 将需要操作的 DOM 绑定 ref,默认函数组件不能使用 ref 属性，
  `<input type="text" ref={ref} />`
  - 通过 ref 对象的 current 属性可以获取真实 DOM
    `ref.current`
- ref 中写回调函数,当真实 DOM 创建好之后，ref 中的回调函数触发，可以通过实例获取真实 DOM
  `<input type="text" ref={(node)=>{this.inpRef = node}} />`

# 8. 类组件中状态 state

- state 是 React 内置的对象
- state 是组件的私有数据，不能共享

## 定义状态

```js
class Test extends React.Component {
  state = {
    name: "zs",
  };
}
```

## 使用状态`this.state`

```js
class Test extends React.Component {
  state = {
    name: "zs",
  };
  render() {
    return <div>{this.state}</div>;
  }
}
```

## 修改状态`this.setState`

```js
class Test extends React.Component {
  state = {
    name: "zs",
  };
  render() {
    return (
      <div>
        <p>{this.state.name}</p>
        <button
          onClick={() => {
            this.setState({ name: "ww" });
          }}
        >
          modify state
        </button>
      </div>
    );
  }
}
```

## 关于 setState

- setState 会让组件更新
- setState 修改数据通常是异步，在原生事件的回调函数中执行 则是同步的
- 重复调用 setState 情况
  - 第一个参数为对象时，重复调用 this.setState 会叠加
  - 如果第一个参数是对象，第二个参数是回调函数
    - 回调函数要等数据修改完毕，并且页面更新完毕才会触发
      如果第一个参数为回调函数则会覆盖
