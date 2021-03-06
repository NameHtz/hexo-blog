---
title: React生命周期钩子函数
date: 2020-08-20 23:36:51
tags: React
---

##### 组件生命周期的三个阶段
1. Mounting（挂载）
2. Updating（更新）
3. Unmounting（卸载）

<!-- more -->

##### 挂载 (Mounting)
当组件实例被创建并插入 DOM 中时，其生命周期调用顺序如下：
+ constructor()
+ static getDerivedStateFromProps()
+ render()
+ componentDidMount()

##### 更新 (Updating)
当组件的 props 或 state 发生变化时会触发更新。组件更新的生命周期调用顺序如下：
+ static getDerivedStateFromProps()
+ shouldComponentUpdate()
+ render()
+ getSnapshotBeforeUpdate()
+ componentDidUpdate()

##### 卸载 (Unmounting)
当组件从 DOM 中移除时会调用如下方法：
+ componentWillUnmount()

##### 错误处理
当渲染过程，生命周期，或子组件的构造函数中抛出错误时，会调用如下方法：
+ static getDerivedStateFromError()
+ componentDidCatch()

```jsx
class Welcome extends React.Component {
 constructor(props) {
    super(props);
    this.state = {}
  }
   /**
    * 组件每次被render的时候，包括在组件构建之后（虚拟dom之后，实际dom挂载之前）
    * 每次获取新的props或state之后；
    * 每次接收新的props之后都会返回一个对象作为新的state，返回null则说明不需要更新state；
    */
   static getDerivedStateFromProps(props, state) {
     return state
   }
   /**
    * 获取到javascript错误
    */
   componentDidCatch(error, info) {}
   /**
    * 挂载后
    */
   componentDidMount() {}
   /**
    * 组件props或者state改变时触发，
    * true:更新
    * false:不更新
    */
   shouldComponentUpdate(nextProps, nextState) {
     return true;
   }
   /**
    * 组件更新前触发
    */
   getSnapshotBeforeUpdate(prevProps, prevState) {
     if(prevProps.value != this.props.value){
       return true
     }
     return null;
   }
   /**
    * 组件更新后触发
    */
   componentDidUpdate(prevProps, prevState, snapshot) {
     if(snapshot != null){
        
     }
  }
   /**
    * 组件卸载时触发
    */
   componentWillUnmount() {}

   render() {
    return <h1>Hello, {this.props.name}</h1>;
   }
}
```

1. React16新的生命周期弃用了`componentWillMount`、`componentWillReceiveProps`，`componentWillUpdate`

2. 新增了`getDerivedStateFromProps`、`getSnapshotBeforeUpdate`来代替弃用的三个钩子函数 `componentWillMount`、`componentWillReceiveProps`，`componentWillUpdate` 

3. React16并没有删除这三个钩子函数，但是不能和新增的钩子函数 `getDerivedStateFromProps`、`getSnapshotBeforeUpdate` 混用，React17将会删除 `componentWillMount`、`componentWillReceiveProps`、`componentWillUpdate`

4. 新增了对错误的处理 `componentDidCatch`

[异步渲染之更新](https://zh-hans.reactjs.org/blog/2018/03/27/update-on-async-rendering.html)

[React](https://reactjs.org) 组件生命周期钩子函数
