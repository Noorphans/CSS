[toc]



# CSS高级技巧

## 什么是界面样式

所谓的`界面样式`，就是更改一些用户操作样式，以便提高更好的用户体验。

- 更改用户的鼠标样式 
- 表单轮廓
- 防止表单域拖拽



###  鼠标样式 cursor

```css
 li {
 	cursor: pointer; 
 }
```

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

![image-20240309202800270](http://images.newstar.net.cn/sally-imgsimage-20240309202800270.png) 

```css
<style>
    li {
      list-style: none;
    }
  </style>
</head>

<body>
  <ul>
    <li style="cursor: pointer;">我是鼠标小手样式</li>
    <li style="cursor: default;">我是默认的小白鼠标样式</li>
    <li style="cursor: move;">我是鼠标移动样式</li>
    <li style="cursor: text;">我是鼠标文本样式</li>
    <li style="cursor: not-allowed;">我是鼠标禁止样式</li>
  </ul>
</body>
```





### 取消轮廓线outline

* 给表单添加 outline: 0;   或者  outline: none; 样式之后，就可以`去掉默认的蓝色边框`。
* 语法：

```css
 input {
 	outline: none; 
 }
```



* 代码参考：

```css
<style>
    input {
      /* 取消表单轮廓 */
      outline: none;
    }
  </style>
</head>

<body>
  <!-- 1. 取消表单轮廓 -->
  <input type="text">
</body>
```



![image-20240310111102084](http://images.newstar.net.cn/sally-imgsimage-20240310111102084.png) 





### 防止拖拽文本域 resize

* 实际开发中，我们文本域右下角是不可以拖拽的。
* 语法：

```css
 textarea{ 
 	resize: none;
 }
```



* 代码参考：

```css
<style>
    textarea {
      /* 防止拖拽文本域 */
      resize: none;
    }
  </style>
</head>

<body>
   <!-- 2. 防止拖拽文本域，textarea写到一行就不会有空白区域 -->
  <textarea name="" id="" cols="15" rows="5"></textarea>
</body>
```

> **注意:**  < textarea>< /textarea>写到一行就不会有空白区域

![image-20240310111533746](http://images.newstar.net.cn/sally-imgsimage-20240310111533746.png) 





## vertical-align 属性应用

* CSS的`vertical-align`属性使用场景：经常用于设置图片或者表单`(行内块元素）和文字`(行内元素)`垂直对齐。
* 官方解释： 用于设置一个元素的**`垂直对齐方式`**，但是它只针对于`行内元素或者行内块元素`有效。
* 语法：

```css
vertical-align : baseline | top | middle | bottom 
```

![1571522023413](http://images.newstar.net.cn/sally-imgs1571522023413.png)



![image-20240310144307592](http://images.newstar.net.cn/sally-imgsimage-20240310144307592.png)





### 图片、表单和文字对齐

> 图片、表单都属于`行内块元素`，`默认`的 vertical-align 是`基线对齐`。

![image-20240310144720237](http://images.newstar.net.cn/sally-imgsimage-20240310144720237.png) 

此时可以给图片、表单这些行内块元素的vertical-align属性设置为`middle`就可以让文字和图片`垂直居中对齐`了。



\- 举例说明：

```css
<style>
    img {
      /* 默认基线对齐 */
      /* vertical-align: baseline; */

      /* 垂直居中底部对齐 */
      /* vertical-align: bottom; */

      /* 垂直居中顶端对齐 */
      /* vertical-align: top; */

      /* 让图片和文字垂直居中 */
      vertical-align: middle;

    }

    textarea {
      resize: none;
    }
  </style>
</head>

<body>
  <img src="../images/ldh.jpg" alt=""> Sally是刘德华

  <br>
  <textarea name="" id="" cols="30" rows="10"></textarea> 请您留言
</body>
```

![image-20240310151728275](http://images.newstar.net.cn/sally-imgsimage-20240310151728275.png) 





## 解决图片底部默认空白缝隙问题

**bug：**图片底侧会有一个空白缝隙(加边框可以看出留白区域)，原因是行内块元素会和文字的基线对齐。



### 图片添加vertical-align

给`图片添加vertical-align:middle | top| bottom `等。（**提倡使用的**）



### 把图片转换为块级元素

把图片转换为块级元素 `display: block`不会有留白问题,因为没有基线对齐的属性



```css
 <style>
    div {
      border: 2px solid gray;
    }

    img {
      /* 1. 图片添加vertical-align 防止基线对齐 */
      /* vertical-align: middle; */

      /* 2.图片转为块级元素，不会有留白问题*/
      display: block;
    }
  </style>
</head>

<body>
  <div>
    <img src="../images/ldh.jpg" alt="">
  </div>
</body>
```



![image-20240310161441412](http://images.newstar.net.cn/sally-imgsimage-20240310161441412.png) 