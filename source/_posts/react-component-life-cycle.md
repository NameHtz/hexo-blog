---
title: React生命周期钩子函数
date: 2020-08-20 23:36:51
tags:
---
[React](https://reactjs.org) 组件生命周期钩子函数

####组件生命周期的三个阶段
1. Mounting（加载阶段）
2. Updating（更新阶段）
3. Unmounting（卸载阶段）

<!-- more -->
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
     return true;
   }
   /**
    * 组件更新后触发
    */
   componentDidUpdate() {}
   /**
    * 组件卸载时触发
    */
   componentWillUnmount() {}

   render() {
    return <h1>Hello, {this.props.name}</h1>;
   }
}
```

1. React16新的生命周期弃用了componentWillMount、componentWillReceiveProps，componentWillUpdate
2. 新增了getDerivedStateFromProps、getSnapshotBeforeUpdate来代替弃用的三个钩子函数 componentWillMount、componentWillReceiveProps，componentWillUpdate 
3. React16并没有删除这三个钩子函数，但是不能和新增的钩子函数 getDerivedStateFromProps、getSnapshotBeforeUpdate 混用，React17将会删除 componentWillMount、componentWillReceiveProps，componentWillUpdate
4. 新增了对错误的处理 componentDidCatch