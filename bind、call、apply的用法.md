# bind、call、apply的用法和区别



**三者都是用来改变函数的this对象的指向的。**

## 三者的相似之处：

1、都是用来改变函数的this对象的指向的。
2、第一个参数都是this要指向的对象。
3、都可以利用后续参数传参。

## 区别

先看一个例子：

```js
var stu1 = {
    name : "小王",
    gender : "男",
    age : 24,
    say : function() {
    	alert(this.name + " , " + this.gender + " ,今年" + this.age); 
    }
}
var stu2 = {
    name : "小红",
    gender : "女",
    age : 18
}
stu1.say();
```
显示的肯定是小王 ， 男 ， 今年24。
那么如何用stu1的say方法来显示stu2的数据呢。
对于call是这样写的：

```js
stu1.say.call(stu2);
```

对于apply是这样写的：

```js
stu1.say.apply(stu2);
```

而对于bind来说需要这样写：

```js
stu1.say.bind(stu2)();
```

**如果直接写stu1.say.bind(stu2);是不会有任何结果的。call和apply都是对函数的直接调用，而bind方法返回的仍然是一个函数，因此后面还需要()来进行调用才可以。**

那么call和apply有什么区别呢？我们把例子稍微改写一下。

```js
var stu1 = {
    name : "小王",
    gender : "男",
    age : 24,
    say : function(school,grade) {
    	alert(this.name + " , " + this.gender + " ,今年" + this.age + " ,在" + school + "上" + grade);                                
    }
}
var stu2 = {
    name : "小红",
    gender : "女",
    age : 18
}
```
可以看到say方法多了两个参数，我们通过call/apply的参数进行传参。
对于call是这样写的：

```js
stu1.say.call(stu2,"实验小学","六年级");       
```

对于apply是这样写的：

```js
stu1.say.apply(stu2,["实验小学","六年级"]);   
```

**call后面的参数与say方法中是一一对应的，而apply的第二个参数是一个数组，数组中的元素是和say方法中一一对应的，这就是两者最大的区别。**

而bind传参也可以像call那样传参：

```js
stu1.say.bind(stu2,"实验小学","六年级")();
```


但是由于bind返回的仍然是一个函数，所以我们还可以在调用的时候再进行传参:

```js
stu1.say.bind(stu2)("实验小学","六年级");
```


