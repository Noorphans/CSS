# 圆角边框(重点)



## 圆角边框的原理

* **border-radius**:在 CSS3 中，新增了`圆角边框`样式，这样我们的盒子就可以变圆角了。
* **radius半径(圆的半径)原理**：(椭)圆与边框的交集形成圆角效果

![image-20240227154943703](http://images.newstar.net.cn/sally-imgsimage-20240227154943703.png)





## 圆角边框的使用

* 语法：

```CSS
border-radius:length;
```

> 1. 参数值可以为`数值`或`百分比`的形式
>
> 2. **如果是`正方形`，想要设置为一个圆，把数值修改为`高度或者宽度的一半`**即可(宽高都一样)，或者**直接写为`50%`**
>
> 3. **`如果是个矩形，设置为高度的一半`**
>
> 4. 该属性是一个`简写属性`，可以跟四个值，分别代表`左上角、右上角、右下角、左下角`
>
> 5. 分开写：`border-top-left-radius`、`border-top-right-radius`、`border-bottom-right-radius`和`border-bottom-left-radius`
>
> 6. `兼容性 ie9+ 浏览器支持, 但是不会影响页面布局,可以放心使用`.



\- 举例说明：

 ```html
  <style>
    .yuanxing {
      width: 200px;
      height: 200px;
      background-color: pink;
      /* border-radius: 100px; */
      /* 50% 就是宽度和高度的一半  等价于 100px */
      border-radius: 50%;
    }

    .juxing {
      width: 300px;
      height: 100px;
      background-color: pink;
      /* 圆角矩形设置为高度的一半 */
      border-radius: 50px;
    }

    .radius {
      width: 200px;
      height: 200px;
      /* border-radius: 10px 20px 30px 40px; */
        
      /* 两个值是对角线关系 */ 
      /* border-radius: 10px 40px; */
      border-top-left-radius: 20px;
      background-color: pink;
    }
  </style>
</head>

<body>
  1. 圆形的做法:
  <div class="yuanxing"></div>
  2. 圆角矩形的做法:
  <div class="juxing"></div>
  3. 可以设置不同的圆角:
  <div class="radius"></div>
</body>
 ```



> 圆角矩形可以为4个角分别设置圆度， 但是是`有顺序`的,还是遵循的`顺时针`。

**分析：**

1. border-radius 一个数值，代表四个角都一样
2. border-radius 两个数值，成对角关系，代表左上 右下和右上 左下
3. border-radius 四个数值不同，可以简写，代表四个角 遵循的`顺时针`。左上 右上 右下 左下
4. border-radius 分开写，可以只设置一个角，但还是遵循的`顺时针`。

![image-20240227160731494](http://images.newstar.net.cn/sally-imgsimage-20240227160731494.png)

 









