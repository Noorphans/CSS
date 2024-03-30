[toc]



## 响应式开发原理

就是使用`媒体查询`**针对不同宽度的设备进行布局**和样式的设置，从而适配不同设备的目的。

![image-20240328160432767](http://images.newstar.net.cn/sally-imgsimage-20240328160432767.png) 



##  响应式布局容器

* 响应式需要一个`父级做为布局容器`(一般都是container)，来`配合子级`元素来实现变化效果。
* **原理**:就是在**不同屏幕下**，通过`媒体查询改变`这个`布局容器的大小`，`再改变里面子元素的排列方式和大小`，从而实现不同屏幕下，看到不同的页面布局和样式变化。



### 平时我们的响应式尺寸划分

* 超小屏幕（手机，小于 768px）：设置宽度为 100%
* 小屏幕（平板，大于等于 768px）：设置宽度为 750px
* 中等屏幕（桌面显示器，大于等于 992px）：宽度设置为 970px
* 大屏幕（大桌面显示器，大于等于 1200px）：宽度设置为 1170px 

> 布局容器宽度比页面尺寸小一点，是为了两侧有空白 更美观 ，也可以**根据实际情况自己定义划分**







### 响应式导航：需求分析

1. 当我们屏幕大于等于800像素，我们给nav宽度为800px，因为里面子盒子需要浮动，所以nav需要清除浮动。
2. nav里面包含8个小li 盒子，每个盒子的宽度定为 100px， 高度为 30px，浮动一行显示。
3. 当我们屏幕缩放，宽度小于800像素的时候， nav盒子宽度修改为 100% 宽度。
4. nav里面的8个小li，宽度修改为 33.33%，这样一行就只能显示3个小li ，剩余下行显示。



* CSS样式：

```css
<style>
        * {
            margin: 0;
            padding: 0;
        }

        ul {
            list-style: none;
        }

        .container {
            width: 750px;
            margin: 0 auto;
        }

        .container ul li {
            float: left;
            width: 93.75px;
            height: 30px;
            background-color: skyblue;
        }

        /* 不大于767 就是不小于768 */
        @media screen and (max-width: 767px) {
            .container {
                width: 100%;
            }

            .container ul li {
                width: 33.33%;
            }
        }
    </style>
```



* HTML结构：

```html
<body>
    <div class="container">
        <ul>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
        </ul>
    </div>
</body>
```

* 当屏幕小于767px时，子元素按照每份33.3%的比例占



