# Macro and micro tasks

## 微任务

> 随着浏览器的应用领域越来越广泛，消息队列中这种粗时间颗粒度的任务已经不能胜任部分领域的需求。
> 微任务可以在实时性和效率之间做一个有效的权衡。

1. 把异步回调函数封装成一个宏任务，添加到消息队列尾部，当循环系统执行到该任务的时候执行回调函数
2. 执行时机是在主函数执行结束之后、当前宏任务结束之前执行回调函数，这通常都是以微任务形式体现的

### 微任务的延伸

> 基于微任务的技术有 MutationObserver、Promise 以及以 Promise 为基础开发出来的很多其他的技术

## 宏任务

> 我们把这些消息队列中的任务称为宏任务。

1. 渲染事件（如解析 DOM、计算布局、绘制）；
2. 用户交互事件（如鼠标点击、滚动页面、放大缩小等）；
3. JavaScript 脚本执行事件；
4. 网络请求完成、文件读写完成事件。

## MutationObserver

> 采用了“异步 + 微任务”的策略。
> 通过异步操作解决了同步操作的性能问题；通过微任务解决了实时性的问题。
