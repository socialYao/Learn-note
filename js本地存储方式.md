# js本地存储方式

## js 本地存储方式有三种：
* cookie
* sessionStorage
* localStorage
## 三种存储方式的区别
它们的相同点都是用于浏览器端存储数据的。
不同点：

* 1、cookie 在浏览器向服务器发起请求时，会自动放到http请求的头部中发送给服务器（即使不需要），而且是所有的请求都会有。
localStorage和sessionStorage就不会随http请求发送给服务器，只在本地存储数据。

* 2、能存储的数据大小不同。
cookie 因为要发送给服务器，为了不造成数据传输的压力，所以能存储的大小有限，只能存储4k。cookie数据还有path的概念。
localStorage和sessionStorage能存储的数据就大的多，至少能存储5M，不同浏览器有不同的限制。

* 3、存储的数据的有效期不同
cookie数据置过期时间，默认就是永久有效，即便关闭窗口或者浏览器。
localStorage数据始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；
sessionStorage数据在浏览器或者窗口关闭就自动删除了。

* 4、作用域不同
localStorage数据在所有同源窗口中都是共享的。
cookie数据也是在所有同源窗口中都是共享的。
sessionStorage数据不在不同的浏览器窗口中共享，即使是同一个页面。


## 使用方法：
**1、cookie **
cookie是以键值对的形式保存的，即key=value的格式。各个cookie之间一般是以“;”分隔。

* 设置cookie
```js
document.cookie="name=jack;password=123";
document.cookie = "username=Bill Gates; expires=Sun, 31 Dec 2017 12:00:00 UTC; path=/"; //设置时间和路径
```

* 读取cookie
```js
var username=document.cookie.split(";")[0].split("=")[1];
```

**2、localStorage**

* 设置localStorage
```js
localStorage.setItem('username','kitty');
```

* 读取localStorage
```js
localStorage.getItem('username');
```

* 删除localStorage
```js
localStorage.removeItem('username');
```

* 清空localStorage
```js
localStorage.clear();
```

**3、sessionStorage**
同localStorage，将localStorage.setItem();的将localStorage换成同sessionStorage就可以了。