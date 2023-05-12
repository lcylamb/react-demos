# 插值表达式

## 插值表达式的位置

1. 标签子节点
2.

## 插值表达式

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

````js
ReactDOM.createRoot(document.getElementById("root")).render(
        <div>
          {arr.map((item, index) => {
            return <div key={index}>The name is {item.name}</div>;
          })}
        </div>
      );
```js
````
