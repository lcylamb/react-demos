# React 原始使用方法

```js
const span = React.createElement("span", { id: "test" }, "hello react");
const p = React.createElement("p", null, span);
ReactDOM.createRoot(document.getElementById("example_root")).render(p);
```

# JSX 使用

- JSX 使得可以在 js 内写标签
- 浏览器无法解析 JSX，需要使用 babel 进行编译，babel 编译成 createElement 的原始语法
- 一段 JSX 必须要有一个父元素
- 在 JSX 要规范书写标签
- JSX 注释`{/**/}`
