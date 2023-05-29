# 类组件中状态 state

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
