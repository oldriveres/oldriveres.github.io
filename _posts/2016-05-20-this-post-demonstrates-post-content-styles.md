---
layout: page
title: "JavaScript从入门到放弃 -（三）"
subtitle: "ES5新增方法及商品查询案例"
date:   2020-05-20 21:21:21 +0530
categories: junk
author: "David Lee"
meta: "Springfield"
---


# 1. ES5新增方法概述
ES5中给我们新增了一些方法，可以很方便的操作数组或者字符串，这些方法主要包括：
    
 - 数组方法
 - 字符串方法
 - 对象方法

# 2. 数组方法
迭代（遍历）方法：`forEach()`、`map()`、`filter()`、`some()`、`every()`；
## 2.1 forEach方法
**语法规范**：

```javascript
array.forEach(function(currentValue,index,arr){})
```
    

 - `currentValue`：数组当前项的值；
 - `index`：数组当前项的索引；
 - `arr`：数组对象本身

**示例：**
```javascript
// 将数组内的值相加
 var arr = [1, 2, 3];
        var sum = 0;
        arr.forEach(function(value, index, array) {
            // console.log('每个数组元素：' + value);
            // console.log('每个数组索引号：' + index);
            // console.log('每个数组本身：' + array);
            sum += value
        })
        console.log(sum);    // 输出 6
```
相比`for`循环更简单。相当于数组遍历的 for循环，没有返回值。
## 2.2 filter 筛选数组方法 
`filter()` 也是会迭代（遍历）目标数组，返回满足条件的新数组

**语法规范**：
```javascript
array.filter(function(currentValue,index,arr){})
```
 - filter()方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素，==主要用于筛选满足条件的数组==；
 - currentValue：数组当前项的值；
 - index“数组当前项的索引；
 - arr：数组对象本身。
> 注意它直接返回一个新数组；对它的操作不会影响原来的数组。

**示例**：

```javascript
// filter 筛选数组
        var arr = [32, 12, 55, 3]
            // 把大于20的元素筛选出来
        var NewArr = arr.filter(function(value, index, array) {
            // 返回条件
            return value >= 20;
        });
        console.log(NewArr);
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721205246909.png)
>返回值 32、55

## 2.3 some方法
**some()方法：**
    用于检测数组中的元素是否满足指定条件。通俗的说，就是查找数组中是否有满足条件的元素。
> 注：
> 1）`some()`的返回值是布尔值，如果找到返回`true`，反之，则返回`false`；
> 2）some()也同样是执行的迭代（循环）；

**语法规范**：
```javascript
array.some(function(currentValue,index,arr){})
```
 - 如果找到第一个满足条件的元素，则终止循环，不再继续查找；
 - currentValue：数组当前项的值；
 - index：数组当前项的索引；
 - arr：数组对象本身。

**示例：**

```javascript
 // some 查找数组中是否存在大于等于10的元素
  var arr = [20, 12, 5];
  var flag = arr.some(function(value) {
       return value >= 10;
  });
        console.log(flag);
```
> 此处`return` 仅需要返回`value`，因此回调函数中的 index，arr 可省略。

返回值：`true` (如下图)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721211527682.png)
**filter( ) 和 some( ) 的区别：**

 - `filter`：查找满足条件的元素，返回的是一个数组，并且是返回所有满足条件的元素
 - `some`：也是查找满足条件的元素是否存在。返回的是一个布尔值，如果找到第一个满足条件的元素，就终止循环。
 
 # 3. 查询商品案例
 本案例需要实现3个功能：
 - 把数据渲染到页面中；
 - 根据价格显示数据；
 - 根据商品名称显示数据。

案例效果图如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721213648710.gif)
## 3.1 HTML结构和CSS样式
~~~html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        table {
            width: 400px;
            border: 1px solid #000;
            border-collapse: collapse;
            margin: 0 auto;
        }       
        td,
        th {
            border: 1px solid #000;
            text-align: center;
        }       
        .search {
            width: 600px;
            margin: 200px auto 20px;
        }       
        button {
            width: 60px;
        }       
        input {
            width: 50px;
        }
    </style>
</head>
<body>
    <div class="search">
        按照价格查询：<input type="text" class="start"> - <input type="text" class="end"> <button class="search-price">搜索</button> 按照商品名称查询：<input type="text" class="product"> <button class="search-pro">查询</button>
    </div>
    <table>
        <thead>
            <tr>
                <th>id</th>
                <th>产品名称</th>
                <th>价格</th>
            </tr>
        </thead>
        <tbody>
        </tbody>
    </table>
</body>
</html>
~~~
## 3.2 准备数据
```javascript
var data=[{
            id:1,
            pname:'小米',
            price:3888
        },{
            id:2,
            pname:'oppo',
            price:888
        },{
            id:3,
            pname:'荣耀',
            price:1288
        },{
            id:4,
            pname:'华为',
            price:1888
        }];
