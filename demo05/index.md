# props 校验

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

# props 批量传递

- 将一个对象批量传递

```js
<Fun {...data}></Fun>
```
