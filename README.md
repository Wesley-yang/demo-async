#基于 Async 前端框架实现异步函数同步调用

异步调用或者说回调是 Javascript 开发中常用到的业务实现方式，但有时候我们也希望可以使用同步的方式来保证业务逻辑可以按顺序执行。
Async.js 给我们带来了这个能力。

##这个示例以 async.js 演示了如何将异步调用同步化
* 示例请使用 Apploader 查看。

##开发指南

**调用示例**

```js
async.auto({
    function1: function(callback) {
        setTimeout(function() {
            console.log(11)
            callback(null, {
                'name': 'function1'
            });
        }, 2000);
    },
    function2: ['function1', function(callback, results) {
        setTimeout(function() {
            console.log(12)
            callback(null, {
                'name': 'function2'
            });
        }, 1000);
    }]
}, function(err, results) {
    console.log(results);
});
```