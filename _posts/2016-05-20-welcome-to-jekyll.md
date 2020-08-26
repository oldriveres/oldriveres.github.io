---
layout: page
title:  "JavaScript从入门到放弃 -（四）"
subtitle: "E5 新增方法"
date:   2020-08-20 21:21:21 +0530
categories: ["general"]
---
# 5. trim方法
去除字符串两端的空格
```javascript
var str = '   helloWorld   '
console.log(str.trim()  //输出helloWorld 去除两端空格
var str1 = '   he l l oWorld   '
console.log(str.trim()  //输出he l l oWorld  去除两端空格
```
 - `trim()`  方法会从一个字符串的两端删除空白字符；
 - `trim()` 方法并不影响原字符串本身，它返回的是一个新的字符串。
# 6. 对象方法
## 6.1 Object.keys()
### 6.1.1 作用
`Object.keys()`用于获取对象自身的所有属性名

### 6.1.2 语法
```javascript
Object.keys(obj)
```
 - 效果类似`for...in` ；
 - 返回一个由属性名组成的数组。
```javascript
 var obj = {
     id: 1,
     pname: '小米',
     price: 1999,
     num: 2000
};
var result = Object.keys(obj)
console.log(result)//[id，pname,price,num]
```
## 6.2 Object.defineProperty()
### 6.2.1 作用
定义对象中新属性或修改原有属性
> Object.defineProperty
> define —— 定义 ；    Property —— 属性。
### 6.2.2 语法
```javascript
object.defineProperty(obj,prop,descriptor)
```
里面有3个参数：
 - obj：必需。当前设置的对象；
 - prop：必需。需定义或修改的属性的名字；
 - descriptor：必需。它是一个对象，该对象中有多个属性。

 `object.defineProperty()` 第3个参数`descriptor`说明：以对象形式`{}`书写。
 - `value`：设置属性的值（可以是任意数据类型），默认为undefined；
 - `writable`：值是否可以重写。true | false 默认为false；
             - `true`：允许重写 
             - `false`：不允许重写
 - `enumerable`：目标属性是否允许遍历。true | false。 默认为false（不允许）；
 - `configurable`：目标属性是否可以被删除、或是否可以再次修改特性。true | false 默认为false；

**示例代码：**
```javascript
<script>
        var obj = {
            id: 1,
            pname: "小米",
            price: 1888,
            num: 1000
        };
        // 1、以前的对象添加和修改的方式
        // obj.num = 1000;
        // 2、采用ES5 defineProperty方式
        Object.defineProperty(obj,'num',{
            value:1000
        });
        Object.defineProperty(obj,'id',{
            // 如果值为false，则不允许修改此属性值
            writable:false
        });
</script>
```

本文原帖地址：[https://blog.csdn.net/zglibk/article/details/107549560](https://blog.csdn.net/zglibk/article/details/107549560)
