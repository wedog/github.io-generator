---
title: 单例模式
tags: javascript_single_mode
categories: javascript
date: 2018-01-09 7:07:20
---

## javascript 单例模式

闭包实现单例模式，基本代码如下：

```
	var createSingleInstance = function() {
        var instance = null;
        return function(fn) {
            if (!instance) {
                instance = new fn();
            }
            return instance;
        }
    }();

    function createModal(){
        this.name = 1;
    }
    var fnA = createSingleInstance(createModal);
    var fnB = createSingleInstance(createModal);
    console.log(fnA === fnB);
```



## 惰性单例模式

```
	var getSingle = function (fn) {
        var result;
        return function () {
            return result || ( result = fn.apply(this, arguments) );
        }
    };
```