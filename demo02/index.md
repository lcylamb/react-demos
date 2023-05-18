# 插值表达式

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
