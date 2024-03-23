[toc]



## 固定定位(fixed) - 重要

- **`固定定位`**是元素`固定于浏览器可视区的位置`。（**认死理型**）   

- 主要使用场景：可以在浏览器页面滚动时元素的**位置不会改变**。

- 语法：

  ```css
   选择器 { 
   	position: fixed; 
   }
  ```



> 固定定位的特点：（务必记住）：
>
> 1. 以`浏览器的可视窗口`为参照点 移动元素。
>    * 跟父元素没有任何关系
>    * 不随滚动条滚动。
> * 固定盒子应该有宽度
>    
> 2. 固定定位**`不在占有原先的位置`**。
>    * 固定定位也是`脱标`的，其实固定定位也可以`看做`是一种`特殊的绝对定位`。（**认死理型**） 
>    * **完全脱标**—— 完全不占位置；
> 3. 只认**浏览器的可视窗口** —— `浏览器可视窗口 + 边偏移属性` 来设置元素的位置；
>    - 跟父元素没有任何关系；单独使用的
>    - 不随滚动条滚动。





## 固定定位小技巧： 固定在版心左侧位置

**小算法：**

1. 让固定定位的盒子 left: 50%.  即走到浏览器可视区（也可以看做版心） 的一半位置。

2. 让固定定位的盒子 margin-left: 版心宽度的一半距离。  多走 版心宽度的一半位置，就可以让固定定位的盒子**贴着版心右侧对齐**了。

![image-20240306202959211](http://images.newstar.net.cn/sally-imgsimage-20240306202959211.png)



![image-20240306203010677](http://images.newstar.net.cn/sally-imgsimage-20240306203010677.png)



```css
<style>
    .w {
      width: 800px;
      height: 1400px;
      background-color: palegoldenrod;
      margin: 0 auto;
    }

    .fixed {
      position: fixed;
      /* 1. 走浏览器可视区宽度的一半50%也就是400 */
      left: 50%;
      width: 50px;
      height: 150px;
      /* 2. 利用margin 走版心盒子宽度的一半距离400+5px间距*/
      margin-left: 405px;
      background-color: skyblue;
    }
  </style>
</head>

<body>
  <div class="fixed"></div>
  <div class="w">版心盒子 800像素</div>
</body>
```







## 固定定位会压住下面标准流所有的内容

* 绝对定位同理

```css
<style>
    .box {
      /* 2. 绝对定位（固定定位） 会压住下面标准流所有的内容。 */
      /* position: absolute; */
      position: fixed;
      width: 200px;
      height: 200px;
      background-color: aqua;
    }
  </style>
</head>

<body>
  <div class="box"></div>
  <p>阁下何不同风起，扶摇直上九万里</p>
</body>
```

![](http://images.newstar.net.cn/sally-imgsimage-20240319175339238.png)







## 粘性定位(sticky) - 了解

- **`粘性定位`**可以被认为是相对定位和固定定位的混合。 Sticky 粘性的 

- `跟页面滚动搭配使用`。 兼容性较差，IE 不支持。

- 语法：

  ```css
   选择器 { 
       position: sticky; 
       top: 10px; 
   }
  ```

  > 粘性定位的特点：
  >
  > 1. 以**浏览器的可视窗口**为参照点移动元素（固定定位特点）
  >
  > 2. 粘性定位`占有原先的位置`（相对定位特点）
  >
  > 3. 必须添加 top 、left、right、bottom **其中一个**才有效

  

  \- 举例说明：

  ```css
  <style>
      body {
        height: 3000px;
      }
  
      .nav {
        /* 粘性定位 */
        position: sticky;
        /* 当元素距离顶部10px的时候  黏住不滚动*/
        top: 10px;
        width: 800px;
        height: 50px;
        background-color: pink;
        margin: 100px auto;
      }
    </style>
  </head>
  
  <body>
    <div class="nav">我是导航栏</div>
  </body>
  ```

  



## 定位总结

| **定位模式**        | **是否脱标**       | **移动位置**         | **是否常用**                 |
| ------------------- | ------------------ | -------------------- | ---------------------------- |
| static 静态定位     | 否                 | 不能使用边偏移       | 很少                         |
| `relative 相对定位` | `否 (占有位置)`    | `相对于自身位置移动` | 基本单独使用 (`常用`)        |
| `absolute绝对定位`  | `是（不占有位置）` | `带有定位的父级`     | 搭配定位父级元素使用(`常用`) |
| `fixed 固定定位`    | `是（不占有位置）` | `浏览器可视区`       | 单独使用，不需要父级(`常用`) |
| sticky 粘性定位     | 否 (占有位置)      | 浏览器可视区         | 当前阶段少                   |



> **切记：** **`相对定位、固定定位、绝对定位 两个大的特点`：** 
>
> 1. 是否占有位置（脱标否） 
> 2. 以谁为基准点移动位置。
> 3. **边偏移**需要和**定位模式**联合使用，**单独使用无效**；
> 4. `top` 和 `bottom` 不要同时使用；`left` 和 `right` 不要同时使用。