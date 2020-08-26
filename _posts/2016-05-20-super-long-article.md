---
layout: page
title:  "JavaScript从入门到放弃系列之二"
subtitle: "继承"
date:   2020-05-20 21:21:21 +0530
categories: misc
---

# 1. Call()
它的作用是：
- `call()`可以调用函数；
- `call()`可以修改函数运行时`this`的指向：使用`call()`的时候，`参数1`是修改后的`this`指向，`参数2`，`参数3...`使用逗号隔开连接。

```javascript
fun.call(thisArg,arg1,arg2,...)
```
 >       1) `thisArg`：当前调用函数`this`的指向对象；
 >       2) arg1,arg2...：传递的其他普通参数。
 >       在ES6之前并没有提供extends继承。我们可以通过构造函数+原型对象模拟实现继承，被称为组合继承。
```javascript
 function fn(x, y) {
     console.log(this);
     console.log(x + y);
}
  var o = {
  	name: 'andy'
  };
  fn.call(o, 1, 2);//调用了函数此时的this指向了对象o,
```
# 2.子构造函数继承父构造函数中的属性
1. 先定义一个父构造函数；
2. 再定义一个子构造函数；
3. 子构造函数继承父构造函数的属性(使用`call`方法)。

```javascript
  // 1. 父构造函数
 function Father(uname, age) {
   // this 指向父构造函数的对象实例
   this.uname = uname;
   this.age = age;
 }
  // 2 .子构造函数 
function Son(uname, age, score) {
  // this 指向子构造函数的对象实例
  3.使用call方式实现子继承父的属性
  Father.call(this, uname, age);
  this.score = score;
}
var son = new Son('刘德华', 18, 100);
console.log(son);
```
# 3. 借用原型对象继承方法
1. 先定义一个父构造函数
2. 再定义一个子构造函数
3. 子构造函数继承父构造函数的属性(使用call方法)

```javascript
// 1. 父构造函数
function Father(uname, age) {
  // this 指向父构造函数的对象实例
  this.uname = uname;
  this.age = age;
}
Father.prototype.money = function() {
  console.log(100000);
 };
 // 2 .子构造函数 
  function Son(uname, age, score) {
      // this 指向子构造函数的对象实例
      Father.call(this, uname, age);
      this.score = score;
  }
// Son.prototype = Father.prototype;  这样直接赋值会有问题,如果修改了子原型对象,父原型对象也会跟着一起变化
  Son.prototype = new Father();
  // 如果利用对象的形式修改了原型对象,别忘了利用constructor 指回原来的构造函数
  Son.prototype.constructor = Son;
  // 这个是子构造函数专门的方法
  Son.prototype.exam = function() {
    console.log('孩子要考试');

  }
  var son = new Son('刘德华', 18, 100);
  console.log(son);
```