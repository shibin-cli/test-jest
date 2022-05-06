# test-jest
[jest](https://github.com/facebook/jest) 的使用
## 开始
```bash
npm i jest -D
```

在 `package.json` 文件中添加命令
```json
{
  "scripts": {
      "test": "jest"
  }
}
```

编写下面代码
```js
// src/sum.js
function sum(a, b) {
    return a + b
}

module.exports = sum
```

编写测试脚本
```js
// test/sum.test.js
const sum = require('../src/sum')

test('adds 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3);
});
```
运行 `npm test`
```
 PASS  test/sum.test.js
  √ adds 1 + 2 to equal 3 (2 ms)
```
## 支持 ESM 方式导入文件

* 使用 babel 支持 ESM 方式导入可以
  * 这样在导入文件时可以省略文件后缀
* 使用 node 本身就支持 ESM 的方式支持
  * 文件名后缀不可省略
## 使用 babel
```bash
npm i babel-jest @babel/core @babel/preset-env -D
```
配置 babel
```js
// babel.conifig.js
module.exports = {
    presets: [['@babel/preset-env', { targets: { node: 'current' } }]]
}
```
## 使用 TypeScript

配置babel
```diff
// babel.config.js
module.exports = {
  presets: [
    ['@babel/preset-env', {targets: {node: 'current'}}],
+    '@babel/preset-typescript',
  ],
};
```