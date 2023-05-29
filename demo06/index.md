# refs 技术

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
