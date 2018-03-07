---
title: 深拷贝
tags: javascript_clone
categories: javascript
date: 2018-01-08 7:07:20
---

## javascript 数据类型

![](/images/type.png)

1. 原始类型（基本类型）：按值访问，可以操作保存在变量中实际的值。原始类型汇总中null和undefined比较特殊。
2. 引用类型：引用类型的值是保存在内存中的对象。

`与其他语言不同的是，JavaScript不允许直接访问内存中的位置，也就是说不能直接操作对象的内存空间。在操作对象时，实际上是在操作对象的引用而不是实际的对象。所以引用类型的值是按引用访问的。`

## javascript 拷贝

**浅拷贝：**

假如源对象的属性值是一个指向对象的引用，它也只拷贝那个引用值。

1. ECMAScript2015实现方法，` Object.assign(target, ...sources)  `  返回目标对象。（不会跳过那些值为 [`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/null) 或 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined) 的源对象）

2. 循环赋值

   ```
   function simpleClone(initalObj) {    
   	var obj = {};    
   	for ( var i in initalObj) {
   		obj[i] = initalObj[i];
   	}    
   	return obj;
   }
   ```

   ​

**深拷贝**

拷贝基本类型及引用类型

```
function clone(item){
    if(!item){
        return item;
    }
    var types = [String, Number, Boolean];
    var result;
    types.forEach(function(e){
        if(item instanceof e){
            result = e(item);
        }
    })
    if(result === void 0){
        if(Object.prototype.toString.call(item) === '[object Array]'){
            result = [];
            item.forEach(function(e, i){
                result[i] = e;
            })
        }else if(typeof item === 'object'){
            result = {};
            for(var i in item){
               result[i] = clone(item[i]);
            }
        }else{
            result = item;
       }
    }
    return result;
}
var a = {
    b: 1,
    c: [2, 3],
    d: {e: 4}
}
var r = clone(a);
console.log(r);

```