```
## 3.3 获取元素并渲染数据
### 3.3.1 获取tbody
```javascript
var tbody = document.querySelector('tbody');
```
### 3.3.2 利用forEach渲染数据
```javascript
 // 遍历数组
 data.forEach(function(value){
            
 })
```
创建行，并放入3个单元格：

```javascript
data.forEach(function(value) {
            // 创建行，并装入3个单元格
            var tr = document.createElement('tr');
            tr.innerHTML = '<td>1</td><td>2</td><td>3</td>';
            // 将创建的行追加到tbody
            tbody.appendChild(tr);
})
```
运行后，效果如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721223831646.png)
再将 "< td> 1 < /td>"中的数字分别替换为数组中相应的属性：`value.id`、`value.pname`、`value.price`，代码如下：

```javascript
   // 1、获取相应元素
var tbody = document.querySelector('tbody');
   // 2、把数据渲染到页面中
data.forEach(function(value) {
   // 2.1、创建行，并装入3个单元格
     var tr = document.createElement('tr');
     tr.innerHTML = '<td>' + value.id + '</td><td>' + value.pname + '</td><td>' + value.price + '</td>';
   //2.2、将创建的行追加到tbody
     tbody.appendChild(tr);
})
```
这样，就把 `data` 数据渲染到了页面中。效果如图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072122430835.png)
## 3.4 根据价格筛选商品
当点击 **搜索** 按钮后，就可以根据我们的商品价格去筛选数组里面的对象。

### 3.4.1 获取按钮和表单
```javascript
var search_price = document.querySelector('.search-price');
var start= document.querySelector('.start');
var end = document.querySelector('.end');
```
### 3.4.2 查询商品
```javascript
// 3、根据价格查询商品
        // 当点击按钮后，就根据指定商品的价格范围去筛选数组里的对象
        search_price.addEventListener('click', function() { //给搜索按钮绑定点击事件
            var newData = data.filter(function(value){
                return value.price>=start.value &&  value.price<=end.value;
            })
            console.log(newData)；
        })
```
用 `console.log` 输出，效果如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200721231558907.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pnbGliaw==,size_16,color_FFFFFF,t_70)
正确的返回了两个数组，接下来，就把筛选完的数组渲染到页面中。

在这之前，为简化代码，需要将先前原来的渲染程序：
```javascript
data.forEach(function(value) {
            // 2.1、创建行，并装入3个单元格
            var tr = document.createElement('tr');
            tr.innerHTML = '<td>' + value.id + '</td><td>' + value.pname + '</td><td>' + value.price + '</td>';
            // 2.2、将创建的行追加到tbody
            tbody.appendChild(tr);
});
```
~ 封装为函数（setData）：
```javascript
function setData(myData){
            myData.forEach(function(value) {
            // 2.1、创建行，并装入3个单元格
            var tr = document.createElement('tr');
            tr.innerHTML = '<td>' + value.id + '</td><td>' + value.pname + '</td><td>' + value.price + '</td>';
            // 2.2、将创建的行追加到tbody
            tbody.appendChild(tr);
        });
}
```
> 注意，原程序封装成函数后，第一次的渲染就失效，这时需要在最上面先调用

```javascript
var search_price = document.querySelector('.search-price');
var start= document.querySelector('.start');
var end = document.querySelector('.end');
setData(data);  // 先调用
```
再在搜索按钮的绑定的单击事件里，调用渲染函数
```javascript
// 3、根据价格查询商品
        // 当点击按钮后，就可以根据商品的价格去筛选数组里的对象
        search_price.addEventListener('click', function() { //给搜索按钮绑定点击事件
            var newData = data.filter(function(value) {
                return value.price >= start.value && value.price <= end.value;
            });
            // 把筛选完的数组渲染到页面中（此处直接调用自定义函数）
            setData(newData);
 })
