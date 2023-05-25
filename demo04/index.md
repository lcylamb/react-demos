# 组件通讯-props

## props 传递数据

- 写在组件标签属性位置
  `<Test name="zs"></Test>`
- 写在组件标签内容位置(只能通过 props.children 获取)

## props 接收数据

- 类组件
  - 通过组件实例`this.props`获取
- 函数组件
  - 通过函数形参接收

## props 特点

- props 只能自上而下逐级传递数据
- props 传递的数据只读
- props 可以传递任何类型的数据(包括组件、组件实例、虚拟 DOM)
