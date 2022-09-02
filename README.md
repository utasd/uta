<!-- # console-feed

![star](https://img.shields.io/github/stars/samdenty/console-feed)
![fork](https://img.shields.io/github/forks/samdenty/console-feed)
![issues](https://img.shields.io/github/issues/samdenty/console-feed)

[console-feed version:3.2.2](https://github.com/samdenty/console-feed) 是一个基于 react 搭建的组件，主要功能是监听、显示来自当前页面、iframe 或跨服务器传输的控制台日志。

![img](https://user-images.githubusercontent.com/13242392/38513414-1bc32870-3c26-11e8-9a8f-0989d2142b1c.png)

### 推荐理由

可以快速构建 devtools,开发在线调试工具简直是一打神器

### 安装

```cmd
yarn add console-feed
# or
npm install console-feed

```

### 使用

```js
import React, { useState, useEffect } from 'react';
import { Console, Hook, Unhook } from 'console-feed';

const LogsContainer = () => {
	const [logs, setLogs] = useState([]);

	// run once!
	useEffect(() => {
		Hook(window.console, log => setLogs(currLogs => [...currLogs, log]), false);
		return () => Unhook(window.console);
	}, []);

	return <Console logs={logs} variant='dark' />;
};

export { LogsContainer };
```

### API

| 参数           | 说明                                               | 类型     | 是否必填 | 默认值/可选值                                                                                                 |
| -------------- | -------------------------------------------------- | -------- | -------- | ------------------------------------------------------------------------------------------------------------- |
| logs           | 日志对象数组                                       | Array    | true     |                                                                                                               |
| filter         | 过滤日志，仅显示某些方法的消息                     | Array    | false    | --/ 'log'、 'debug'、 'info'、 'warn'、 'error'、 'table'、 'clear'、 'time'、 'timeEnd'、 'count'、 'assert' |
| variant        | 设置组件的主体颜色                                 | string   | false    | --/'light' 、 'dark'                                                                                          |
| styles         | 组件样式                                           | string   | false    |                                                                                                               |
| searchKeywords | 用于筛选日志的字符串值                             | string   | false    |                                                                                                               |
| logFilter      | 如果要使用自定义日志过滤器函数，可以提供自己的实现 | function | false    |                                                                                                               |

#### Logs

| 参数    | 说明           | 类型   | 是否必填 | 默认值/可选值                                                                                                 |
| ------- | -------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------- |
| Methods | 日志方法       | string | true     | --/ 'log'、 'debug'、 'info'、 'warn'、 'error'、 'table'、 'clear'、 'time'、 'timeEnd'、 'count'、 'assert' |
| data    | 需要打印的消息 | any[]  | true     |                                                                                                               |

### 注意

V3.4.0 目前使用有个 bug ,console.log(a,b,c)多个字段报错后报错
issues: https://github.com/samdenty/console-feed/issues/108

### 使用场景

前端监控平台、 开发调试器开发、在线运行

### 其他
 -->
