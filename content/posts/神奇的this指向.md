---
title: "神奇的this指向"
date: 2023-08-02T14:44:45+08:00
draft: true
---

## This指向总结

在JavaScript中，this的指向并不是固定的，而是取决于函数的调用方式。以下是this在不同情况下的指向：

1. 全局环境：在非严格模式下，this指向全局对象；在严格模式下，this的值为undefined。

2. 函数调用：这也分为非严格模式和严格模式。在非严格模式下，函数中的this指向全局对象；而在严格模式下，函数中的this的值为undefined。

3. 方法调用：当函数作为某个对象的方法被调用时，this指向该对象。

   1. 这里很有意思，也使我真的懂得了什么是调用决定。

      1. ``` js
         const obj = {
           name: 'sun',
           getName: function () {
             return this.name;
           },
         };
         console.log(obj.getName()); // sun
         const getName = obj.getName;
         console.log(getName()); // undefined
         
         ```

4. 构造函数：在构造函数中，this指向新创建的实例对象。

5. 箭头函数：箭头函数没有自身的this，它里面的this实际上是继承自外层代码块的this。

6. 显式绑定：通过call、apply、bind等方法可以显式地设置函数中this的指向。

7. 事件处理函数：在事件处理函数中，this通常指向触发事件的元素。

8. DOM事件监听：addEventListener的回调函数中的this，指向的是绑定事件的元素本身。

需要注意的是，this的指向是在函数调用时决定的，而不是在函数定义时决定的。
