



> 学习目标：了解  PS切图; 掌握  CSS属性书写顺序; 掌握  学成在线案例



## PS 切图

PS 有很多的切图方式：图层切图、切片切图、PS 插件切图等。



### 常见的图片格式

| 序号 | 格式 | 特点和常用的用途                                             |
| ---- | ---- | ------------------------------------------------------------ |
| 1    | jpg  | JPEG（.JPG）对色彩的信息保留较好，高清，颜色较多，我们**产品类的图片** 经常用jpg格式的 |
| 2    | gif  | GIF格式最多只能储存256色，所以通常用来显示简单图形及字体，但是可以保存透明背景和动画效果, 实际 **经常用于一些图片小动画效果** |
| 3    | png  | png图像格式，是一种新兴的网络图形格式，结合了GIF和JPEG的优点，具有存储形式丰富的特点，能够保持透明背景. 如果想要切成 **背景透明的图片** ,请选择png格式. |
| 4    | psd  | PSD图像格式，Photoshop的专用格式，里面可以存放图层、通道、遮罩等多种设计稿. **对我们前端人员来说,最大的优点,我们可以直接从上面复制文字,获得图片,还可以测量大小和距离**. |







### 图层切图

* 简单版步骤：
  1. 使用**移动工具**，点击需要的图片

​     ![1571299959992](http://images.newstar.net.cn/sally-imgs1571300150618.png) 



​	2. 查看右侧，找到图片对应的图层，右击图层 → 快速导出为 PNG

​     ![1571300150618](http://images.newstar.net.cn/sally-imgs1571300150618.png) 



* 但是很多情况下,我们需要合并图层再导出:
  1. 选中需要的若干个图层：选择一个图层，再按住shift键，继续选第二个图层:  
  2. 图层菜单 → 合并图层(ctrl+e)   

​	![1571300529539](http://images.newstar.net.cn/sally-imgs1571300529539.png)

	3. 查看右侧生成的新图层，在合并后的图层上，右击 →  快速导出为 PNG





### 切片切图

步骤：

1. 利用切片选中图片 ：利用切片工具手动划出

![1571301270696](http://images.newstar.net.cn/sally-imgs1571301270696.png)  

2. 导出选中的图片：文件菜单 → 导出→ 存储为web设备所用格式→ 选择我们要的图片格式 →存储。

![1571301357818](http://images.newstar.net.cn/sally-imgs1571301357818.png) 

> 注意：保存的时候，要选“选中的切片”：







### PS插件切图

* `Cutterman `是一款运行在 Photoshop 中的插件，能够自动将你需要的图层进行输出，以替代传统的手工 "导出web所用格式" 以及使用切片工具进行挨个切图的繁琐流程。 

* 它支持各种各样的图片尺寸、格式、形态输出，方便你在pc、ios、Android等端上使用。 它不需要你记住一堆的语法、规则，纯点击操作，方便、快捷，易于上手。

* 官网：http://www.cutterman.cn/zh/cutterman

> **注意：**`Cutterman 插件要求你的 PS 必须是完整版，不能是绿色版，所以大家需要安装完整版本。`



1. 查看 “窗口菜单”里面的“扩展功能”：

​	① 如果是扩展功能的是灰色的，表示就是绿色版的，需要重新安装PS

​	② 如果是扩展功能右侧是可以使用的，表示就是完整版的，可以安装cutterman插件快速切图

![1571302032310](http://images.newstar.net.cn/sally-imgs1571302032310.png)



2. 当cutterman 安装完成后，重启PS，会发现扩展功能里面多了一个cutterman工具：

![1571302286467](http://images.newstar.net.cn/sally-imgs1571302286467.png)



3. 使用步骤

​	① 选择需要的图层

​	② 选择web端，点击web下面的下拉三角

​	③ 选择需要的图片格式

​	④ 设置好存储路径

​	⑤ 点击 “导出选中图层” 按钮

![1571303715362](http://images.newstar.net.cn/sally-imgs1571303715362.png) 

示意图：

![sample1](http://images.newstar.net.cn/sally-imgssample1.gif)





### 像素大厨测量取色

* 官网：https://www.fancynode.com.cn/

* 下载地址：https://www.fancynode.com.cn/pxcook

* 使用的步骤：

  1. 在像素大厨，点击创建项目，选择web项目，选择本地项目。

  2. 把你的图片，拖到像素大厨中，可以拖N张。

  3. 双击某一张图片，就打开这一张图片，打开后，就可以测量了。

  4. 测量的一些快捷键：

     1）alt + 鼠标中键 可以 放大或缩小图片。

     2）空格键 鼠标变成小手 拖拽图片。

     3）可以选择小尺子，量宽度 和 高度 。

     4）选择吸管，就可以量颜色，量出来是16进制。



## CSS属性书写顺序（重点）

**生活中衡量一个人有气质：**

​	穿着打扮  举止言行  等等  

**编程中如何衡量一个人的代码能力**：

​	规范标准  优雅高质量 等等   一个词形容   专业    从代码中看出是否有经验..



建议遵循以下顺序：

1. **布局定位属性**：display / position / float / clear / visibility / overflow（建议 display 第一个写，毕竟关系到模式）
2. **自身属性**：width / height / margin / padding / border / background
3. **文本属性**：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. **其他属性（CSS3）**：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …

**举例：**

```css
 .jdc {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    border-radius: 10px;
 } 
```



