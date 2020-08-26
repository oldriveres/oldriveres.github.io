---
layout: page
title:  "JavaScript从入门到放弃系列之一"
subtitle: "构造函数和原型"
date:   2020-05-20 21:21:21 +0530
categories: ["general"]
---

                                        （一）构造函数和原型
# 1. 创建对象的三种方式

## 1.1 用字面量创建
```javascript
 var obj = {};
```

## 1.2 用new关键字创建
```javascript
 var obj = new Object();
```

**new执行做的四件事情：**
  - 在内存中创建一个新的空对象；
  - 让 this 指向这个新的对象；
  - 执行构造函数里面的代码，给这个新对象添加属性和方法；
  - 返回这个新对象（构造函数里面不需要 return ）。

## 1.3 借用构造函数创建
```javascript
function Person(name,age){
  this.name = name;
  this.age = age;
}
var obj = new Person('zs',12);
```

# 2. 实例成员和静态成员
构造函数中的**属性**和**方法**统称为**成员**，成员又分为**实例成员**和**静态成员**。

## 2.1 实例成员
**定义**：构造函数内部通过this添加的成员,；
比如1.3 构造函数中的`Person`里面的`name`、`age`。
> 注意：实例成员，只能通过实例化的对象来访问
## 2.2 静态成员
**定义**：直接在构造函数三身上添加的成员。
例如：
```javascript
Person.sex = '男';
```
> 静态成员，只能通过构造函数来访问。


# 3 构造函数原型
构造函数方法虽然好用，但是存在浪费内存的问题。

如果希望所有对象使用同一个函数，需要做些什么呢？
答案是**构造函数原型**`prototype`
构造函数通过原型分配的函数是所有对象所==共享的==，这就意味着不用再单独开辟内存空间。
> **JavaScript** 规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象。这个 `prototype` 就是一个对象，这个对象的所有属性和方法，都会被构造函数所拥有。

因此，我们可以把某些固定的方法，直接定义在prototype对象上，这样所有对象的实例就可以共享这些方法。

举例说明：
  1. 普通构造函数写法：
```javascript
function Person(uname, age) {
     this.uname = uname;
     this.age = age;
     this.sing = function() {
     console.log('会唱歌');
    }
}
var ldh = new Person('刘德华', 18);
var zxy = new Person('张学友', 19);
ldh.sing();//会唱歌
zxy.sing();//会唱歌
```
  2. 构造函数原型的写法：
```javascript
function Person(uname, age) {
    this.uname = uname;
    this.age = age;
}
Person.prototype.sing = function() {
	console.log('会唱歌');
}
var ldh = new Person('刘德华', 18);
var zxy = new Person('张学友', 19);
ldh.sing();//会唱歌
zxy.sing();//会唱歌
```
这样就实现了方法的共享，所有的实例都可以使用这个方法，不再另行开辟内存空间。

**总结：**
一般情况下，简单数据类型的公共属性放到构造函数里，复杂数据类型如公共方法放到原型对象上

# 4 对象原型 __ proto__
对象都有一个属性`__proto__` 指向构造函数的prototype原型对象，之所以对象可以使用构造函数prototype原型对象的属性和方法，就是因为对象有`__proto__`原型存在。
`__proto__`对象原型和原型对象 `prototype` 是等价的；
`__proto__`对象原型的意义就在于为对象的查找机制提供一个方向，或者说一条路线。

> **方法的查找规则：**
> 首先,，看对象身上是否有该方法，如果有就执行这个对象上的方法，如果没有这个方法，因为有__proto__ 的存在，就去构造函数原型对象prototype上去查找方法。

{% comment %}
Might you have an include in your theme? Why not try it here!
{% include my-themes-great-include.html %}
{% endcomment %}

本文为节选，原贴请参见：[https://blog.csdn.net/zglibk/article/details/107417951](https://blog.csdn.net/zglibk/article/details/107417951)
