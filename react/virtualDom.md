# Virtual DOM
## 提高操作dom的效率
## 操作dom耗费性能，频繁操作造成页面卡顿
## 1.精准找出发生变化的dom对象，只更新发生变化的部分
## 2.eact在第一次创建Dom对象后，会为每个Dom对象创建其对应的virtual dom对象，在dom对象发生更新之前，react会先更新所有的virtual dom对象，然后react会将更新后的virtual dom和更新前的virtual dom进行比较，从而找出发生变化的部分，react会将发生变化的部分更新到真实dom对象中，react仅更新需要更新的部分
## 3.virtual dom对象更新和比较仅发生在内存中，不会在视图中渲染任何内容，所以这一部分的性能损耗成本是微不足道的

# 创建Virtual Dom对象：
## 在React代码执行前，JSX会被react.createElement方法调用，在调用react.createElement方法时会传入元素的类型，元素的属性，以及元素的子元## 素，react.createElement的返回值为构建好的Virtual dom