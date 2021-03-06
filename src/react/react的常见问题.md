# react的常见问题

### react是什么，他的产生解决的什么问题？

react是一个构建页面的javascript库。
react两个特点 
- 声明式 数据改变能有效的重新渲染视图
- 组件化 开发，复用，维护

### react怎么实现数据变化视图更新的？

直接更改state的值不会触发视图更新，通过 setState，传入部分状态，在状态合成完毕后，component update ReactNoopUpdateQueue 方法

setState 是一个异步的过程，会先将变更的数据放在更新队列中，在下一渲染时统一渲染

setState 第二个参数是回调函数，可以在数据更新后进行后续操作

### JSX 和 React.createElement

jsx在通过babel转换后成为 React.createElement

```
<div className="hello" data="123">
  你好
<span id="12">123</span>
</div>
```
转换后
```
"use strict";

React.createElement("div", {
  className: "hello",
  data: "123"
}, "\u4F60\u597D", React.createElement("span", {
  id: "12"
}, "123"));
```

createElement 的前两个参数很定，type props ， 但是之后的参数如果是多个则都是他的子组件

### Component

> 属性
- props
- context
- refs 节点的实例
- updater ？？？那里实现的？

> 原型

- setState
- 


## reactDOM

问题

- 怎么做到局部更新的？

> api
- render （首次）
- hydrate
- setState


流程

创建更新 -> 进入调度


### FiberRoot 对象

- 应用的起点
- 更新过程信息

> 属性

- expirationTime 更新过期时间 小的优先大的跳过
- 


### Fiber

react16后的核心

每一个ReactElement都创建一个Fiber对象来存放状态，所以函数式组件使用hooks管理状态提供可能
不再局限于Component的this.state

> 属性

- Fiber
- return （父节点）
- child  （第一个子节点）
- sibling （下一个兄弟节点）

高效率遍历一棵树

- tag 组件类型
- key
- type elementType
- stateNode 实例
- ref
- pendingProps 新的props
- memozieState
- 


### Update

记录组件的改变，存放于updateQueue，多个update存在

- tag
- payload
- next 下一个update 单向链表
- 

### expirationTime的算法

- requestCurrentTime


计算结果的值相差25的话默认为相等

101除以25取整
```
101/25 | 0 


(x /25 | 0 + 1 ) *25
```


### ReactFiberReconciler

scheduler 调度

保证高优先级的任务优先执行，例如：动画流畅