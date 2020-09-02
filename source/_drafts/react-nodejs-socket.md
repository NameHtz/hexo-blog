---
title: React.js + Node.js + socket.io
tags: 
---
####准备
新建两个项目，一个React.js前端项目, 一个Node.js后端项目
>前端
```shell script
create-react-app my-socket-app
cd my-socket-app
yarn add socket.io-client

#or

npx create-react-app my-app
cd my-app
yarn add socket.io-client
yarn start 
```
>Node.js
```shell script
mkdir node-socket && cd node-socket
yarn add express socket.io nodemon
```
####前端代码
```jsx

```
####Node.js代码
在package.json中添加启动命令
```json
 {
  .....
 "sctipts": {
     "start": "nodemon index.js"
  }
  ......
 }
```
关于更多 [nodemon](https://github.com/remy/nodemon#nodemon)