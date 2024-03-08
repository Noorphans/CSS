

## 元素的显示与隐藏

场景：类似网站广告，当我们点击关闭就不见了，但是我们重新刷新页面，会重新出现！

**本质：**`让一个元素在页面中隐藏或者显示出来`。

1. display 显示隐藏元素 但是不保留位置
2. visibility 显示隐藏元素 但是保留原来的位置
3. overflow 溢出显示隐藏 但是只是对于溢出的部分处理



### display 显示（重点）

- display 设置或检索对象是否显示 及 如何显示？


>display: none `隐藏`对象
>
>display：block 除了`转换为块级`元素之外，同时`还有显示`元素的意思。

- **特点：**  **`display 隐藏元素后，不再占有原来的位置。`**
- 后面应用及其广泛，`搭配 JS 可以做很多的网页特效`。
- **实际开发场景：**配合后面js做特效，比如下拉菜单，原先没有，鼠标经过，显示下拉菜单， 应用极为广泛

```css
<style>
    .peppa {
      /* 隐藏 */
      display: none;
      /* 显示 */
      /* display: block; */
      width: 200px;
      height: 200px;
      background-color: pink;

    }

    .george {
      width: 200px;
      height: 200px;
      background-color: skyblue;
    }
  </style>
</head>

<body>
  <div class="peppa">佩奇</div>
  <div class="george">乔治</div>
</body>
```

![image-20240307184329005](http://images.newstar.net.cn/sally-imgsimage-20240307184329005.png)



### visibility 可见性 （了解）

- visibility属性用于指定一个元素应可见还是隐藏。


> visibility：visible ; 　元素可视
>
> visibility：hidden; 　  元素隐藏

- 特点：**visibility 隐藏元素后，继续占有原来的位置**。（停职留薪）


```css
<style>
    .peppa,
    .george,
    .pink {
      width: 100px;
      height: 100px;
    }

    .peppa {
      /* 隐藏 */
      visibility: hidden;
      /* 显示 */
      /* visibility: visible; */
      background-color: pink;
    }

    .george {
      background-color: skyblue;
    }

    .pink {
      background-color: plum;
    }
  </style>
</head>

<body>
  <div class="peppa">熊大</div>
  <div class="george">熊二</div>
  <div class="pink">光头强</div>
</body>
```

![image-20240307185306322](http://images.newstar.net.cn/sally-imgsimage-20240307185306322.png)



> **注意：** 
>
> 1. 如果隐藏元素想要原来位置， 就用 visibility：hidden
> 2. 如果隐藏元素不想要原来位置， 就用 display：none  (用处更多 重点）





### overflow 溢出（重点）

- overflow 属性指定了如果内容溢出一个元素的框（超过其指定高度及宽度）时，会发生什么？

| 属性值      | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| **visible** | 不剪切内容也不添加滚动条(`显示`)                             |
| **hidden**  | 不显示超过对象尺寸的内容，`超出的部分隐藏掉`(`隐藏`)         |
| **scroll**  | 不管超出内容否，总是显示滚动条(`显示滚动条`)                 |
| **auto**    | `超出自动显示滚动条`，不超出不显示滚动条(`溢出才显示滚动条`) |

```css
<style>
    .peppa {
      /* 显示 */
      /* overflow: visible; */

      /* 超出的部分被隐藏掉 */
      /* overflow: hidden; */

      /* 显示滚动条  溢出和不溢出都显示滚动条 */
      overflow: scroll;

      /* 溢出才显示滚动条，不溢出不显示滚动条 */
      /* overflow: auto; */
      width: 200px;
      height: 200px;
      margin: 100px auto;
      border: 3px solid pink;
    }
  </style>
</head>

<body>
  <div class="peppa">
    小猪佩奇》，又名《粉红猪小妹》（台湾名为粉红猪），英文名为《Peppa
    Pig》，是由英国人阿斯特利（Astley）、贝克（Baker）
    <!-- 
    《小猪佩奇》，又名《粉红猪小妹》（台湾名为粉红猪），英文名为《Peppa
    Pig》，是由英国人阿斯特利（Astley）、贝克（Baker）、戴维斯（Davis）创作、导演和制作的一部英国学前电视动画片，也是历年来最具潜力的学前儿童品牌。故事围绕小猪佩奇与家人的愉快经历，幽默而有趣，藉此宣扬传统家庭观念与友情，鼓励小朋友们体验生活。 -->
  </div>
</body>
```



![image-20240307192814278](http://images.newstar.net.cn/sally-imgsimage-20240307192814278.png)

> **注：**
>
> 1. 一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局。
> 2. 但是`如果有定位的盒子`， 请`慎用overflow:hidden`  因为`它会隐藏多余的部分`。



截图所示：

1. 限制内容 不超出盒子 用overflow:hidden

 ![image-20240307193144979](http://images.newstar.net.cn/sally-imgsimage-20240307193144979.png)  

2. 有定位的盒子，本身效果就是要超出盒子，慎用用overflow:hidden

![image-20240307193343591](http://images.newstar.net.cn/sally-imgsimage-20240307193343591.png)