```
运行程序后，即可发现，筛选渲染得到的结果，包含了原来的所有数据。因此，需要在自定义函数内最上面添加清除：`tbody.innerHTML="";`因此，完整的自定义函数如下：
```javascript
function setData(myData) {
            // 先清空原来的tbody里面的数据
            tbody.innerHTML = "";
            myData.forEach(function(value) {
                // 2.1、创建行，并装入3个单元格
                var tr = document.createElement('tr');
                tr.innerHTML = '<td>' + value.id + '</td><td>' + value.pname + '</td><td>' + value.price + '</td>';
                // 2.2、将创建的行追加到tbody
                tbody.appendChild(tr);
            });
}
```
至此，完成 **搜索** 按钮的筛选功能
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200722225046927.gif)
## 3.5 根据名称查询商品
根据商品名称查找商品

如果查询数组中唯一的元素，用some方法列合适，因为它找到这个元素，就不再进行循环，效率更高。

同样的，第一步获取元素：
```javascript
var product = document.querySelector('.product');
var search_pro = document.querySelector('.search-pro');
```
### 3.5.1 渲染查询得到的数组

```javascript
// 4、 通过商品名称查找商品
 search_pro.addEventListener('click', function() {
      var arr = [];
      data.some(function(value) {
             if (value.pname === product.value) {
                  arr.push(value);
                  return true // 此处必须写true;
             }
      })
      // 把拿到的数据渲染到页面中
      setData(arr);
})
```
>1) `push()` 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
>2) 提示：要想数组的开头添加一个或多个元素，请使用 `unshift()` 方法。

更多关于push的说明，请参阅 W3school 技术文档：
[JavaScript push() 方法](https://www.w3school.com.cn/jsref/jsref_push.asp)

本节内容 **要点提示**：

 - 如果查询数组中唯一的元素，用`some`更合适，`some`遇到`true`就会终止循环，效率更高；
 - 而`forEach`中`return`不会终止迭代
# 4. tab栏切换（课后练习）
## 4.1 tab栏切换案例效果图
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072321525870.gif)
## 4.2 效果实现
### 4.2.1 HTML结构
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script type="text/javascript" 	src="https://cdn.bootcss.com/jquery/1.12.4/jquery.js"></script>
</head>
<body>
    <div class="tab">
        <ul>
            <li class="couser">前端
                <ul>
                </ul>
            </li>
            <li class="couser">Python
                <ul>
                </ul>
            </li>
            <li class="couser">JavaEE
                <ul>
                </ul>
            </li>
        </ul>
    </div>
</body>
</html>
```
### 4.2.2 CSS样式
```css
<style>
        * {
            margin: 0;
            padding: 0;
            font-weight: 400;
            list-style: none;
        }
        
        .tab {
            width: 400px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            margin: 100px auto;
        }
        
        .tab li {
            width: 120px;
            height: 30px;
            float: left;
            color: #fff;
            background: #139DFF;
            cursor: pointer;
        }
        
        .tab li:hover {
            background: #FF345F;
            font-weight: 700;
            color: #fff;
        }
    </style>
```
### 4.2.3 JavaScript 代码
```javascript
<script>
        var data = ["就业班", "精品微课", "学员福利"];
        $('.couser').mouseenter(function() {
            var that = $(this).first();
            data.forEach(function(value, index) {
                var li = $("<li>" + value + "</li>");
                $(that).append(li).css("display", "block")
            })
        });
        $('.couser').mouseleave(function() {
            var $li = $(this).first().children();
            $li.remove().css("display", "block");
        });
</script>
```


本帖原文地址：[https://blog.csdn.net/zglibk/article/details/107497739](https://blog.csdn.net/zglibk/article/details/107497739)
