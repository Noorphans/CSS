[toc]





## 黑马面面布局开发

### 一、目的

1. 了解移动端页面开发流程
2. 掌握移动端常见布局思路





#### 技术方案

> 1. 弹性盒子 + rem + LESS 
> 4. 最小适配设备为iphone5 320px  最大设配设备为iphone8plus(ipad能正常查看内容即可)



#### 代码规范

> 1. 类名语义化,尽量精短、明确，必须以字母开头命名，且全部字母为小写，单词之间统一使用下划线“_” 连接
> 2. `类名嵌套层`次尽量`不超过三层`
> 3. `尽量避免直接使用元素选择器`
> 4. 属性书写顺序
>    布局定位属性：display / position / float / clear / visibility / overflow
>    尺寸属性：width / height / margin / padding / border / background
>    文本属性：color / font / text-decoration / text-align / vertical-align
>    其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow
> 5. `避免使用id选择器`
> 6. `避免使用通配符*和!important`



#### 目录规范

* 项目文件夹：heimamm
  * 样式文件夹：css
  * (产品类)业务类图片文件夹：images
  * （不经常换的装饰图）样式类图片文件夹： icons
  * 字体类文件夹： fonts





### 二、流程开发

#### 蓝湖/摹客协作平台

- UI设计师 psd效果图完成后，会上传到蓝湖//摹客里面，同时会拉前端工程师进入开发
- 大部分情况下，UI会把图片按照前端设计要求给切好
- UI设计师 上传蓝湖到或者/摹客（了解）

> 1. 摹客官网地址： https://www.mockplus.cn/  注册一个账号
> 2. 下载moke里面的ps插件 
> 3. PS 安装/摹客/蓝湖插件
> 3. 打开PS/摹客/蓝湖插件
> 4. 上传（需要切图，需要先标注切图）
> 5. 查看项目
> 6. 邀请成员进入（分享按钮，链接地址）

- 前端设计师可以直接/摹客/蓝湖测量取值

![image-20240326212250973](http://images.newstar.net.cn/sally-imgsimage-20240326212250973.png) 



![image-20240326212303866](http://images.newstar.net.cn/sally-imgsimage-20240326212303866.png) 





#### 适配方案

- flex 布局  
- 百分比布局
- rem布局
- vw/vh布局
- 响应式布局
- 本次案例  **flex + rem + + flexible.js +  LESS**   

#### 初始化文件

- 引入  normalize.css

- less 中 初始化body样式

- 约束范围

~~~css
@media screen and (min-width: 750px) {
    html {
      font-size: 37.5px !important;
    }
  }
~~~

**分析：**

* 物理像素是750px，1px等于两个物理像素，
* iPhone6/7/8 开发像素是375px js把它分为10等份，所以375/10=37.5px
* 当然基准值设为75px也没问题，因为有cssrem转换，比如100px就是2.666667rem，大了除就大，小了除了就小，只是一个比例关系，最后生成结果都一样
* 750/10=75，与37.5px他们比例关系只是两倍的关系，都是十分之一的关系
* 最后，因为**flexible.js默认10等份 改为了20等份**

![image-20240327153154806](http://images.newstar.net.cn/sally-imgsimage-20240327153154806.png) 






#### 布局模块

1. 头部模块  .header    高度为 80px 

2. nav 模块制作  多用 flex

3. 盒子 阴影

   ~~~css
   box-shadow: 0 0px 10px rgba(0, 0, 0, 0.1)
   ~~~

   


#### swiper 插件使用

官网地址：<https://www.swiper.com.cn/>

- 下载需要的css和js文件  html页面中 引入相关文件
- 官网找到类似案例，复制html结构，css样式  js 语法
- 根据需求定制修改模块



#### 图标字体上传下载

上传步骤：

1. 让UI美工准备好 图标字体（必须是svg格式）

2. 点上传按钮（保留颜色并提交）

3. 生成之后加入购物车即可

4. 点击下载 --- 下载代码

小技巧：  如何批量下载全部字体图标呢？

~~~javascript
var span = document.querySelectorAll('.icon-cover');
for (var i = 0, len = span.length; i < len; i++) {
     console.log(span[i].querySelector('span').click());
}
~~~



#### 上传码云并发布部署静态网站

准备工作：  需要下载git软件    需要码云注册账号

git 可以把我们的本地网站提交上传到远程仓库（码云 gitee）里面    类似以前的ftp,码云就是远程仓库， 类似服务器 

1. 码云创建新的仓库。   heimamm  

2. 利用git 提交 把本地网站提交到 码云新建的仓库里面

   - 在网站项目根目录右键-- Git Bash Here

   - 如果是第一次利用git提交，请配置好全局选项

     ~~~javascript
     git config --global user.name "用户名"
     git config --global user.email "你的邮箱地址"
     ~~~

   - 初始化仓库

     ~~~javascript
     git init
     ~~~

   - 把本地文件放到暂存区

     ~~~javascript
     git add .
     ~~~

   - 把本地文件放到本地仓库里面

     ~~~javascript
     git commit -m '提交黑马面面网站'
     ~~~

   - 链接远程仓库

     ~~~javascript
     git remote add origin 你新建的仓库地址
     ~~~

   - 把本地仓库的文件推送到远程仓库 push

     ~~~javascript
     git push -u origin master
     ~~~

3. 码云部署发布静态网站

   - 在当前仓库中，点击  “服务”   菜单 ，选择 Gitee Pages

     ![image-20240327202227773](http://images.newstar.net.cn/sally-imgsimage-20240327202227773.png)  

     

   - 选择 “启动” 按钮

     ![image-20240327202300333](http://images.newstar.net.cn/sally-imgsimage-20240327202300333.png) 

     

   - 稍等之后，会拿到地址，就可以利用这个地址来预览网页了

   ![image-20240327202354429](http://images.newstar.net.cn/sally-imgsimage-20240327202354429.png) 

   - 当然你也可以利用  [草料二维码](https://cli.im/) 生成二维码   
   
     ![image-20240327202659103](http://images.newstar.net.cn/sally-imgsimage-20240327202659103.png) 

最后： 如果提交网站，你不愿意用git 提交， 可以直接找到仓库，里面有文件，选择上传本地文件即可。

![image-20240327203147912](http://images.newstar.net.cn/sally-imgsimage-20240327203147912.png) 

​       ![image-20240327202959136](http://images.newstar.net.cn/sally-imgsimage-20240327202959136.png) 



> 但是，1个小时内，只能上传 20个以内的文件， 前端人员，git必备技能