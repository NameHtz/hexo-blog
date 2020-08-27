---
title: React.js
date: 2020-08-20 23:36:51
tags:
---
[React](https://reactjs.org)
### React 组件生命周期钩子函数
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