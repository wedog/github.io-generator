---
title: 观察者模式
tags: javascript_observer_mode
categories: javascript
date: 2018-01-09 7:07:20
---

## javascript 观察者模式（发布者与订阅者）

观察者模式又叫发布订阅模式，基本代码如下：

```
	var observer = (function () {
        var subscribers = {};
        return {
            listen: function (key, fn) {
                subscribers[key] = subscribers[key] || [];
                subscribers[key].push(fn);
            },
            trigger: function () {
                var key = Array.prototype.shift.call(arguments);
                var subscriberList = subscribers[key];
                if (!subscriberList || subscriberList.length < 0) {
                    return;
                }
                for (var i = 0; i < subscriberList.length; i++) {
                    var fn = subscriberList[i];
                    fn.apply(this, arguments);
                }
            },
            remove: function (key, fn) {
                var fns = subscribers[key];
                if (!fns) {
                    return;
                }
                if (!fn) {
                    delete subscribers[key];
                } else {
                    for (var i = 0; i < fns.length; i++) {
                        if (fn === fns[i]) {
                            fns.splice(i, 1);
                        }
                    }
                }
            }
        }
    })();
    var fn = function (msg) {
        console.log("收到消息：" + msg);
    }
    observer.listen('ly', fn);
    observer.trigger('ly', 'hello world');
    observer.remove('ly', fn);
```

主要元素：

1. subscribers，订阅者集合
2. listen, 订阅者与响应方法绑定
3. trigger， 发布者发布内容，订阅者处理方法接收并打印
4. remove,  删除订阅者或订阅者的处理方法