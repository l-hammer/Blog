---
title: 🖖你还在用for循环大法麽
lang: zh-CN
direction: rtl
date: 2017.10.29 20:29:29
tags:
  - Array
  - Javascript
---

文章主要介绍了数组Array.prototype方法的使用，需要的朋友可以参考下，如果你是大神，请直接无视。在ES5中，一共有[9种Array方法](http://kangax.github.io/compat-table/es5/)

```js
  Array.prototype.indexOf
  Array.prototype.lastIndexOf
  Array.prototype.every
  Array.prototype.some
  Array.prototype.forEach
  Array.prototype.map
  Array.prototype.filter
  Array.prototype.reduce
  Array.prototype.reduceRight
```

在ES6即将普及的时代，我相信这些方法对FE开发者是非常实用的必备技能，接下来我将通过实例帮大家替换for循环大法，更高效的来操作数组。

### 1、indexOf
indexOf()方法返回在该数组中第一个找到的元素位置，如果它不存在则返回-1。

```js
/* for */
var arr = ['apple','orange','pear'],
    found = false;
for(var i= 0, l = arr.length; i< l; i++){
    if(arr[i] === 'orange'){
        found = true;
    }
}
console.log("found:",found);
```

```js
/* indexof */
var arr = ['apple','orange','pear'];  
console.log("found:", arr.indexOf("orange") != -1);
```

### 2、lastindexOf
`lastIndexOf()`方法返回在该数组中最后一个找到的元素位置，和`indexof()`相反。

### 3、every()
`every()`可是检测数组中的每一项是否符合条件

```js
/* for 是否全部大于0 */
var ary = [12,23,24,42,1];
var result = function(){
  for (var i = 0; i < ary.length; i++) {
    if(ary[i] < 0){
       return false;
    }
  }
  return true;
}
console.log(result()) // true
```

```js
/* every */
var ary = [12,23,24,42,1];
var result = ary.every(function(item, index){
  return item > 0
})
console.log(result)
```

### 4、some()
`some()`可以检测数组中是否有某一项符合条件

```js
/* for 是否存在小于0的项 */
var ary = [12,23,-24,42,1];
var result = function(){
  for (var i = 0; i < ary.length; i++) {
    if(ary[i] < 0){
       return true;
    }
  }
  return false;
}
console.log(result())  //有一项小于0，返回true
```

```js
/* some 是否存在小于0的项 */
var ary = [12,23,-24,42,1];
var result = ary.some(function(item, index){
  return item < 0
})
console.log(result)
```

### 5、forEach() 
`forEach`为每个元素执行对应的方法

```js
/* for */
var arr = [1,2,3,4,5,6,7,8];

for(var i= 0, l = arr.length; i< l; i++){
  console.log(arr[i]);
}
```

```js
/* forEach */
var arr = [1,2,3,4,5,6,7,8];

arr.forEach(function(item,index){
  console.log(item);
});
```
> forEach是用来替换for循环的

### 6、map()
`map()`对数组的每个元素进行一定操作（映射）后，会返回一个新的数组， 

```js
/* for */
var oldArr = [{first_name:"Colin",last_name:"Toh"},{first_name:"Addy",last_name:"Osmani"},{first_name:"Yehuda",last_name:"Katz"}];

function getNewArr(){
  var newArr = [];
  for(var i= 0, l = oldArr.length; i< l; i++){
    var item = oldArr[i];
    item.full_name = [item.first_name,item.last_name].join(" ");
    newArr[i] = item;
  }
  return newArr;
}
console.log(getNewArr());
```

```js
/* map */
var oldArr = [{first_name:"Colin",last_name:"Toh"},{first_name:"Addy",last_name:"Osmani"},{first_name:"Yehuda",last_name:"Katz"}];

function getNewArr(){
  return oldArr.map(function(item,index){
    item.full_name = [item.first_name,item.last_name].join(" ");
    return item;
  });

}
console.log(getNewArr());
```
> map()是处理服务器返回数据时是一个非常实用的函数。

#### forEach 与map的区别：

语法：forEach和map都支持2个参数：一个是回调函数（item,index,list）和上下文；
> forEach：用来遍历数组中的每一项；这个方法执行是没有返回值的，对原来数组也没有影响；数组中有几项，那么传递进去的匿名回调函数就需要执行几次；每一次执行匿名函数的时候，还给其传递了三个参数值：数组中的当前项item,当前项的索引index,原始数组list；理论上这个方法是没有返回值的，仅仅是遍历数组中的每一项，不对原来数组进行修改；但是我们可以自己通过数组的索引来修改原来的数组；
forEach方法中的this是ary,匿名回调函数中的this默认是window；

```js
var ary = [12,23,24,42,1];
var res = ary.forEach(function (item,index,input) {
  input[index] = item * 10;
})
console.log(res); /* undefined */
console.log(ary); /* 会对原来的数组产生改变 */
```
> map： 和forEach非常相似，都是用来遍历数组中的每一项值的，用来遍历数组中的每一项；

区别：map的回调函数中支持return返回值；return的是啥，相当于把数组中的这一项变为啥（并不影响原来的数组，只是相当于把原数组克隆一份，把克隆的这一份的数组中的对应项改变了）；
不管是forEach还是map 都支持第二个参数值，第二个参数的意思是把匿名回调函数中的this进行修改。
```js
var ary = [12,23,24,42,1];
var res = ary.map(function (item,index,input) {
  return item * 10;
})
console.log(res); /* [120,230,240,420,10] */;
console.log(ary); /* [12,23,24,42,1] */;
```

### 7、filter
该filter()方法创建一个新的匹配过滤条件的数组。

```js
/* for */
var arr = [
  {"name":"apple", "count": 2},
  {"name":"orange", "count": 5},
  {"name":"pear", "count": 3},
  {"name":"orange", "count": 16},
];
var newArr = [];
for(var i= 0, l = arr.length; i< l; i++){
  if(arr[i].name === "orange" ){
    newArr.push(arr[i]);
  }
}
console.log("Filter results:",newArr);
```

```js
/* filter */
var arr = [
  {"name":"apple", "count": 2},
  {"name":"orange", "count": 5},
  {"name":"pear", "count": 3},
  {"name":"orange", "count": 16},
];
var newArr = arr.filter(function(item){
  return item.name === "orange";
});
console.log("Filter results:",newArr);
```

### 8、reduce()
reduce()可以实现一个累加器的功能，将数组的每个值（从左到右）将其降低到一个值。 说实话刚开始理解这句话有点难度，它太抽象了。 

场景： 统计一个数组中有多少个不重复的单词 

```js
/* for */
var arr = ["apple","orange","apple","orange","pear","orange"];

function getWordCnt(){
  var obj = {};
  for(var i= 0, l = arr.length; i< l; i++){
    var item = arr[i];
    obj[item] = (obj[item] +1 ) || 1;
  }
  return obj;
}
console.log(getWordCnt());
```

让我先解释一下我自己对reduce的理解。reduce(callback, initialValue)会传入两个变量。回调函数(callback)和初始值(initialValue)。假设函数它有个传入参数，prev和next,index和array。prev和next你是必须要了解的。一般来讲prev是从数组中第一个元素开始的，next是第二个元素。但是当你传入初始值(initialValue)后，第一个prev将是initivalValue，next将是数组中的第一个元素。 

```js
/* 二者的区别，在console中运行一下即可知晓 */
var arr = ["apple","orange"];

function noPassValue(){
  return arr.reduce(function(prev,next){
    console.log("prev:",prev);
    console.log("next:",next);
    return prev + " " +next;
  });
}
function passValue(){
  return arr.reduce(function(prev,next){
    console.log("prev:",prev);
    console.log("next:",next);
    prev[next] = 1;
    return prev;
  },{});
}

console.log("No Additional parameter:",noPassValue());
console.log("----------------");
console.log("With {} as an additional parameter:",passValue());
```

### 9、reduceRight()
reduceRight的语法以及回调函数的规则和reduce方法是一样的，区别就是在与reduce是升序，即角标从0开始，而reduceRight是降序，即角标从arr.length-1开始。方法可应用于字符串。

```js
/* 使用此方法反转字符串中的字符 */
var word = "retupmoc";
function AppendToArray(previousValue, currentValue) {
  return previousValue + currentValue;
}
var result = [].reduceRight.call(word, AppendToArray, "the ");
console.log(result); /* the computer */
```

### isArray()
isArray()是Array对象的一个静态函数，用来判断一个对象是不是数组

```js
var ary1 = [];
var res1 = Array.isArray(ary1);  /* Output: true */
console.log(res1)

var ary2 = new Array();
var res2 = Array.isArray(ary2);  /* Output: true */
console.log(res2)

var ary3 = [1, 2, 3];
var res3 = Array.isArray(ary3);  /* Output: true */
console.log(res3)

var ary4 = new Date();
var res4 = Array.isArray(ary4);  /* Output: false */
console.log(res4)
```
### Resources

##### [links](http://blog.csdn.net/i10630226)
