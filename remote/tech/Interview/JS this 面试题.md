<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">var a=10;</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">var foo={</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">a:20,</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">bar:function(){</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">var</span> <span style="font-size: 18px;"></span> <span style="color: rgb(69,131,131);background-color: rgb(255,255,255);font-size: 18px;">a</span><span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">=30;</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">console.log(this.a);</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">}</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">}</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">foo.bar();</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">(foo.bar)();</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">(foo.bar=foo.bar)();</span> <span style="font-size: 18px;"></span> <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;">(foo.bar,foo.bar)();</span>

`测试：`

`foo.bar()`

`//20`

`(foo.bar)()`

`//20`

`(foo.bar=foo.bar)()`

`//10`

`(foo.bar,foo.bar)()`

`分析：`

在 ECMAScript 中，要掌握的最重要的概念之一是关键字 this 的用法，它用在对象的方法中。关键字 this **总是指向调用该方法的对象**。简单说的就是调用了该方法this就是谁。

`var` `a=10;`

`var` `foo={`

`a:20,`

`bar:function(){`

`var` `a=30;`

`return` `this.a;//this指向调用该方法的对象 }`

`}`

`foo.bar() foo调用了bar这个函数,this` `指向的是foo,然后foo里面有个对象a,this.a其实就是foo.a。 输出的结果为20`

`(foo.bar)()`

`foo.bar 是一个匿名函数,调用这个匿名函数使用的是(),this指向这个匿名函数,但是这个匿名函数仅限于foo里面的全局变量使用,此时this.a就是foo里面的全局变量a. 和上面的调用方法是等价 this指向的就是foo这个对象。输出为20`

`(foo.bar=foo.bar)()`

`根据=从右向左进行赋值 把右边的foo.bar赋值到左边的foo.bar 等价于把右边的匿名函数重新赋值给脸foo.bar 此时 foo.bar整体相当于一个全局变量,这个变量是一个函数性质的变量,再用()调用这个函数时 this指向的是全局变量中的a 输出的是10。可以这么理解： var` `b = foo.bar; b() 输出的就是10`

`这个和上面的区别是使用了=号赋值(此时会改变this的指向)操作,上面那个没有进行=号赋值,后面直接进行调用的foo.bar这个匿名函数。`

`(foo.bar,foo.bar)() 理解了逗号运算符 就理解这个调用过程,相当于调用 左边foo.bar的匿名函数 剩下的就是和第二个调用的过程一样了。`

`这是js里面的逗号运算符`

`逗号运算符参考:`

`<a href="`[`http://m.blog.csdn.net/blog/liaozhongping/46770249`](http://m.blog.csdn.net/blog/liaozhongping/46770249)`"` `target="_blank">`[`http://m.blog.csdn.net/blog/liaozhongping/46770249`](http://m.blog.csdn.net/blog/liaozhongping/46770249)

`</a><a href="`[`http://www.zhihu.com/question/27620371`](http://www.zhihu.com/question/27620371)`"` `target="_blank">`[`http://www.zhihu.com/question/27620371`](http://www.zhihu.com/question/27620371)

`</a>`

[http://www.nowcoder.com/discuss/2085](http://www.nowcoder.com/discuss/2085)