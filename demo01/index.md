# React 原始使用方法

```js
const span = React.createElement("span", { id: "test" }, "hello react");
const p = React.createElement("p", null, span);
ReactDOM.createRoot(document.getElementById("example_root")).render(p);
```

# JSX 使用
