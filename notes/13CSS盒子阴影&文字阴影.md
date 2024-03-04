## 盒子阴影(重点)

CSS3 中新增了盒子阴影，我们可以使用 `box-shadow` 属性为盒子添加阴影。
语法：

```css
 box-shadow: h-shadow v-shadow blur spread color inset; 
```

![1571541874805](http://images.newstar.net.cn/sally-imgs1571541874805.png)

> **注意：**
>
> 1. 默认的是外阴影(outset), 但是不可以写这个单词,否则造成阴影无效
> 2. `盒子阴影不占用空间，不会影响其他盒子排列`。
> 3. **前两个值代表水平和垂直，必须写**





\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    div {
      width: 200px;
      height: 200px;
      background-color: plum;
      margin: 100px auto;

      /* 俩值是水平和垂直阴影 */
      /* box-shadow: 10px 10px */
    }

    div:hover {
      box-shadow: 10px 10px 10px -4px rgba(0, 0, 0, .3);
    }

    /* 原先盒子没有影子,当我们鼠标经过盒子就添加阴影效果 */
  </style>
</head>

<body>
  <div></div>
</body>
```



![image-20240227162841991](http://images.newstar.net.cn/sally-imgsimage-20240227162841991.png) 









## 文字阴影

在 CSS3 中，我们可以使用 text-shadow 属性将阴影应用于文本。
语法：

```css
 text-shadow: h-shadow v-shadow blur color;
```

![1571541954222](http://images.newstar.net.cn/sally-imgs1571541954222.png)



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    div {
      font-size: 50px;
      color: orangered;
      font-weight: 700;
      text-shadow: 5px 5px 6px rgba(0, 0, 0, .3);

    }
  </style>
</head>

<body>
  <div>
    你是阴影,我是火影
  </div>
</body>
```



![image-20240228151227428](http://images.newstar.net.cn/sally-imgsimage-20240228151227428.png)