# vue中好用的插件

## 1、shortid

> 用于为v-for渲染时自动生成唯一的key。（适合用在数组中没有id的时候）
>
> 地址：https://github.com/dylang/shortid

使用方法：

 + 1、初始化

   ```
   npm i shortid --save
   ```

* 2、使用

  ```
  //1.引入
  import shortId from "shortid";
  
  //2.定义一个存放key值的数组
  data(){
  	lists:[], //v-for要渲染的数据列表
  	listsKey:[], //存放key值
  },
  //3. 初始化
  mounted(){
  	this.listsKey = this.list.map(()=>shortId.generate());
  },
  
  //4.使用
  <div v-for="(item,index) in lists" :key="listsKey[index]"></div>
  ```

  