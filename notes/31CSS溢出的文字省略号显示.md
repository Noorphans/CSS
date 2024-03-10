[toc]



# CSS高级技巧



## 单行文本溢出显示省略号

**单行文本溢出显示省略号--`必须满足三个条件`：**

```css
/*1. 先强制一行内显示文本*/
 white-space: nowrap; （ normal 默认自动换行）
 /*2. 超出的部分隐藏*/
 overflow: hidden;
 /*3. 文字用省略号替代超出的部分*/
 text-overflow: ellipsis;
```



\- 举例说明：

```css
<style>
    div {
      width: 150px;
      height: 80px;
      background-color: pink;
      margin: 100px auto;
      /* 这个单词的意思是如果文字显示不开自动换行 */
      /* white-space: normal; */

      /* 1.这个单词的意思是如果文字显示不开也必须强制一行内显示 */
      white-space: nowrap;
      /* 2.溢出的部分隐藏起来 */
      overflow: hidden;
      /* 3. 文字溢出的时候用省略号来显示 */
      text-overflow: ellipsis;
    }
  </style>
</head>

<body>
  <div>
    啥也不说，此处省略一万字
  </div>
</body>
```

![image-20240310170357537](http://images.newstar.net.cn/sally-imgsimage-20240310170357537.png) 





## 多行文本溢出显示省略号(了解)

* 多行文本溢出显示省略号，**有较大兼容性问题**，适合于webKit浏览器或移动端（移动端大部分是webkit内核）
* 需要**满足五个条件**：

```css
/*1. 超出的部分隐藏 */
overflow: hidden;

/*2. 文字用省略号替代超出的部分 */
text-overflow: ellipsis;

/* 3. 弹性伸缩盒子模型显示 */
display: -webkit-box;

/* 4. 限制在一个块元素显示的文本的行数 */
-webkit-line-clamp: 2;

/* 5. 设置或检索伸缩盒对象的子元素的排列方式 */
-webkit-box-orient: vertical;
```

**`更推荐让后台人员来做这个效果，因为后台人员可以设置显示多少个字，操作更简单`。**



\- 举例说明：

```css
<style>
    div {
      width: 150px;
      height: 65px;
      background-color: pink;
      margin: 100px auto;
      overflow: hidden;
      text-overflow: ellipsis;
      /* 弹性伸缩盒子模型显示 */
      display: -webkit-box;
      /* 限制在一个块元素显示的文本的行数 */
      -webkit-line-clamp: 3;
      /* 设置或检索伸缩盒对象的子元素的排列方式 */
      -webkit-box-orient: vertical;
    }
  </style>
</head>

<body>
  <div>
    啥也不说，此处省略一万字,啥也不说，此处省略一万字此处省略一万字
  </div>
</body>
```

![image-20240310171341258](http://images.newstar.net.cn/sally-imgsimage-20240310171341258.png) 



