[toc]





# CSS高级技巧



## 字体图标的产生

* 字体图标使用场景：主要用于显示网页中通用、常用的一些小图标。

* 精灵图是有诸多优点的，但是缺点很明显。
  1. 图片文件还是比较大的。
  2. 图片本身放大和缩小会失真。
  3. 一旦图片制作完毕想要更换非常复杂。(比如想换其中一个图标，更换时需要美工先把图更换，前端再到代码里更换)
* **`字体图标 iconfont`**: 这种技术的出现很好的解决了以上问题。它可以为前端工程师提供一种方便高效的图标使用方式，(看见)**`展示的是图标，本质属于字体`**。
  * 放大缩小不失真，因为文字可以随意更换大小和颜色



## 字体图标的优点

* 轻量级：一个图标字体要比一系列的图像要小。一旦`字体加载`了，`图标`就会马上`渲染`出来，`减少了服务器请求`

- 灵活性：`本质其实是文字`，可以很随意的改变颜色、产生阴影、透明效果、旋转等
- 兼容性：几乎支持所有的浏览器，请放心使用

> **注意：** **`字体图标不能替代精灵技术`**，只是对工作中图标部分技术的提升和优化。



## 字体图标总结

1. 如果遇到一些结构和样式比较简单的小图标，就用字体图标。

