---
title: Node.js 修改文件后缀
date: 2020-09-08 15:20:15
tags: Node.js
---

把项目修改成ts，第一个痛点，修改文件后缀，突然意识到可以用Node.js写个脚本自动修改，于是就动手了；

<!-- more -->
```typescript
import fs = require('fs');
import  chalk = require('chalk');

export default function rename(path?: string): void {
  if (path === undefined) return;
  let readDir: string[] = fs.readdirSync(path);
  for (let i = 0; i < readDir.length; i++) {
    let isFile: boolean = fs.lstatSync(`${path}/${readDir[i]}`).isFile();
    if (isFile) {
      let data: string = fs.readFileSync(`${path}/${readDir[i]}`, {encoding: "utf-8"});
      let name: string = readDir[i];
      let reg = /js$/;
      if (reg.test(name)) {
        name = name.replace(reg, 'ts');
        let oldPath: string = `${path}/${readDir[i]}`;
        let newPath: string = `${path}/${name}`;
        let err: any = fs.renameSync(oldPath, newPath);
        if (err) {
          console.log(chalk.red(`${oldPath}(修改失败)`))
        } else {
          console.log(chalk.blue(`new path: ${newPath} ->(修改成功)`))
        }
      }
    } else {
      rename(`${path}/${readDir[i]}`)
    }
  }
}

/** 
 * 参数为要修改文件夹的路径
 * 🌰
 */
rename('/Users/namehtz/Documents/github/project/src')
```
到这里革命还未胜利，后续还要手动修改文件内容； /手动狗头