![image-20240309093354953](http://images.newstar.net.cn/sally-imgsimage-20240309093354953.png) 



2. 如果遇到一些结构和样式复杂一点的小图片，就用精灵图。

![image-20240309093427850](http://images.newstar.net.cn/sally-imgsimage-20240309093427850.png) 





## 字体图标使用步骤

字体图标是一些网页常见的小图标，我们直接网上下载即可。 因此使用可以分为：

1. 字体图标的下载 

2. 字体图标的引入 （引入到我们html页面中）

3. 字体图标的追加 （以后添加新的小图标）



### 字体图标的下载 

**推荐下载网站：**

- **icomoon** **字库**  http://icomoon.io  推荐指数  **★★★★★**

IcoMoon 成立于 2011 年，推出了第一个自定义图标字体生成器，它允许用户选择所需要的图标，使它们成一字型。该字库内容种类繁多，非常全面，唯一的遗憾是国外服务器，打开网速较慢 ——国外网站

- **阿里** **iconfont** **字库**   http://www.iconfont.cn/  推荐指数   **★★★★★** 

这个是阿里巴巴 M2UX 的一个 iconfont 字体图标字库，包含了淘宝图标库和阿里巴巴图标库。可以使用 AI制作图标上传生成。 重点是，免费！ ——国内网站





### 字体图标的引入

`下载完毕之后，注意原先的文件不要删，后面会用。`

1. **把下载包里面的 fonts 文件夹放入页面根目录下**

![image-20240309111957053](http://images.newstar.net.cn/sally-imgsimage-20240309111957053.png) 



*  **字体文件格式**

  不同浏览器所支持的字体格式是不一样的，字体图标之所以兼容，就是因为包含了主流浏览器支持的字体文件。

  * TureType(  **.ttf**  )格式.ttf字体是Windows和Mac的最常见的字体，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome4+、Safari3+、Opera10+、iOS Mobile、Safari4.2+；
  * Web Open Font Format( **.woff** )格式woff字体，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome6+、Safari3.6+、Opera11.1+；
  * Embedded Open Type( **.eot** )格式.eot字体是IE专用字体，支持这种字体的浏览器有IE4+；
  * SVG(  .**svg**  )格式.svg字体是基于SVG字体渲染的一种格式，支持这种字体的浏览器有Chrome4+、Safari3.1+、Opera10.0+、iOS Mobile Safari3.2+；





2. **在 CSS 样式中全局声明字体**： 简单理解把这些字体文件通过css引入到我们页面中。一定注意字体文件路径的问题

```css
 @font-face {
   font-family: 'icomoon';
   src:  url('fonts/icomoon.eot?7kkyc2');
   src:  url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
     url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
     url('fonts/icomoon.woff?7kkyc2') format('woff'),
     url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
   font-weight: normal;
   font-style: normal;
   font-display: block;
 }
```

> 我们要做的就是 复制 icomoon里的style.css 语法@font-face

![image-20240309114256500](http://images.newstar.net.cn/sally-imgsimage-20240309114256500.png)



3. **html 标签内添加小图标。**

* 打开icomoon里的 demo.html 并复制小图标 粘贴到span标签里
* 这时是个小框，需要指定一个字体，给标签声明一个字体

![image-20240309114621189](http://images.newstar.net.cn/sally-imgsimage-20240309114621189.png) 



4. **给标签定义字体**

  ```css
   span {
     font-family: "icomoon";
   }
  ```

> **注意：**务必保证 这个`字体`和上面`@font-face`里面的`字体保持一致 `

![image-20240309115407134](http://images.newstar.net.cn/sally-imgsimage-20240309115407134.png) 



代码参考：

```css
<style>
    /* 字体声明 */
    @font-face {
      font-family: 'icomoon';
      src: url('fonts/icomoon.eot?7kkyc2');
      src: url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
        url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
        url('fonts/icomoon.woff?7kkyc2') format('woff'),
        url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
      font-weight: normal;
      font-style: normal;
      font-display: block;
    }

    /* span使用字体图标 */
    span {
      font-family: 'icomoon';
      font-size: 50px;
      color: brown;
    }
  </style>
</head>

<body>
  <span></span>
  <span></span>
  <span></span>
</body>
```

效果图：

![image-20240309162011719](http://images.newstar.net.cn/sally-imgsimage-20240309162011719.png) 

### 字体图标的追加

* 如果工作中，原来的字体图标不够用了，我们需要添加新的字体图标到原来的字体文件中。
* 把压缩包里面的 `selection.json` 从新上传，然后选中自己想要新的图标，从新下载压缩包，并替换原来的文件即可。
* 首先打开官网 ——>进入[icomoon.app](https://icomoon.app/) ——>点击导航栏的Import Icons ——>导入我们的json文件 ——>继续添加所需要的图标 ——>生成字体并下载解压，替换之前的font

![image-20240309165103033](C:\Users\Sally\AppData\Roaming\Typora\typora-user-images\image-20240309165103033.png) 





### 字体图标加载的原理：

* 类似精灵图原理。将图标作为字体文件加载到网页中，并通过CSS来使用这些字体图标
* 比如，我们浏览器需要一个定位的小图标，这时它会发送请求让服务器返回给我们图标，服务器返回的是这几个字体文件，浏览器拿到这几个文件就会渲染出来。
* 浏览器拿到这几个字体了，选择其他各种各样的图标就可以直接使用，不用再次发送请求

![1571520617270](http://images.newstar.net.cn/sally-imgs%E5%AD%97%E4%BD%93%E5%9B%BE%E6%A0%87%E5%8A%A0%E8%BD%BD%E7%9A%84%E5%8E%9F%E7%90%86.gif) 



## 扒网页字体图标

1. 首先找到对方的图标位置

![image-20240329202104655](http://images.newstar.net.cn/sally-imgsimage-20240329202104655.png) 

2. 在页面中找到[字体图标](https://so.csdn.net/so/search?q=字体图标&spm=1001.2101.3001.7020)元素对应的css文件，点击css文件，再点击在另一窗口打开

![image-20240329202534892](http://images.newstar.net.cn/sally-imgsimage-20240329202534892.png) 

3. 在打开的css文件中找到以` .eot 、.ttf 、.svg 、.woff`文件结尾的文件，并复制到新的地址栏回车 下载下来，放到自己项目新建的fonts文件夹下

![image-20240329202603857](http://images.newstar.net.cn/sally-imgsimage-20240329202603857.png) 

> 注意.svg结尾的文件把路径复制到地址栏后，按回车键不会下载，此时需要手动右键下载（右键存储为）

4. 整个字体图标样式，也就是打开的这个css文件，也一起下载下来,全部复制到自己目录下新建的fonts文件夹下的iconfont.css里，此文件css名称可自行定义

![image-20240329204310631](http://images.newstar.net.cn/sally-imgsimage-20240329204310631.png) 





5. 找到对应位置，并右键单击复制元素

![image-20240330132054852](http://images.newstar.net.cn/sally-imgsimage-20240330132054852.png) 







































